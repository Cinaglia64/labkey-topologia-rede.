# Validação Experimental do EMEN2 para Gestão de Ativos de Rede (CMDB)

Este repositório documenta a avaliação prática e o processo de adaptação da plataforma **EMEN2** como ferramenta de inventário/CMDB no domínio de **Redes de Computadores**, desenvolvida no âmbito de uma Revisão Sistemática da Literatura (RSL).

---

## 1. Acesso e Estrutura Não-Instanciada (Nó Raiz)

Acedeu-se à instância local do EMEN2 a correr no ambiente Docker na porta `8080`. O sistema disponibiliza o nó de registo inicial `Record #0` (Root), a partir do qual toda a estrutura ontológica de ativos é construída hierarquicamente.

| Tela de Login | Nó Raiz Inicial (`/record/0/`) |
| :---: | :---: |
| ![Login Inicial](Login_senha.png) | ![Root Record](root.png) |

---

## 2. Ontologia e Modelação de Parâmetros (`ParamDef`)

Inspecionou-se a ontologia de parâmetros nativos do sistema (`/paramdefs/`) e procedeu-se à criação dos atributos específicos de ativos de rede.

![Ontologia de Parâmetros](Parameter%20ontology.png)

### Cadastro dos Parâmetros de Camada 2 e 3

1. **IP Address (`ip_address`):**
   * Definição como tipo `string` indexado.
   * Confirmação da persistência no Berkeley DB (`/paramdef/ip_address/`).

| Formulário de Criação | Parâmetro Persistido |
| :---: | :---: |
| ![Novo IP](new%20parameter.png) | ![IP Salvo](Parameter_IP%20Address.png) |

2. **MAC Address (`mac_address`):**
   * Definição como tipo `string`.
   * Confirmação da persistência no banco de dados (`/paramdef/mac_address/`).

| Formulário de Criação | Parâmetro Persistido |
| :---: | :---: |
| ![Novo MAC](mac_address.png) | ![MAC Salvo](MAC%20Address.png) |

3. **Bandwidth (`bandwidth_mbps`):**
   * Definição como tipo `float` para medição de largura de banda em Mbps.
   * Confirmação da persistência (`/paramdef/bandwidth_mbps/`).

| Formulário de Criação | Parâmetro Persistido |
| :---: | :---: |
| ![Novo Bandwidth](bandwidth_mbps.png) | ![Bandwidth Salvo](Bandwidth.png) |

---

## 3. Definição e Ajuste do Tipo de Registro (`RecordDef`)

Criação da entidade base **`network_device`** (*Network Device*) derivada do protocolo raiz para agrupar os metadados.

### Limitação de GUI e Injeção de Template

A interface gráfica nativa ocultava a caixa de edição direta do template principal da *view*.

| View Inicial Limita GUI | Template Injetado na View |
| :---: | :---: |
| ![Protocolo Inicial](Protocol_%20Network%20Device.png) | ![Simulação de View](simula%C3%A7%C3%A3o.png) |

Para contornar a limitação e associar os 7 parâmetros (`ip_address`, `mac_address`, `vlan_id`, `bandwidth_mbps`, `firmware_version`, `routing_protocol` e `vendor`), executou-se a injeção via script Python no contêiner:

```bash
docker exec -it emen2-test python -c "
import emen2.db.recorddef

rectype = emen2.db.recorddef.get('network_device')

template = '''# {{desc_short}}
{{desc_long}}

* IP Address: {{ip_address}}
* MAC Address: {{mac_address}}
* VLAN ID: {{vlan_id}}
* Bandwidth (Mbps): {{bandwidth_mbps}}
* Firmware Version: {{firmware_version}}
* Routing Protocol: {{routing_protocol}}
* Vendor: {{vendor}}'''

rectype['views']['main'] = template
emen2.db.recorddef.update(rectype)
print('RecordDef network_device atualizado com sucesso!')
"
---

## 4. Hierarquia de Ativos: Criação do Modelo `SW-CORE-01`

Para simular um ambiente CMDB real de infraestrutura de rede, derivou-se um tipo de registo específico para switches de núcleo de camada 3 (**`SW-CORE-01`**) a partir da definição base `network_device`.

### Parâmetros e Atributos Mapeados:
* **IP Address (`ip_address`):** Endereço IPv4 de gestão do dispositivo.
* **MAC Address (`mac_address`):** Endereço físico da interface principal.
* **VLAN ID (`vlan_id`):** Identificador da VLAN de gerência.
* **Bandwidth (`bandwidth_mbps`):** Capacidade de comutação / largura de banda em Mbps.
* **Firmware Version (`firmware_version`):** Versão do sistema operacional instalado no switch.
* **Routing Protocol (`routing_protocol`):** Protocolo de roteamento ativo (ex.: OSPF, BGP).
* **Vendor (`vendor`):** Fabricante do equipamento de rede.

| Formulário de Definição | Protocolo `SW-CORE-01` Salvo |
| :---: | :---: |
| ![Criando SW-CORE-01](switch.png) | ![SW-CORE-01 Salvo](switch_salvo.png) |

---

## 5. Conclusão da Análise para a RSL

A avaliação prática da plataforma **EMEN2** forneceu dados para compor a análise comparativa de ferramentas no âmbito da RSL:

1. **Capacidade de Adaptação (Extensibilidade):** **Alta.** O motor de dados do EMEN2 baseado em Berkeley DB e Python permite a criação e personalização de ontologias e novos tipos de dados sem necessidade de recompilação do sistema ou alteração do esquema de banco de dados tradicional.
2. **Usabilidade e Interface Web (DX / UX):** **Média/Baixa.** A interface gráfica nativa apresentou limitações para edição direta de templates de exibição (*views*), exigindo *workarounds* via linha de comando/scripts Python para injeção de atributos no backend.
3. **Adequação como CMDB de Redes:** **Viável com ressalvas.** O sistema atende aos requisitos de modelagem hierárquica e rastreabilidade de ativos, porém demanda um esforço considerável de configuração técnica inicial se comparado a soluções CMDB especializadas de mercado.
