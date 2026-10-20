# Evidências e Adaptação do LabTrove - Testes de Rede

Esta pasta reúne a documentação, ficheiros de configuração e capturas de ecrã da adaptação do ELN **LabTrove** (v2.4) para o registro de experimentos e simulações de Redes de Computadores no âmbito do TCC.

##  Deployment e Provisionamento (Docker Compose)

O ambiente da aplicação LabTrove foi containerizado e subido via Docker Compose, utilizando uma imagem personalizada conectada a uma instância de banco de dados MySQL 5.7:

```yaml
version: '3.8'

services:
  web:
    image: re2jppa/labtrove:latest
    container_name: labtrove_app
    ports:
      - "8080:80"
    environment:
      - DB_HOST=db
    depends_on:
      - db
    restart: always

  db:
    image: mysql:5.7
    container_name: labtrove_db
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: labtrove
      MYSQL_USER: labtrove
      MYSQL_PASSWORD: labtrove
    volumes:
      - db_data:/var/lib/mysql
    restart: always

volumes:
  db_data:
```
# Evidências e Adaptação do LabTrove - Testes de Rede

Esta pasta reúne a documentação, ficheiros de configuração e capturas de ecrã da adaptação do ELN **LabTrove** (v2.4) para o registro de experimentos e simulações de Redes de Computadores no âmbito do TCC.

##  Características e Limitações da Plataforma

* **Estrutura Baseada em Blog:** Funciona com uma dinâmica de entradas cronológicas e cadernos de anotações (*notebooks*). Por não impor campos rígidos da área de química ou biologia, adapta-se com facilidade a experimentos e laboratórios de redes.
* **Mecanismos de Autenticação:** Oferece suporte a múltiplos plugins de login no arquivo `config.php` (como autenticação local por usuário/senha ou OAuth).
* **Gestão e Visibilidade:** A hierarquia permite definir o nível de visibilidade de cada *notebook* (Público, Apenas Usuários Logados, Privado ou Acesso por Zona).
* **Colaboração e Linha do Tempo:** Suporta comentários em postagens e disponibiliza visualização em linha do tempo (*Timeline*) dos registros do experimento.
* **Exportação:** Possibilita a exportação integral de *notebooks* e o download dos dados em arquivo comprimido (`.zip`).
* **Limitação:** Não possui integração nativa com Jupyter Notebook.

---

##  Evidências do Ambiente e Funcionalidades

### 1. Autenticação e Gestão Administrativa

![Tela de Login](login.png)
*Figura 1: Tela inicial e formulário de autenticação do LabTrove.*

![Painel de Administração](admin.png)
*Figura 2: Painel administrativo listando usuários cadastrados, configurações do ambiente PHP/MySQL e plugins ativos.*

---

### 2. Criação, Configuração e Estrutura do Notebook

![Criação de Novo Notebook](criando_notebook.png)
*Figura 3: Formulário de criação do notebook para o experimento de garantia de atraso VoIP em SDN.*

![Configurações e Segurança do Notebook](config_notebook.png)
*Figura 4: Opções de configuração de visibilidade e níveis de acesso (Public, Logged In, Private).*

![Visualização do Notebook Vazio](notebook_vazio.png)
*Figura 5: Interface do notebook recém-criado antes da inclusão de postagens.*

---

### 3. Registro do Experimento, Postagens e Colaboração

![Login com Notebook Cadastrado](login_com_notebook_cadastrado.png)
*Figura 6: Lista de notebooks ativos exibida na interface principal.*

![Adicionando Entrada no Notebook](adicionando_entrada_notebook.jpg)
*Figura 7: Editor de postagem utilizado para registrar detalhes da metodologia, os parâmetros do ambiente experimental (Mininet e OpenDaylight) e a topologia da rede.*

![Notebook com Primeira Entrada](notebook_preenchido.png)
*Figura 8: Visualização do notebook exibindo a seção de Metodologia cadastrada.*

![Notebook com Experimento Completo](notebook_experimento_preenchido_completo.jpg)
*Figura 9: Caderno com todas as entradas preenchidas (Resultados, Cenários de Teste e Metodologia).*

![Dashboard com Dados](dashboard_com_dados.png)
*Figura 10: Painel principal listando as postagens recentes do experimento.*

![Entrada com Comentários](notebook_entrada_comentario.jpg)
*Figura 11: Seção de comentários em uma postagem, demonstrando o recurso de colaboração.*

![Linha do Tempo das Entradas](timeline_entradas.png)
*Figura 12: Visualização em linha do tempo (Timeline) organizando cronologicamente as postagens do experimento.*

---

### 4. Exportação e Download dos Dados

![Exportação do Notebook](exportar_dashboard.png)
*Figura 13: Interface de exportação de entradas do notebook com opções de vínculo.*

![Download do Arquivo Exportado](dashboard_exportado_download.png)
*Figura 14: Confirmação do processamento de exportação e link de download do arquivo comprimido (`voip_atraso.zip`).*

---

## Resumo do Experimento Registrado

* **Experimento:** Modelo para garantir o atraso máximo para conexões VoIP em uma rede SDN ODL
* **Ferramentas de Emulação:** Mininet, OpenDaylight (ODL), D-ITG
* **Entradas Registradas:**
  * **Metodologia:** Regressão linear simples e múltipla com parâmetros de taxa de dados, buffer e quantidade de hosts.
  * **Cenários de Teste:** Definição das filas de prioridade e tráfego VoIP.
  * **Resultados:** Medições efetuadas no ambiente emulado.
* **Status:** Validação concluída e dados exportados.





