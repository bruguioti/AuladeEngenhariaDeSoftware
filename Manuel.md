```mermaid
stateDiagram-v2
    [*] --> ReceberPedido

    state Fork_Node <<fork>>
    ReceberPedido --> Fork_Node

    %% Caminho da Esquerda (Processamento do Pedido)
    Fork_Node --> PreencherPedido
    
    state ramificacao <<choice>>
    PreencherPedido --> ramificacao
    
    ramificacao --> EntregaRapida : [Se rápido]
    ramificacao --> EntregaNormal : [Se normal]

    state pontoDeUniao <<choice>>
    EntregaRapida --> pontoDeUniao
    EntregaNormal --> pontoDeUniao

    %% Caminho da Direita (Faturamento)
    Fork_Node --> EnviarFatura
    EnviarFatura --> ReceberPagamento

    %% Sincronização Final
    state Join_Node <<join>>
    pontoDeUniao --> Join_Node
    ReceberPagamento --> Join_Node

    Join_Node --> FecharPedido
    FecharPedido --> [*]
