# Encontrando os Domínios (Bounded Contexts)

Seguiremos com o design de software monolito e modular, ou seja, cada modulo dentro da mesma base de codigo será um domínio isolado com regras bem definidas e baixo acomplamento entre outros dominios. Cada dominio deve gerenciar seu próprio estado e tabelas. 

A intenção dessa primeira etapa é isolar todos os domínios respondendo perguntas que ajudarão no processo:

- **Oportunidade (Alpha/Signal):** Quem é responsável por olhar os livros de ofertas e calcular se o spread compensa? Esse módulo guarda histórico ou é puramente efêmero (calcula em memória e joga fora)? 
    - **Motor de Oportunidades:** Ele olha para todos os livros de ofertas e calcula o spread, e com base nos dados de contexto do mercado ele decide se emite um sinal de oportunidade quando os critérios configurados e os dados de contexto do mercado atendem a estratégia de negócio. Quem coordena as pernas (mercados) e executa são outros modulos que receberão esse sinal.  

- **Gestão de Ordens (OMS/Saga Orchestrator):** Onde fica o "cérebro" que sabe que a Operação X é composta pela Perna A e Perna B? Quem guarda o estado global (Pendente, Executada Parcialmente, Compensando, Concluída)?

- **Conectores de Venue (Execution/Adapters):** Como você vai isolar a complexidade de cada exchange (ex: Binance vs. Mercado Bitcoin)? Cada exchange terá um submódulo ou você terá um módulo genérico de "Execução" que traduz as ordens?

- **Conciliação (Reconciliation/Risk):** Como o sistema descobre se o saldo real na exchange bate com o que o banco de dados acha que aconteceu? Isso roda em tempo real ou via cron job (ex: a cada 5 minutos)?

