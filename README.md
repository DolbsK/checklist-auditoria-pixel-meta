# Checklist de auditoria de pixel e eventos da Meta

Este é o roteiro que eu sigo antes de recomendar aumento de verba, troca de criativo ou mudança de público numa conta de Meta Ads.

A regra é simples: **o técnico vem primeiro.** Nenhuma otimização de anúncio conserta rastreamento quebrado. Se o pixel mede errado, a campanha aprende com o dado errado e cada real a mais só acelera a conclusão errada.

## Quando usar

- Na entrada de um cliente novo, antes da primeira campanha.
- Quando o número de conversões da Meta não bate com as vendas do cliente.
- Quando a campanha gasta, mas o resultado some de uma semana para outra.
- Antes de qualquer pedido de aumento de verba.

## Antes de começar

Confira estes acessos. Sem eles a auditoria fica pela metade.

- [ ] Gerenciador de Eventos da conta, com permissão de leitura do pixel.
- [ ] Gerenciador de Anúncios, para ver o evento de otimização de cada conjunto.
- [ ] Google Tag Manager ou painel do site, para ver onde o pixel está instalado.
- [ ] CRM ou planilha de vendas do cliente, para comparar com o que a Meta registra.

## 1. Pixel base

- [ ] O pixel está instalado uma única vez. Instalação dupla (plugin do site mais GTM, por exemplo) conta cada evento duas vezes.
- [ ] O evento PageView dispara em todas as páginas que recebem tráfego pago.
- [ ] O domínio do site está verificado no Gerenciador de Negócios.
- [ ] O pixel usado nos anúncios é o mesmo que está no site. Conta antiga costuma ter mais de um pixel criado.

## 2. Eventos do funil

- [ ] Cada etapa do funil tem um evento: visita, contato, cadastro e compra.
- [ ] O evento dispara no momento certo. Lead dispara no envio confirmado do formulário, não no clique do botão nem na abertura da página.
- [ ] O evento de Compra existe e leva valor e moeda (`value` e `currency`).
- [ ] O volume de cada evento faz sentido quando comparado com o CRM. Lead em dobro costuma ser disparo duplicado. Lead zerado com venda acontecendo é evento quebrado.

## 3. Evento que a campanha otimiza

Este é o item que mais encontro errado, e o mais caro.

- [ ] Abra cada conjunto de anúncios e anote o evento de otimização.
- [ ] Confira no Gerenciador de Eventos se esse evento disparou nos últimos 7 dias. Campanha otimizando para evento que não dispara gasta sem ter com o que aprender.
- [ ] Confira o volume. A Meta usa como referência cerca de 50 eventos por conjunto em 7 dias para sair da fase de aprendizado. Abaixo disso, otimize para um evento mais frequente do funil.
- [ ] Confira o tempo entre o clique e a venda. A janela padrão é de 7 dias após o clique. Venda que fecha depois disso não volta para a campanha.

## 4. API de Conversões

- [ ] Os eventos importantes chegam também pelo servidor, não só pelo navegador. Bloqueador de anúncio e restrição de privacidade derrubam parte dos eventos do navegador.
- [ ] Evento enviado pelo navegador e pelo servidor leva o mesmo `event_name` e o mesmo `event_id`. Sem isso, a Meta conta a mesma conversão duas vezes.
- [ ] A Qualidade de Correspondência do Evento, no Gerenciador de Eventos, está boa. Para subir a nota, envie e-mail e telefone criptografados e os identificadores de clique `fbc` e `fbp`.
- [ ] A venda é enviada sozinha, por integração, assim que acontece. Evento enviado à mão chega em lote e atrasado e não ensina a campanha.

## 5. Conversão pelo WhatsApp

Em campanha de clique para WhatsApp, a Meta mede a conversa iniciada. A venda acontece fora dela.

- [ ] Existe um registro de quais conversas viraram venda, no CRM ou numa planilha.
- [ ] A venda confirmada volta para a Meta pela API de Conversões, para a campanha aprender com quem compra e não só com quem chama.
- [ ] O custo por conversa é comparado com o custo por venda. Conversa barata que não vende é volume sem qualidade.

## 6. Teste final

- [ ] Faça uma conversão de teste com a ferramenta Eventos de Teste do Gerenciador de Eventos.
- [ ] Confira se o evento aparece uma vez só, com os parâmetros certos.
- [ ] Registre a data da correção. A comparação de antes e depois começa nela.

## Modelo de entrega

Eu entrego o resultado da auditoria ao cliente nesta tabela, antes de qualquer proposta de verba.

| Item | Situação | Impacto | Ação | Status |
|---|---|---|---|---|
| Evento de otimização | Conjunto otimiza para Lead, que não dispara há 30 dias | Campanha sem sinal para aprender | Corrigir o disparo e otimizar para Contato até ter volume | Feito |
| Evento de Compra | Não existe no pixel | Não dá para medir custo por venda | Criar o evento com valor e moeda | Não feito |

## Casos reais (clientes anonimizados)

**Assinatura de climatização.** A campanha otimizava para um evento que nunca disparava. Eu corrigi o pixel antes de recomendar mais verba. Depois disso, as vendas de assinatura confirmadas passaram a ir para a Meta pela API de Conversões, e a campanha passou a aprender com venda real.

**Clínica de estética.** A conta gerava conversas a bom custo, mas o evento de Compra não existia no pixel. Sem ele não havia como saber quanto custava cada paciente. Eu recomendei a criação do evento antes de qualquer aumento de verba.

## O que este checklist não cobre

- Criativo, público e estrutura de campanha. Isso vem depois, com o rastreamento confirmado.
- Google Ads e GA4. Eu uso um roteiro separado para eles.

---

Kallebe Alves · Gestor de Tráfego Pago e Automação de Marketing · [portfolio.vyzar.com.br](https://portfolio.vyzar.com.br)
