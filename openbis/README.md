# Mapeamento e Evidências Visuais do openBIS para Experimentos de Redes (SDN/QoS)

Este diretório reúne as capturas de tela e a documentação dos procedimentos realizados no **openBIS** para a gestão de dados de proveniência em experimentos de **Redes Definidas por Software (SDN)** e **Qualidade de Serviço (QoS)** aplicados ao tráfego VoIP.

---

## 📸 Registro e Fluxo de Trabalho no Sistema

As imagens a seguir detalham todo o fluxo de operação, desde a autenticação no sistema até o registro de objetos, anexos e gestão de falhas na plataforma openBIS local (`localhost:8080`):

### 1. Autenticação e Acesso Inicial

<img width="1915" height="1012" alt="Login" src="https://github.com/user-attachments/assets/804396bc-0caa-4baf-94a0-94dede55980b" />

Tela inicial de autenticação da plataforma openBIS.

<img width="957" height="1007" alt="Login_Senha" src="https://github.com/user-attachments/assets/9d14fcd8-cb29-40e4-8616-201294eb4e7e" />

Preenchimento dos dados de acesso utilizando a conta de administrador (`admin`).

<img width="1917" height="1020" alt="tela inicial" src="https://github.com/user-attachments/assets/6952c8af-484e-48ab-9098-b53a996e0cd0" />

Painel principal de boas-vindas (*Welcome to openBIS*) exibido imediatamente após o acesso efetuado com sucesso.

<img width="1917" height="972" alt="abriu_essa_aba_quando_cliquei_no_link" src="https://github.com/user-attachments/assets/33dd4cb0-55b0-4536-982a-622e1ba8baac" />

Visualização da interface em modo simplificado (`viewMode=SIMPLE`) acionado por permalink, apresentando o histórico de navegação (*Last Visited Places*).

---

### 2. Configuração do Espaço (Space)

<img width="1912" height="970" alt="New_Space" src="https://github.com/user-attachments/assets/140dcf3c-3dca-421b-adb6-ee6dfc114d35" />

Formulário de criação do espaço `SDN_QOS_VOIP`, acompanhado da descrição do escopo da pesquisa em SDN e QoS para tráfego VoIP.

<img width="1917" height="965" alt="New_space_salvo" src="https://github.com/user-attachments/assets/591f2711-4255-4124-a707-c9209c16bf54" />

Navegador de Espaços (*Space Browser*) listando o espaço `SDN_QOS_VOIP` devidamente cadastrado no sistema.

---

### 3. Configuração do Projeto e Coleção

<img width="1917" height="965" alt="Registrar_projeto" src="https://github.com/user-attachments/assets/88f6bbe4-71fc-4c7a-9b1b-d0219b370f88" />

Formulário de registro do projeto (*Project Registration*) para definição do código `PESQUISA_SDN_VOIP`.

<img width="1912" height="917" alt="Registrar_Projeto_Salvar" src="https://github.com/user-attachments/assets/ad3fd688-7ab4-40e0-a9bd-15a15d6ac7ef" />

Associação e vínculo do projeto ao espaço `SDN_QOS_VOIP` criado na etapa anterior.

<img width="1917" height="867" alt="Registrado" src="https://github.com/user-attachments/assets/78945fa7-5759-482a-92d2-4cefd8ca5506" />

Confirmação do registro do projeto `/SDN_QOS_VOIP/PESQUISA_SDN_VOIP` no openBIS.

<img width="1917" height="827" alt="registrar_projeto1" src="https://github.com/user-attachments/assets/3856634f-b174-4bbc-b480-d26c5a316d6f" />

Formulário de cadastro da Coleção de dados do tipo `EXPERIMENTOS` vinculada ao projeto de pesquisa.

<img width="1906" height="950" alt="Registrado_com_sucesso" src="https://github.com/user-attachments/assets/ec7ef523-d341-4ce9-a7cd-0c872276f6e0" />

Mensagem de confirmação após a criação bem-sucedida da coleção `/SDN_QOS_VOIP/PESQUISA_SDN_VOIP/EXPERIMENTOS`.

<img width="1917" height="962" alt="Collection EXPERIMENTS" src="https://github.com/user-attachments/assets/f32e91ba-8594-4f0b-94c5-b326ef7c43e2" />

Painel de visualização e gestão da coleção `EXPERIMENTOS`, apresentando as suas propriedades e metadados de auditoria.

---

### 4. Registro dos Objetos (Cenários de Teste)

<img width="1917" height="966" alt="registro_do_objeto" src="https://github.com/user-attachments/assets/a8439e17-9392-4222-aa1d-af86a4b858fb" />

Formulário de cadastro do objeto `ENTRY2` (Cenário 1: *Atraso vs Número de Usuários*), contendo os detalhes do planejamento no campo `Document` (topologia com 32 hosts e 2 switches).

<img width="1917" height="972" alt="Registrar_objeto_cenário_2" src="https://github.com/user-attachments/assets/c029c2e3-68a2-4de7-9e72-0d7e7bbb7dfe" />

Formulário de cadastro do objeto `ENTRY23` referente ao Cenário 2 (*Influência do Número de Switches*).

<img width="1917" height="971" alt="Cenário_2_salvo" src="https://github.com/user-attachments/assets/5f3d75e3-9bd3-4a83-aa97-56aaeef5c164" />

Ecrã de confirmação do salvamento do objeto para o Cenário 2.

<img width="1917" height="965" alt="experimentos" src="https://github.com/user-attachments/assets/a8d1284d-8960-428f-b94f-13feb8879ddf" />

Visualização detalhada do objeto no sistema, exibindo as suas abas de navegação (`Data Sets`, `Children`, `Parents`, `Attachments`, etc.).

---

### 5. Gestão de Anexos e Datasets (Attachments)

<img width="1912" height="970" alt="Resultado_cenário_2" src="https://github.com/user-attachments/assets/e96f6a02-7a3c-460c-9369-353d69ccf07c" />

Visualização da aba *Attachments* do objeto `ENTRY23` antes da inclusão de ficheiros de resultado.

<img width="1912" height="962" alt="Attachments" src="https://github.com/user-attachments/assets/adf98549-89ec-47ca-bca2-e08e1037a776" />

Formulário de inclusão de ficheiro PDF contendo o relatório de ferramentas de QoS no Cenário 1.

<img width="1917" height="972" alt="Attachments_cenário_2" src="https://github.com/user-attachments/assets/8141202c-9e7d-4143-984a-e9db209876f7" />

Formulário de inclusão do ficheiro ODT com os dados de medição de atraso e regressão linear do Cenário 2.

<img width="1912" height="966" alt="Attachments_resultado" src="https://github.com/user-attachments/assets/cb3b0c82-441e-45cf-8624-9bdc8ce6912b" />

Listagem do anexo PDF registado com sucesso no Cenário 1, contendo o permalink e controlo de versões.

<img width="1917" height="967" alt="Cenário_2_salvo_Attachments" src="https://github.com/user-attachments/assets/ac519cbe-2355-4ce9-97d7-329cd34f12dd" />

Lista de anexos salvos no objeto `ENTRY23` referente ao Cenário 2.

---

### 6. Download, Configurações e Tratamento de Erros

<img width="1917" height="971" alt="download_link_cenário_2" src="https://github.com/user-attachments/assets/a2d43d35-0760-4ec6-a981-84c9d7c12661" />

Janela de descarregamento de ficheiro acionada através do link permanente (`attachment-download`).

<img width="1917" height="962" alt="Cenário_2_table" src="https://github.com/user-attachments/assets/1312e5f1-ab8d-4260-811c-2f6855c1340d" />

Janela de personalização de tabelas (*Table Settings*), utilizada para filtrar e organizar os metadados exibidos.

<img width="1917" height="967" alt="Falha_upload" src="https://github.com/user-attachments/assets/4d9c2df3-1790-4cbf-9c4d-ad3cf017d936" />

Notificação de erro (`Uploading of 'resultados_cenario2.pdf' failed`) apresentada pelo sistema durante a tentativa de envio do dataset.
