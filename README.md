# RELATÓRIO DE IMPLEMENTAÇÃO DE SERVIÇOS AWS

**Data:** 05/10/2026
**Empresa:** Abstergo Industries (rede de farmácias)
**Responsável:** Guilherme Skorupa

## Introdução
Este relatório apresenta o processo de implementação de ferramentas na empresa Abstergo Industries, realizado por Guilherme Skorupa. O objetivo do projeto foi elencar 3 serviços AWS, com a finalidade de realizar diminuição de custos imediatos na operação de uma farmácia, substituindo infraestrutura própria (servidores locais, armazenamento físico e bancos de dados autogerenciados) por serviços em nuvem com cobrança sob demanda.

## Descrição do Projeto
O projeto de implementação de ferramentas foi dividido em 3 etapas, cada uma com seus objetivos específicos:

### Etapa 1
- **Ferramenta:** Amazon S3 (com a classe S3 Intelligent-Tiering e regras de ciclo de vida)
- **Foco da ferramenta:** Redução de custos de armazenamento e backup.
- **Caso de uso:** A farmácia gera grande volume de dados não estruturados: digitalizações de receitas, XMLs de notas fiscais, laudos, contratos com fornecedores e cópias de segurança. Esses arquivos deixam de ocupar servidores e HDs locais e passam para buckets S3. Como o padrão de acesso é imprevisível, o Intelligent-Tiering move os objetos automaticamente entre camadas de acesso e a regra de ciclo de vida arquiva o que precisa ser guardado por obrigação legal. Paga-se apenas pelo que é armazenado, com durabilidade de 99,999999999% e sem compra de hardware.

### Etapa 2
- **Ferramenta:** Amazon RDS (PostgreSQL ou MySQL, com Multi-AZ)
- **Foco da ferramenta:** Redução de custos operacionais e de administração do banco de dados.
- **Caso de uso:** O banco do sistema de gestão (estoque, vendas, cadastro de clientes e controle de medicamentos) é migrado de um servidor próprio para o RDS. O serviço gerenciado automatiza patches, backups, redundância, failover e recuperação de desastres, eliminando hardware dedicado, licenças de infraestrutura local e horas de administração repetitiva. Para cargas estáveis, Instâncias Reservadas reduzem ainda mais o custo em relação ao preço sob demanda.

### Etapa 3
- **Ferramenta:** Amazon EC2 com Auto Scaling e Savings Plans
- **Foco da ferramenta:** Redução de custos de computação, ajustando a capacidade à demanda real.
- **Caso de uso:** Os servidores do ERP, do PDV integrado e do e-commerce/aplicativo da farmácia passam a rodar em instâncias EC2 dimensionadas conforme a demanda. O Auto Scaling aumenta a capacidade em horários de pico e reduz de madrugada, evitando pagar por servidores ociosos. Para a base fixa de consumo, os Savings Plans oferecem desconto mediante compromisso de uso, e para processamento de logs e relatórios, volumes EBS HDD otimizados para throughput (st1) oferecem melhor custo por GB.

## Conclusão
A implementação de ferramentas na empresa Abstergo Industries tem como esperado *a redução de custos com infraestrutura física, armazenamento, administração de banco de dados e capacidade de computação ociosa, além de maior disponibilidade e segurança dos dados*, o que aumentará a eficiência e a produtividade da empresa. Os percentuais exatos de economia devem ser validados com a AWS Pricing Calculator e com o histórico de consumo da empresa. Recomenda-se a continuidade da utilização das ferramentas implementadas, o acompanhamento mensal de custos com o AWS Cost Explorer e a busca por novas tecnologias que possam melhorar ainda mais os processos da empresa.

## Anexos
- Estimativa de custos (AWS Pricing Calculator) – [a anexar]
- Inventário da infraestrutura atual – [a anexar]
- Plano de migração e cronograma – [a anexar]
- Política de retenção de documentos e backups – [a anexar]

**Assinatura do Responsável pelo Projeto:**

Guilherme Skorupa
