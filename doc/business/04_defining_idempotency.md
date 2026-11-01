# Definindo Idempotência e Conciliação

Em sistemas financeiros a rede é um inimigo. Um timeout em uma requisição pode não significar que a ordem falhou. Ela pode ter sido executada, mas a. resposta pode ter se perdido

Para garantir consistência, responda:

- **Chave de Idempotência:** Como você garante que, ao re-enviar uma ordem após um timeout, a exchange não execute duas vezes? Você consegue enviar um clientOrderId customizado gerado pelo seu sistema para a exchange?

- **Tratamento de Sinais Duplicados:** Se o módulo de Oportunidades enviar o mesmo sinal duas vezes em um intervalo de milissegundos, como o OMS garante que só criará uma intenção de ordem?

- **Auditoria de Conciliação:** Se a exchange executar uma ordem parcialmente (ex: pediu 1 BTC, executou 0.4 BTC e cancelou o resto), como o módulo de conciliação atualiza o estado e avisa a Saga para ajustar a outra perna?
