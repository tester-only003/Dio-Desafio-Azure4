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










