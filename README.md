# Dashboard de Vendas Porsche

Dashboard interativa (HTML de arquivo único) com **100 vendas de exemplo de Porsche nos EUA**, feita como projeto prático da Aceleração Santander (DIO): *AI Reports com Excel, GPT Agents e Claude Code*.

**Endereço da dashboard publicada:** https://SEU-USUARIO.github.io/dashboard-porsche-sales/ *(trocar pelo endereço real depois de publicar)*

## Perguntas de negócio escolhidas e por quê
1. **Quais modelos geram mais receita?** A receita mostra onde está o dinheiro; o volume de vendas sozinho esconde modelos caros que vendem pouco.
2. **Quais estados vendem mais e qual é a forma de pagamento predominante em cada um?** Ajuda a direcionar campanhas e condições de financiamento por região.
3. **Qual a proporção de vendas entregues, em andamento e canceladas?** Mostra gargalos de entrega e receita perdida com cancelamentos.

## Como usar
Abra `index.html` no navegador (ou o endereço acima). Use os filtros de modelo, ano, estado, cidade e pagamento; os indicadores do topo, os gráficos e as frases de leitura se atualizam juntos. O botão **Limpar filtros** volta ao total.

## Tratamento da base antes de ir para a IA
Partimos da planilha já sanitizada na aula anterior (colunas "sujas" e colunas "tratadas") e fizemos uma **segunda rodada de revisão**:
- Ficaram **só as colunas tratadas** (modelo, ano, preço, quilometragem, pagamento, cidade, estado, entrega e data). **Nomes de clientes e de vendedores foram retirados**, porque os dados ficam embutidos no HTML.
- Preço, ano e quilometragem foram convertidos em **número** e colados como valores.
- **Formas de pagamento agrupadas:** *Wire Transfer*, *Bank Transfer* e *ACH Payment* viraram "Transferência bancária" (9 formas → 7).
- **Status de entrega agrupados:** *Delivered* → Entregue; *Cancelled* → Cancelada; os outros 8 (Pending, In Transit, Shipped, Awaiting Delivery, Awaiting Pickup, Pending Approval, Pending Review, Awaiting Review) → Em andamento.
- **Datas:** 24 vinham inválidas. **3** estavam em formato AAAA/DD/MM (por exemplo `2024/15/07`, que só pode ser 15/07/2024) e foram recuperadas. As outras **21 são impossíveis** (como 30 de fevereiro ou dia 32) e ficaram em branco, sem inventar valor. Por isso a dashboard não tem gráfico ao longo do tempo.
- A coluna `date_note` da base registra o que foi feito em cada data.

Arquivo usado pela dashboard: `dados/base_porsche_limpa_v2.csv`.

## Ferramenta de IA usada
Foi usado o **Claude** (assistente de IA da Anthropic, pelo aplicativo Claude Code), que gerou o HTML a partir do prompt abaixo; o conteúdo foi revisado e testado (filtros, filtro sem resultado e leitura no celular). Não foi usado o ChatGPT com Canvas nem um agente com skill.

## Prompt e o que mudou
O prompt completo e a lista de mudanças entre a primeira versão e a final estão em [`prompt.md`](prompt.md). Resumo do prompt: dashboard em HTML único, em português, com 4 indicadores no topo, 5 filtros combináveis, 3 gráficos (um por pergunta) com frase de leitura, visual escuro com detalhe vermelho, uso apenas dos dados da planilha.

## Observações e limites
- Os dados são de **exemplo** (fictícios) e ficam **públicos dentro do HTML**: não use este método com dados sensíveis.
- Só há 100 vendas; por estado ou cidade os números são pequenos e devem ser lidos como ilustração.

## Arquivos
- `index.html` — a dashboard.
- `dados/base_porsche_limpa_v2.csv` — base tratada usada na dashboard.
- `prompt.md` — prompt e mudanças.
