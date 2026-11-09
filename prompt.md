# Prompt usado para gerar a dashboard

> Versão final enviada à IA (Claude), junto com a planilha `dados/base_porsche_limpa_v2.csv`.

```
Anexei uma planilha com 100 vendas de Porsche nos EUA (valores em dólar, USD). As colunas são:
sale_id, sale_date, model, model_year, price_usd, mileage, payment_group, city, state, delivery_group.
Algumas datas (sale_date) estão vazias; ignore-as nos gráficos de tempo e avise isso no rodapé.

Crie uma DASHBOARD em HTML, arquivo único (index.html), com os dados embutidos no próprio arquivo, em português do Brasil.

INDICADORES NO TOPO (respondem ao filtro ativo):
- Total de vendas (quantidade)
- Receita total (US$)
- Ticket médio (US$)
- % de vendas entregues

FILTROS (combináveis): modelo, ano do modelo, estado, cidade e forma de pagamento.

TRÊS PERGUNTAS DE NEGÓCIO, cada uma com um gráfico e uma frase de leitura abaixo:
1. Quais modelos geram mais receita? (barras horizontais, top 10 por receita)
2. Quais estados vendem mais e qual a forma de pagamento predominante em cada um? (barras por estado, empilhadas por forma de pagamento)
3. Qual a proporção de vendas entregues, em andamento e canceladas? (rosca)

VISUAL: elegante e refinado, tema escuro (grafite e preto) com um detalhe em vermelho, tipografia limpa e sem enfeites. Cartões com cantos suaves, bom contraste, legível no celular.

REGRAS: use só os dados da planilha (não invente números); mostre mensagem clara quando o filtro não tiver resultado; sem nomes de clientes.
Ao final, explique em 5 linhas como cada indicador foi calculado.
```

## O que mudou do primeiro prompt para o final
1. **Base:** a primeira versão trazia 9 formas de pagamento e 10 status de entrega. Na revisão, as formas de pagamento parecidas foram agrupadas e os status foram reunidos em 3 grupos, direto na planilha (colunas `payment_group` e `delivery_group`), em vez de pedir à IA para agrupar.
2. **Gráfico 3:** o agrupamento do status deixou de ser descrito no prompt, porque já vem pronto na base.
3. **Pedidos de ajuste depois da primeira versão:** corrigir a cor repetida no gráfico de estados (havia mais formas de pagamento do que cores), singularizar o texto quando o filtro tem só um estado e completar a lista de status no rodapé.
