
# Objetivo:
Documentar o fluxo de processo para manipulação de um pedido, conforme o diagrama fornecido. Este diagrama modela as atividades envolvidas desde o recebimento do pedido até o seu fechamento, com foco especial no processamento paralelo de faturamento e entrega.


# Descrição Visual do Fluxo:

O diagrama é um Diagrama de Atividades UML que utiliza um nó de controle Fork e um nó de controle Join para gerenciar o paralelismo.

* Início: Começa no nó inicial (círculo preto).

Atividade 1 (Linear): A primeira atividade é Receber Pedido.

Fork (Divisão em Paralelo): Após "Receber Pedido", há uma barra horizontal preta (Fork). Ela separa a transição em duas vias que executam ao mesmo tempo.

Caminho A: Preencher Pedido -> Realizar Entrega

Caminho B: Enviar Fatura -> Receber Pagamento

Join (Sincronização): Após "Realizar Entrega" e "Receber Pagamento", ambas as vias convergem para outra barra horizontal preta (Join). O fluxo só avança após a conclusão de ambas as atividades anteriores.

Atividade Final (Linear): Após o Join, a última atividade é Fechar Pedido.

Fim: Termina no nó final (círculo preto com contorno).

* Requisitos de Implementação/Documentação
Utilizar exatamente esta lógica de negócios.

Garantir que os caminhos de Faturamento e Entrega possam ser processados de forma assíncrona/paralela.

O pedido não pode avançar para o estado "Fechado" até que a entrega tenha sido realizada e o pagamento tenha sido recebido.

(Opcional) Recriar este diagrama em um formato digital editável (ex: ;, draw.io ou Mermaid.js).
