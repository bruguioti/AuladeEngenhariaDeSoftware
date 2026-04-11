```mermaid
flowchart TD
    start((Inicio)) --> receber[Receber Pedido]

    receber --> fork{Fork}

    %% Fluxo de Entrega
    fork --> preencher[Preencher Pedido]
    preencher --> decisao{Tipo de Entrega}
    
    decisao -- Rapida --> entrega_rapida[Entrega Rapida]
    decisao -- Normal --> entrega_normal[Entrega Normal]

    entrega_rapida --> uniao{Uniao}
    entrega_normal --> uniao

    %% Fluxo paralelo financeiro
    fork --> fatura[Enviar Fatura]
    fatura --> pagamento[Receber Pagamento]

    %% Junção final (join)
    uniao --> juncao{Juncao}
    pagamento --> juncao

    juncao --> fechar[Fechar Pedido]
    fechar --> fim((Fim))
