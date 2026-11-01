# Levantamento de Requisitos da Saga e Compensação

**Temos uma necessidade legítma da saga**: Se a perna A executar mas a perna B falhar (ou rejeitar por falta de margem, ou sofrer timeout), estaremos expostos ao risco de mercado.

A Resiliência do produto é fundamental em situações como essas, e para definirmos com mais clareza, vamos responder as seguintes perguntas:

- O que constitui uma falha na Perna B? É um erro 500 da API? É a ordem ficar aberta por mais de 2 segundos sem executar?

- Qual é a ação de compensação? Se a Perna A (Compra Spot) executou e a Perna B (Venda Perpétuo) falhou, o que a Saga faz? Ela vende o Spot imediatamente para zerar o risco (assumindo o prejuízo da taxa), ou ela tenta re-enviar a Perna B N vezes?