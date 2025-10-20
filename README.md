# ARQUITETURA E SERVIÇOS AZURE

## Componentes da Arquitetura do Azure <br>
- Descrever regiões, pares de regiões e regiões soberanas do Azure.
- Descrever as zonas de disponibilidade.
- Descrever os datacenters do Azure.
- Descrever os recursos e os grupos de recursos do Azure.
- Descrever as Assinaturas.
- Descrever os grupos de gerenciamento.
- Descrever a hierarquia de grupos de recursos, assinaturas e grupos de gerenciamento.
<br>
<br>


### REGIÕES
Cada região é um conjunto de instalações físicas que incluem datacenters e infraestrutura de rede.
<br>

<img width="654" height="376" alt="Azure-region1" src="https://github.com/user-attachments/assets/4a7e3587-faab-443b-9a7c-5037fe37edba" />

<br>
<br>

***Várias regiões do Azure fornecem zonas de disponibilidade,*** *que são grupos separados de datacenters em uma região. Cada zona de disponibilidade tem energia, resfriamento e infraestrutura de rede independentes, para que, se uma zona sofrer uma interrupção, os serviços regionais, a capacidade e a alta disponibilidade sejam compatíveis com as zonas restantes.*


> As regiões são compostas de um ou mais datacenters muito próximos.
* É necessário ter em mente que teremos cerca de 3 datacenters por região (isso forma uma zona de disponibilidade - um bloco autossustentável)*

> Eles fornecem flexibilidade e escala para reduzir a latência do cliente.

<br>

Cada região está contida em uma única geografia que serve como um limite de residência de dados fixo. Caso tenha requisitos de residência de dados, é importante selecionar regiões dentro da geografia necessária. Cada geografia tem pelo menos uma região equipada com zonas de disponibilidade.

<br>

> As regiões preservam a residência dos dados com uma oferta abrangente de conformidade.
<br>

*Nesse caso, é necessário levar em consideração a LGPD: se tratando de dados confidenciais, eu preciso validar se isso está em compliance e se eu posso levá-los para fora do território nacional ou não.
* Nesse caso a própria Microsoft garante que não vai ficar movimentando as minhas informações (ela é proprietária dos recursos não da informação).

<br>
<br>

#### Escolhendo Regiões do Azure

* Latência. Selecione regiões que estão geograficamente próximas aos usuários para reduzir a latência. Por exemplo, se os usuários estiverem nos Estados Unidos, você poderá selecionar uma região nos Estados Unidos ou canadá.

* Zonas de disponibilidade. Selecione regiões que dão suporte a zonas de disponibilidade para fornecer redundância e isolamento de falhas. Verifique se você espalhou seus recursos em várias zonas de disponibilidade na região.

* Residência de dados: Verifique se todas as regiões selecionadas estão dentro de um limite de residência de dados exigido pela sua organização.

<br>
<br>

#### ZONAS DE DISPONIBILIDADE

ZONA DE DISPONIBILIDADE == DATACENTER <br>

Uma zona de disponibilidade é um agrupamento lógico de um ou mais datacenters fisicamente separados em uma região. Cada zona de disponibilidade é criada de uma maneira que, se algo der errado em uma (como uma interrupção de energia ou um problema de rede), as outras continuarão funcionando. Um único datacenter não oferece esse nível de proteção por conta própria.

<br>
<img width="494" height="411" alt="Azure-region2" src="https://github.com/user-attachments/assets/52129d66-0cfa-4021-ae65-17f17a30f9fb" />


<br>

* Fornece proteção contra tempo de inatividade devido a falha do datacenter.

* Separa de forma física os datacenters dentro da mesma região.

* Cada datacenter é equipado com alimentação, resfriamento e rede independentes.

* Conectadas por meio de redes privadas de fibra óptica.

<br>

Entendendo Pares de Região e Grupo de Recursos

#### PARES DE REGIÃO
***TODA REGIÃO POSSUI UMA REGIÃO PAR; ESSA REGIÃO PAR É PARA ONDE OS MEUS SERVIÇOS DE DISASTER RECOVERY SERÃO DIRECIONADOS.***

As regiões do Azure são independentes umas das outras. No entanto, a Microsoft associa algumas regiões do Azure a outra região, em que ambas geralmente estão na mesma geografia. Juntas, as regiões formam um par de regiões.

>>> Cada região possui uma região par que vai atuar como uma zona secundária em caso de indisponibilidade na região original.

* No mínimo 300 milhas de separação entre pares de regiões.
  
* Replicação automática para alguns serviços.

* Recuperação de região priorizada em caso de interrupção.

* As atualizações são distribuídas sequencialmente para minimizar o tempo de atividade.

<br>

No entanto, muitas regiões não são organizadas em pares e, em vez disso, usam zonas de disponibilidade como o principal meio de redundância. Além disso, muitos serviços do Azure dão suporte à redundância geográfica, quer as regiões sejam emparelhadas ou não.

<br>

**Mais sobre Pares de Regiões:**
[https://aka.ms/PairedRegions-ptb](https://aka.ms/PairedRegions-ptb)

<br>

Pares de região:<br>

<img width="628" height="420" alt="Pares-regiao" src="https://github.com/user-attachments/assets/5adb0764-89c0-4cea-bf4d-9234eedb6f2a" />

<br>
<br>

#### REGIÕES SOBERANAS DO AZURE

*Regiões da Microsoft que estão disponibilizadas para clientes específicos (Regiões exclusivas - como para o governo dos USA).*
<br>

**Serviços Governamentais dos EUA**
* Atende às necessidades de segurança e conformidade das agências federais, governos estaduais e locais dos EUA e seus provedores de soluções.

* É uma região disponibilizada apenas para a área militar;

* Instância separada do Azure.
* Fisicamente isolada de implantações que não sejam do governo dos EUA.
* Acessível somente ao pessoal verificado e autorizado.

<br>
<br>

**Azure China**
A Microsoft é o primeiro provedor estrangeiro de serviços de nuvem pública da China, em conformidade com as regulamentações governamentais.
<br>
* Fisicamente separada dos serviços de nuvem do Azure e operados pela 21Vianet.
* Todos os dados permanecem dentro da China para garantir a conformidade.

<br>

### RECURSOS DO AZURE

Os recursos do Azure são componentes como armazenamento, máquinas virtuais e redes que estão disponíveis para criar soluções de nuvem.
<br>

<img width="578" height="253" alt="recursos-1" src="https://github.com/user-attachments/assets/d023a313-d138-4c59-953b-04d8873a34c6" />

<br>
<br>

<img width="611" height="429" alt="recursos-2" src="https://github.com/user-attachments/assets/4b464543-2e5d-4f7c-993b-431a2c4bbf1e" />

<br>

*É importante não analisar apenas os recursos, mas as soluções em si.*

> Os recursos não precisam estar dentro da mesma região.
> É possível movimentar os recursos para outro grupo de recursos.


* Um grupo de recursos é um contêiner que você usa para gerenciar e agregar recursos em uma única unidade.

* Os recursos podem existir em apenas um grupo de recursos;
* Os recursos podem existir em diferentes regiões.
* Os aplicativos podem utilizar vários grupos de recursos.

>>> Não é possível renomear um grupo de recursos

<br>
<br>

### ASSINATURA DA AZURE E GRUPOS DE GERENCIAMENTO
<br>

<img width="707" height="504" alt="assinatura_azure1" src="https://github.com/user-attachments/assets/0d5bf1fc-305e-402f-8516-122474b8a9b8" />

<br> 

Quando criamos nossa conta, teremos apenas uma única assinatura associada.

> É possível ter várias assinaturas (isso é comum nas empresas).

Para entender melhor:
Esse cenário é comum, por exemplo, em empresas multinacionais, devido a quantidade de recursos que a mesma precisará ter.
> Uma assinatura para o pessoal de desenvolvimento, outra para o RH / Administrativo, etc.

#### O que precisamos saber à nível de prova, é que uma conta pode ter várias assinaturas, mas uma assinatura está associada apenas à uma conta.

**UMA CONTA  → [contem] → VÁRIAS ASSINATURAS**
<br>
<br>
UMA ASSINATURA → [Associada] → UMA CONTA

*Para cada conta do Azure eu posso ter quantas assinaturas eu puder; Para cada assinatura ela está respondendo para apenas uma conta.*

Para cada assinatura eu vou ter uma fatura.
> Muitas vezes as empresas usam para um projeto específico.
> Isso ajuda a definir o centro de custo da assinatura (qual departamento irá custear essa assinatura);


* Uma assinatura do Azure fornece a você acesso autenticado e autorizado às contas do Azure.

* Limite de cobrança:
gere relatórios de cobrança e faturas separados para cada assinatura

* Limite do controle de acesso:
gerenciar e controlar o acesso aos recursos que os usuários podem provisionar com assinaturas específicas.

<br>
<br>

### GRUPOS DE GERENCIAMENTO

(Hierarquia)
<br>

<img width="769" height="520" alt="Grupos_gerenciamento1" src="https://github.com/user-attachments/assets/361e6d45-2461-4460-95a6-907ea0336479" />

<br>

* Os grupos de gerenciamento podem incluir várias assinaturas do Azure.

* As assinaturas herdam as condições aplicadas ao grupo de gerenciamento.

<br>

#### Revisão do conteúdo: <br>
(O que aprendemos até aqui?) <br>

* Regiões, pares de regiões e regiões soberanas do Azure
* Zonas de disponibilidade e datacenters do Azure.
* Recursos e os grupos de recursos do Azure.
* Assinaturas e grupos de gerenciamento.
* Hierarquia de grupos de recursos, assinaturas e grupos de gerenciamento.
<br>

**DOCUMENTAÇÃO:**
<br>
[https://learn.microsoft.com/training/modules/describe-core-architectural-components-of-azure/3-get-started-azure-accounts](https://learn.microsoft.com/training/modules/describe-core-architectural-components-of-azure/3-get-started-azure-accounts)
<br>
[https://learn.microsoft.com/training/modules/describe-core-architectural-components-of-azure/1-introduction](https://learn.microsoft.com/training/modules/describe-core-architectural-components-of-azure/1-introduction)
<br>
[https://learn.microsoft.com/training/modules/describe-core-architectural-components-of-azure/5-describe-azure-physical-infrastructure](https://learn.microsoft.com/training/modules/describe-core-architectural-components-of-azure/5-describe-azure-physical-infrastructure)
<br>
[https://learn.microsoft.com/training/modules/describe-core-architectura-components-of-azure/5-describe-azure-physical-infrastructure](https://learn.microsoft.com/training/modules/describe-core-architectura-components-of-azure/5-describe-azure-physical-infrastructure)
<br>




