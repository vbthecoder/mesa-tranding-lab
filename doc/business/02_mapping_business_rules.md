# Mapeando as Regras de Negócio e Estados das Pernas

Para mapearmos as regras de negócios e estados das pernas, vamos as seguintes perguntas que ajudarão nesse processo:

- Gatilho: Qual é o spread mínimo (em % ou valor nominal) que justifica abrir a operação, considerando as taxas de corretagem de entrada e saída?

- Sequenciamento: As pernas serão executadas em paralelo (manda as duas ordens ao mesmo tempo para minimizar risco de preço) ou em série (só mando a Perna B se a Perna A executar)?
   - Nota: No cash-and-carry, se você compra o Spot e o Perpétuo cai antes de você vender, você perde dinheiro. Se manda em paralelo, as duas podem executar parcialmente.

- Tipos de Ordem: Você usará ordens a mercado (Market Orders - execução garantida, mas sofre com slippage) ou ordens limitadas (Limit Orders - preço garantido, mas podem ficar pendentes no livro)?
