# Azure

Gerenciar identidades e governança do Azure 20-25%

- Conceitos básicos Microsoft Entra ID
    - Gerencia aplicativos, autenticação, gerenciamento de dispositivos e identidade híbrida entre AD e Entra ID
    - Utiliza protocolos HTTP, HTTPS, SAML
    - Identidade: Um objeto que pode ser autentica (usuário, computadores, aplicativos, etc…)
    - Conta: Uma identidade que tenha dados associados a ela
    - Conta do Microsoft Entra ID: Uma identidade criada no MS Entra ID ou por outro serviço de nuvem da MS
    - Locatário/diretório: É a unidade organizacional daquela empresa quando essa se cadastra em uma assinatura do serviço do MS Cloud.
    - Assinatura do Azure: Usada para pagar pelos serviços do Azure
    - PIM: autoriza acesso a recursos por período limitado via solicitação a responsável, além de controle de cada acesso específico bem granular
- Autenticação
    - Autenticação nativa do AD on-premises usava Kerberos e NTLM
    - Autenticação atual com os identity managers utiliza SAML, Oauth, OPEN IP, WS-Federation que faz as comunicações de autenticação com os aplicativos e recursos da MS e parceiros
    - Existe um meio termo entre estes que são as autorizações via grupos e as autenticações do usuário
- Entra ID vs. ADDS
    - Entra ID é uma estrutura plana e não segue as UOs e GPOs conforme eram feitos no AD

Planos e Preços

Recursos comuns: Autenticação na nuvem, logon único, portal de gerenciamento da conta, MFA

- Gratuita
- P1
- P2 - Recursos exclusivos: Acesso condicional baseado em risco de entrada (risco de login, risco de usuário), Provisionamento automatizado (autopilot), PIM (Priviliged Identity Management)
- Governança - Recursos exclusivos: Provisionamento automatizado (autopilot), PIM (Priviliged Identity Management)

Configurar identidades de dispositivos:

Conceitos básicos:

- Entra ID apenas dispositivos Windows 10+, AD apenas dispositivos Winows 7+

Categorias: BYOD, Dispositivos registrados (Intune)

SSPR (SELF SERVICE PASSWORD RESET) - Portal para redefinição de senha escolhendo métodos de autenticação para confirmar se a pessoa é ela de fato APENAS LICENÇA P2 MUITO PEDIDO NA PROVA

- Administrador deve escolher se a autenticação para redefinição deve acontecer com 1 ou 2 métodos (Email, Nº celular SMS, Nº telefone comercial, Perguntas de segurança (quantas perguntas obrigatórias 3 a 5 e quantas perguntas precisa para redefinir de 3 a 5), código do aplicativo móvel, notificação do aplicativo)
- Pode ser destinado a um grupo de usuários, desabilitado ou todos

Atribuições de licenças podem falhar se não estiver atribuído uma usage location e existir uma política para impor que o usage location seja de algum país específico

Ativação da licença P2

- Só permite criação de contas que são daquele tenant (não deixa usar com e-mails externos, mesmo que seja o criador do tenant)

Configurando Contas de Usuário e de Grupo

- Para gerenciar contas de usuário e grupo deve-se ter o papel Administrador Global ou Administrador de Usuários
- Criação em massa de usuário pode ser feita via CSV padrão através da tela de usuários do entra e assim pode ser usado para exclusão também

GRUPOS

- Existem os de segurança para permissionamento e o do 365 para utilização de setores e funcionalidades
- Tipos de atribuição podem ser Atribuído, Usuário dinâmico (de acordo com as definições de regra pode ser definir quem irá para o grupo específico ex: AMCOM ALL QUE É PARA TODOS QUE TENHAM A EMPRESA AMCOM NA ORGANIZAÇÃO), Dispositivo dinâmico (Somente grupos de segurança)

UNIDADES ADMINISTRATIVA “OU do Entra ID” P1 OU P2 OU ADMIN GLOBAL

- Utiliza funções com permissões para gerenciar quais os escopos de permissão, pode ser utilizado para ser as áreas, times de locais (sc,sp,pr,etc…)

Replicações sempre acontecem AD > Entra, nunca ao contrário

Custom domain names - é o local onde se faz o registro do domínio contratado pela empresa para se utilizar nos ambientes microsoft, será gerado os dados de alias or host name (@), destination or points to adress e TTL tendo as opções TXT e MX para adicionar ao DNS do seu domínio e registrado de fato aos ambientes MS *MICROSOFT NÃO VENDE DOMÍNIOS*

RBAC Ruled Based Access Control x Roles

- Roles são papéis que o administrador pode definir aos usuários criados para que atuem e tenham permissões dentro dos ambientes microsoft
- RBAC

Quem cria um tenant novo vai sozinho para aquele tenant sendo apenas ele listado como usuário e admin daquele ambiente

- Assinaturas:
    - Usado para rateio de custos
    - Modelos de Assinatura: Gratuita, Pré-paga (cobrança mensal), CSP (contratos de parceria com parceiros MS que garantem descontos e licenças, voltado para empresas pequenas e médias), Enterprise Agreement (Um acordo, com descontos para novas licenças e software assurance - para organizações de escala empresarial DIRETO COM A MS), Aluno ($100 12 meses VIA PARCERIA COM FACULDADES) PODE SER USADO QUALQUER UM DELES EM UMA MESMA ORGANIZAÇÃO

![image.png](attachment:63f76796-682c-45ce-b419-56b22eb76d8d:image.png)

- Grupo de recursos (container)
    - Organização vai conforme a vontade do administrador, segregar por CC, projetos, produtos etc…
    - Só existe um grupo de recursos para um recurso
    - Grupo de recursos não podem ser renomeados, jamais, se quiser cria outro e move os recursos
    - Os recursos disponíveis podem ser de qualquer região independe da região do grupo de recursos
    - Não podem ser aninhados
    - COTAS da Assinatura é um ponto a ser verificado quando migrações, implementações grandes, o aumento dessa cota deve ser feito via chamado para Microsoft.
        - A cota pode barrar a instalação de algo se já estiver extrapolado comum para FAMILIAS DE MÁQUINAS, SSD DISCOS MELHORES, ETC…
        - Para as cotas pode ser solicitado um novo limite ou ajuste de %
    - Pode ser necessário ativar produtos ou serviços no resource providers
    - 

- TAG/ MARCAÇÕES NOME:VALOR são recursos não herdáveis, podem ser atribuidos de forma automática via policy
    - Se utiliza para organização logica de recursos, fornece metadados e reunir informações de cobrança
- Gerenciar custos

![image.png](attachment:26ec9364-1e90-4064-89c2-58b6638b7664:image.png)

![image.png](attachment:f978d511-677a-42bd-9c54-05e5ecc8c074:image.png)

- Azure Policy
    - Executa avaliações e varreduras em busca de recursos não compatíveis
    - A política é imposta a qualquer pessoa independente da permissão, de owner a colaborador, independe. PORÉM PODE SER QUE UM USUÁRIO ESPECÍFICO ESTEJA COM UMA EXCLUSÃO DA POLÍTICA GARANTINDO A ELE ESTRAPOLAR ALGUMA POLÍTICA
    - **As regras de negócios descritas nas Polices são descritas em qual formato? JSON**
    - Pode ser feito uma REMEDIAÇÃO que pode ir a recursos e coisas feitas anteriormente e ajustar os pontos solicitados conforme o que for configurado EX: impor TAG “Família x” para máquinas virtuais de certa assinatura
    - Vantagens: IMPOSIÇÃO e CONFORMIDADE, APLICAR POLÍTICAS EM ESCALA, REMEDIAÇÃO
    - Para política ser imposta ela tem que estar enforcement on
    - Pode ser aplicado a dispositivos, assinaturas e ambiente como manipulação de arquivos, etc…
        - Tipos de recursos permitidos
        - SKUs de VM permitidas
        - Locais permitidos
        - Exigir TAG e seus valores
        - Backup obrigatório para VMs
    - Iniciativas podem ser “moldes” de políticas para replicar para novos recursos, assinaturas, etc… como na imagem abaixo

![image.png](attachment:aeadf24b-822e-49c5-9f45-4b6ce785a8bb:image.png)

- Funções RBAC vs Funções Azure AD
    - RBAC
        - Gerenciar o acesso aos recursos do Azure
        - Parte do IAM dos recursos, grupo de recursos
        - O escopo pode ser especificado em vários níveis
        - As informações de função podem ser acessadas no portal do AZURE, CLI, POWERSHELL, AZURE RESOUCE MANAGER, NA API REST
        - é gerenciado nas role assignment (IAM) dos recursos ou grupos ou assinaturas É ONDE TEM DIVERSAS ROLES PERSONALIZADAS PARA ESCOLHER
    - Azure AD Funções
        - Gerenciar acesso aos objetos do Azure AD
        - O escopo está no nível do locatário
        - As informações de função podem ser acessadas no portal do AZURE, ADMIN DO M365, NO GRAPH, NO AZURE AD POWERSHELL PARA GRAPH
        - São as funções lá atribuídas no usuário, admin de autenticação, de usuário, de grupos, YAMMER, etc…
        
        ![image.png](attachment:acb9e503-d0d5-445a-a6c2-e469273d4cce:image.png)
        

- RBAC
    - Podem existir bloqueios (locks) para read only ou delete antes de executar as funções deve-se desabilitar, os bloqueios são herdáveis então se tiver na assinatura por exemplo tudo abaixo é bloqueado, independente da permissão do usuário porém se for movido o recurso para outro que não tenha bloqueio ele não leva o bloqueio com ele a não ser se o bloqueio for diretamente nele ai ele leva
        
        SOMENTE LEITURA BLOQUEIA TUDO MESMO NÃO PODE FAZER NADA
        
        SÓ O OWNER PODE REMOVER BLOQUEIO
        
        OS BLOQUEIOS DE READ-ONLY NÃO PERMITEM A LEITURA DAS ACCESS KEYS NAS STORAGE ACCOUNTS POIS ISSO IRIA CAUSAR UMA OPERAÇÃO DE ESCRITA DE DADOS
        
    
    - Elas podem ser aplicadas diretamente ao usuário, ao usuário dentro de uma assinatura e grupo de recursos
    
    ![image.png](attachment:c17938dd-0731-4a03-ae62-becd6d3da8b6:image.png)
    
    - Principais que caem na prova: PROPRIETÁRIO (faz tudo de fato), COLABORADOR (faz tudo que o proprietário faz porém não pode garantir permissão a outros usuários) E LEITOR
    - Principais conceitos:

![image.png](attachment:e5204ed6-fa90-4fd4-8e83-e2e02d5adb50:image.png)

![image.png](attachment:86213e14-82b9-4d63-9f0c-fa45ada4e5c5:image.png)

- Configurar Recursos do Azure com Ferramentas
    - Portal do Azure
    - Azure Cloud Shell - Bash ou PowerShell funciona localmente em qualquer OS mac,linux,win
        - Ideal para implantações em massa e que podem ser repetitivas então automatiza
        - Expira em 20 min a autenticação mas loga automaticamente
        - Precisa de um grupo de recursos e uma conta de armazenamento e um compartilhamento de arquivos no AZ
        - Módulos são um arquivo DLL com código para cada cmdlet
        - Get-Module para listar módulos carregados

- Vantagens de modelo ARM
    - Melhora a consistência e promove a reutilização
    - Reduz tarefas manuais, propensas a erros e repetitivas
    - Automatiza tarefas repetitivas
    - Cada geração de recurso pode gerar um modelo JSON para reutilização, segue modelo abaixo
    - O ARM pode ser gerado em export template na parte de automação do recursos
    
    ![image.png](attachment:6503d480-bc15-45bf-9721-a8650a75ba3f:image.png)
    

![image.png](attachment:f823da3c-0b78-4b46-b2dc-aa690dfdb62f:image.png)

- Bicep
    - Apenas para Azure então limita ao invés do Terraform que pode ser usado multicloud
    - Sintaxe mais simples para escrever modelos
    - Arquivos menores do que os modelos ARM

 Implantar e gerenciar os recursos de computação do Azure 20-25%

 ![image.png](attachment:4ca3b300-3dfc-4ed6-b881-7c56958fc299:image.png)

- Planejamento de VMs pode ser seguindo da seguinte maneira
    - Iniciar com a rede para provisionar já conforme os padrões de sua organização
    - Nomear a VM conforme políticas internas e função
    - Definir local, pode ser restrito via policy e basear de acordo com a necessidade do usuário final
    - Considerar os preços no momento de escolher SKU, disco, replicação
- Armazenamento
    - Pode ser adicionado depois da criação ou antes
    - Disco temporário morre junto com a máquina sempre que desliga, reinicia, etc…
    - Modelo possíveis são Standard (HD ou SSD), Premium ou Ultra (SSD)
- Tempo de inatividade
    - Pode haver manutenção de hardware não planejada que é migrado para outro hospedeiro a VM
    - Tempo de inatividade inesperado migra automaticamente
    - Manutenção planejada onde o azure avisa e deve mover de local para evitar paradas inesperadas
- Conjunto de disponibilidade DISTRIBUI ENTRE DIFERENTES RACKS PARA EVITAR FALHA
    - 2 ou mais instâncias em conjuntos tem SLA de 99,95% de SLA
    - Domínio de falha vs domínio de atualização
        - Falha é o rack
        - Atualização são as máquinas lado a lado
        
        ![image.png](attachment:8d4b158b-7592-4933-b0da-1c55969c22a8:image.png)
        

![image.png](attachment:372f9bdb-266d-4e35-89ac-482fbd7f5d8e:image.png)

- Zona de disponibilidade
    - Fornece SLA de 99,99
    - Envolve replicar o recurso entre mais de uma zona
- Escala vertical X horizontal
    - Vertical: aumento ou redução é o processo de aumentar ou diminuir a potência para uma única instância de uma carga de trabalho, geralmente manual
    - Horizontal: aumenta o número de instâncias de um set de VMs para atender a uma carga de trabalho, é feito frequentemente de forma automatizada *requer que o serviço seja preparado para escalonamento* pode ter de *0 A 10*
- VM Scale Set
    - O tempo padrão para um VM sacle set criar mais um é 10 e a quantidade mínima padrão para VMs é de 2 e de CPU 80/20%

Implementar e gerenciar redes virtuais 15-20%

- Planejamento de redes virtuais
    - A comunicação entre o local da organização e as redes do azure são feitos através de VPN, local seguro, redes virtuais, express route (serviço da MS)
    - Deve se ter cuidado para sobreposição de IPs entre on-premises e nuvem
    - Por padrão mas não obrigatório redes virtuais são chamadas de VNet1,2,3,etc…
    - Quando for criado um rede virtual a sub-rede já é criada automaticamente, e elas já se enxergam automaticamente DENTRO DA MESMA VNET, FORA DA MESMA VNET NÃO SE ENXERGAM
- Planejamento do endereçamento IP
    - IPs privados: válido dentro do ambiente privado
    - IPs públicos: válido dentro do ambiente público
    - Quem pode receber um IP public no azure:
    
    ![image.png](attachment:063a733a-6b6a-43a5-ab23-34db38e7d263:image.png)
    
    - Quem pode receber um IP privado no azure:

![image.png](attachment:93c6c1a2-9283-42f1-8a95-c727969aaf58:image.png)

- Grupos de segurança de rede NSGs
    - Atua limitando o tráfego de rede a uma rede virtual
    - Controla saída e entrada de portas
    - Pode ser associado várias vezes
    - As regras NSG são de acordo com nível de prioridade tanto para entrada quanto saída, indo da mais baixa para mais alta em nível de aplicação dessas regras REGRAS SÃO APLICADAS NA SUBREDE
        - NSG pode ser aplicado na máquina na placa de rede ou na SUBREDE mas ai as alterações não se conversam então mantém apenas na SUBREDE
    
    ![image.png](attachment:ef288fc3-3999-4bda-a9bd-1800b5fab85a:image.png)
    
- ASG
    - Muda para o contexto de aplicações
    - Pode ser usado junto a um NSG para maior segurança
    - ASG agrupam logicamente VMs - servidores, serviços, ETC…

- DNS
    - Quando cria um locatário do AAD um novo domínio padrão é criado com a nomenclatura, [domainname.onmicrosft.com](http://domainname.onmicrosft.com) e pode ser adicionado um domínio seu e verificado através de um registro no seu DNS É USADO TXT OU MX
    - MS não vende domínios
    - Pode ser adicionado até 20 registro em qualquer conjunto de registros de DNS
    - Zonas de DNS podem ser usadas para loadbalancer
- Emparelhamento de VNET ***é o que mais cai na prova, focar no estudo***
    - É o chamado Peering
    - Serve para fechar uma conexão segura, rápida e confiável entre as VNETs, como se fosse uma IPsec
    - Por padrão VNETs criadas não se enxergam então por isso se faz necessário o peering
    - Existe o peering regional e o global, conforme regiões e imagem abaixo: O PEERING É NECESSÁRIO SER FEITO UMA A UMA, POR EXEMPLO NA IMAGEM A VNET1 NÃO TEM PEERING COM VNET3 ENTÃO EELAS NÃO SE COMUNICAM POR “TABELA” POR AS DUAS ESTAREM SE COMUNICANDO COM A VNET2
    
    ![image.png](attachment:bb76e1e9-b28a-4442-90f5-5a7e5bc00b60:image.png)
    

- Trânsito de gateway e necessidades de conectividade
    - É uma rede que serve como “HUB” para o ambiente onpremises e ambiente nuvem onde podem estar proteções para essas conexões

![image.png](attachment:f036d096-0a9a-4b66-a3bb-5dbd2b0875de:image.png)

- Rotas de Sistema
    - O usuário pode criar rotas personalizadas para além das rotas já existentes do AZURE
    - Pode ser configurado pontos de extremidade onde pode definir até qual IP pode ser acessado ou quais IPs podem acessar tal IP ou se irá estar disponível para tráfego na internet ou para outros serviços do azure

![image.png](attachment:af871e3c-55d2-4bef-8e42-3e7920325cbd:image.png)

- Conectividade entre sites
    - Route tabels podem ser movidos entre assinaturas e grupo de recursos
    - Route tabels Define **o caminho que o tráfego deve seguir**. Ex: todo tráfego para a internet vai pro Azure Firewall, ou pra um appliance. Ela **não altera o IP** da origem ou destino.
- Azure Load Balancer
    - Equilibra conexões e solicitações de entrada e saída em seus aplicativos ou pontos de extremidade de servidor
    - Recursos compatíveis com NVA seriam no SKU GATEWAY que não aparece ainda em todas as documentações mas já é disponível e o BASIC entrará em desuso E O GATEWAY FICA EXPOSTO APENAS PARA INTERNO
    - Apenas atua na camada 4 IP e porta
    - Apenas para AZURE

![image.png](attachment:ae99ed6b-319f-47b4-9143-882865cfcbce:image.png)

![image.png](attachment:bc600f46-d8fa-4413-aba8-f0d24e60bcb6:image.png)

- Gateway de aplicativo
    - É o local onde vai chegar a conexão para ai sim direcionar para os pools de VM, conjunto de dimensionamento de VMs, serviço de aplicativo do AZ e até servidores locais
    - O nome do host, a porta e o caminho na URL da solicitação. ATUA NA CAMAD A7
    - disponível para qualquer infra, nuvem, azure, onprems
- Observador de rede NETWORKWATCHER
    - É criado de forma automática quando são criados recursos justamente para fazer essa função CRIA UM GRUPO DE RECURSOS CHAMADO NETWORKWATCHERRG E DENTRO UM PARA CADA REGIAO
    - Tem funções de testes como:
        - Verificação de fluxo de IP testa se a conexão fecha ou não e apresenta quais motivos
        - Diagnóstico do próximo salto
            - O **Azure Network Watcher** oferece **Packet Capture**, que permite:
                - **Monitorar tráfego** em VMs ou scale sets.
                - Analisar problemas de rede e identificar tráfego suspeito.
                - Filtrar capturas por porta, IP ou protocolo.
                - Salvar capturas em **Storage Account** para análise com Wireshark.
    - Tem funções de visualização de dados de rede:
        - Visualizar a topologia de rede

![image.png](attachment:d8c85c52-059c-4e8c-97bd-efcc48c5249b:image.png)

### 🗺️ Guia-flash de **TODOS** os balanceadores de carga do Azure

*(o mínimo que você precisa lembrar na hora de configurar)*

| Fase comum a TODOS | O que fazer | Onde muda |
| --- | --- | --- |
| **1 . Front-end** | Escolha o **IP** (estático x dinâmico, público x privado). | *Front Door* e *Traffic Manager* já vêm com **Anycast** global; os demais pedem IP que você define. |
| **2 . Back-end Pool** | Aponte para VMs, VM SS, App Service, IPs, NICs ou endpoints. | *Traffic Manager* usa **FQDNs**/URLs; *App Gateway* aceita **App Service** direto; *Load Balancer* só recursos de IaaS. |
| **3 . Probes** | Configure **health probe** (porta + protocolo) para remover instâncias doentes. | *App Gateway* permite **probes HTTP/S customizados**; os demais são TCP/HTTP simples. |
| **4 . Regra de roteamento** | Defina **porta/protocolo** de entrada → porta de destino. | Diferenças:  • *Load Balancer* → regra L4 (`lb rule`) • *App Gateway* → regra **listener + path-based/host-based** • *Front Door* → **routing rule + backend set + policy** • *Traffic Manager* → **método de roteamento DNS** (Prioridade, Performance, etc.) |
| **5 . Segurança** | NSG, Azure Firewall ou WAF. | Só *App Gateway* e *Front Door* têm **WAF integrado**. |

---

## ⚙️ Ajustes-chave por tipo

| Serviço | Camada | Alcance | Distribuição padrão | Ajustes que mais caem na prova |
| --- | --- | --- | --- | --- |
| **Azure Load Balancer (Standard)** | L4 (TCP/UDP) | Regional | **Hash 5-tuplas** (afinidade opcional) | Outbound SNAT, HA Ports, Floating IP, reglas inbound NAT. |
| **Application Gateway v2** | L7 (HTTP/S) | Regional | **Round Robin** (com path/host routing) | WAF, SSL offload, reescrita de header, sessão “cookie-based persistence”, WebSocket. |
| **Azure Front Door (Standard/Premium)** | L7 Global | Global | **Anycast + latência** | Rules Engine, WAF global, aceleração TLS, caching edge. |
| **Traffic Manager** | DNS | Global | **Performance / Prioridade / Weighted / Sub-net** | TTL, endpoints externos, redireciono de Failover cross-region. |
| **Azure Gateway Load Balancer** | L4 | Regional | Flow hashing | Encapsulamento VXLAN para inserir NVAs inline. |

---

## 🧠 Lembre-rápido das diferenças-de-prova

- **Quem faz NAT automático outbound?**
    
    *Load Balancer Standard* (SNAT).
    
- **Quem decide rota com base no conteúdo (URL/host)?**
    
    *Application Gateway* e *Front Door*.
    
- **Quem escolhe a região mais próxima antes mesmo de chegar no Azure?**
    
    *Front Door* (Anycast) ou *Traffic Manager* (DNS).
    
- **WAF integrado?**
    
    Apenas *Application Gateway* (regional) e *Front Door* (global).
    
- **Camada 4 puro e barato para IaaS?**
    
    *Azure Load Balancer*.
    
- **Inspecionar/forçar tráfego por appliance de terceiros?**
    
    *Gateway Load Balancer* (in-line NVAs).

Implementar e gerenciar o armazenamento 15-20%

- QUE MAIS CAI NA PROVA

- Contas de armazentamento STORAGE ACCOUNTS
    - Configurações possíveis TODOS OS PREMIUM JÁ ARRANCA PAGANDO TODO O ESPAÇO CONTRATADO JÁ OS STANDARD PAGA CONFORME USO E NÃO É POSSÍVEL ALTERAR DEPOIS premium acontece apenas em LRS E ZRS
        - Geral V2 Standard: inclui blob, arquivo, fila, tabela e data lake storage
        - Blocos premium: blob de blocos que exigência latência baixa
        - Arquivos premium: níveis de alto desempenho para arquivos
        - Blobs premium cenários de blob de páginas premium
    - Pode conter seguintes, mesmo que simultaneamente
        - Contêiner
        - Tabela
        - Fila
        - Arquivos
    - Estratégias de replicação
        - LRS Local redundant storage - 3 réplicas de dados em uma região, recomendado para não produção
        - ZRS Zone redundant storage - 3 réplicas em 3 zonas e uma região
        - GRS Geo redundant storage - 6 réplicar em duas regiôes (3 por região), cópia assíncrona para região secundária e nas regiões LRS - NÃO PERMITE READ NA SECUNDÁRIA
        - RA-GRS - igual a GRS porém permite a consulta na região secundária, pode ser útil para utilização de informações com baixa latência em mais de uma região RA de read
        - GZRS - 6 réplicas em 3+1 zonas, duas regiões não permite leitura na secundária
        - RA-GZRS - 6 réplicas em 3 + 1 LRS zonas, duas regiões permite leitura na secundária
        - Dicas RA permite leitura na secundária, Z replica entre as 3 regiões da zona ficando

![image.png](attachment:a88385d1-8dc3-423e-a930-45e3f6207842:image.png)

![image.png](attachment:ae555fde-aca0-4a36-bec2-2834acf5653b:image.png)

- Configuração de Blobs:
    - Arquivos gerais, vídeos, fotos, gifs, etc… com foco em utilização para aplicações para guardar apenas arquivos ai é o Arquivos do Azure mapeamento de // etc…
    - Pode ser os seguintes niveis de acesso: Privado (sem acesso anônimo), Blob (acesso de leitura anônimo somente para blobs), Contêiner (acesso de leitura anônimo somente para contêineres e blobs)
    - As contas têm contêineres ilimitados
    - Tem as possíveis camadas de acesso: Principal, Agradável 30 DIAS, Frio  90 DIAS e Arquivar 180 DIAS
    - Podem ser criadas regras para mover entre as camarada por tempo de criação e de alteração CICLO DE VIDA DO ARQUIVO

- Segurança do armazenamento:
    - Pode ser das seguintes formas:
        - Criptografia do serviço de armazenamento
        - Autenticação com ENTRA ID E RBAC
        - Assinaturas de acesso compartilhado (Shared acess), acesso delegado
        - Chave compartilhada - cadeia de caracteres de assinatura criptografada
        - Criptografia do lado do cliente. HTTPS e SMB 3.0 para dados em trânsito
        - Criptografia de disco do AZ
        - Acesso anônimo a contêineres e blobs
        
        ![image.png](attachment:fc2f6267-adbc-46f1-be73-2637abfb7293:image.png)
        

![image.png](attachment:dab017b7-a1ea-4a30-a373-f9d56ae1fda4:image.png)

- Arquivos do Azure
    - Acessa via SMB o famoso público ou // direto na máquina
    - Arquivos tem que garantir o usuário que vai ser autenticado para dar o acesso
    - Deve se definir quais OSs que podem ser acessados mac linux windows
    - Porta 445 para o azure files NORMALMENTE OPERADORAS BLOQUEIAM
    - Linux e MacOS precisa montar a unidade
- Serviço de importação e exportação
    - Você mesmo envia seus discos para MS e eles importam para o servidor
    - Pode solicitar o Azure Data Box que tem 40tb para transferir
 
Monitorar e manter os recursos do Azure 10-15%

- Configuração de backups de arquivos e pastas
    - Centro de backup é o local onde gerencia os backups de todos os recursos
    - Backup é responsabilidade total sua a MS fornece apenas os recursos para isso
    - MARS é um client que faz backup local
    - Recovery Service Vault é o local onde os backups serão salvos e para apontar ele como local para salvar o backup é preciso que os recursos estejam na mesma região PODE BOTAR QUANTOS BACKUPS QUISER

![image.png](attachment:3130fa31-ba9f-4063-a7e0-2fd94b761014:image.png)

- Configuração de backups de VMs
    - Instântaneos são formas de fornecer opção simples e rápida para backup das VmS QUE USAM DISCOS GERENCIAODR para o MABS que não suporte LINUX ou os COFRES para MARS e MABS que ai sim suporta linux
        - Os snapshots são armazenados no Vault e precisa ta na mesma região
        - Pode ter retenção de 1 a 5 dias e ai podem ser configurados backups e não snapshots para períodos maiores que isso
    - Backup de VM é compatível para WIN E LINUX apenas MARS não é
    - ASR AZ SITE RECOVERY protege de um caso mais grave quando a região toda sofre interrupção fica uma cópia em outra região para subir em caso de falha
    - Para funcionar o agente tem que estar instalado tanto win quanto linux
    - Para a restauração de um backup é feito no painel
    
    ![image.png](attachment:be63d94f-84e6-4a0e-bd89-3756afe71861:image.png)
    
    - 

![image.png](attachment:5a39c50e-425d-466b-a546-a0456cae45dd:image.png)

![image.png](attachment:1e9203fb-bb2f-4286-854a-1096ae0d0efc:image.png)

- Existe a policy Standard que faz backup uma vez por dia e Enhanced que pode fazer até a cada 1h
- Para excluir o vault tem que parar as rotinas de backup primeiro mesmo se excluir a VM não vai poder excluir o vault ainda assim

- Azure Monitor
    - Heartbeat pode ser usado para o log analytics consultar
    - Quando é ativado monitoramento é necessário criar um workspace
    - Service health mostra os service issues no país todos e como estão a saúde das zonas e quais serviços afetados se estiverem com problema
    - Os alertas do monitor vão para o AZ Monitor Metricas e Logs que posteriormente segue para as regras dos alertas conforme a ferramenta definida e assim saindo para as ações a serem tomadas
    - Monitorar Linux é via Syslog
    - Quando um alerta é reconhecido quer dizer que alguém já está atuando nele
    - Contém alguns recursos principais para monitor disponibilidade, desempenho, os erros, o uso do seu aplicativo, insights de segurança, etc…
        - Application Insights: Disponibilidade, desempenho os erros e o uso do seu aplicativo
        - Insights de Contêiner
        - Insights de VMs
        - Insights de Rede
            
            ![image.png](attachment:f5e245d6-85aa-4112-82be-607e34045235:image.png)
            
    - Métricas X Logs
        - Métrica são as informações de desempenho e coisa específicas que vc deseja monitorar de forma constante e enviada a um proxy para ser monitorado
        - Logs são registros constantes de atividades dos recursos, como acesso, erros, instalações, etc…
    - Os logs podem ser consultados no Log Analytics via KQL dentro do workspace de monitoramento onde estão os recursos que pretende consultar

![image.png](attachment:ec44bf7e-5a19-420a-b94d-4f5d2d2b103e:image.png)
