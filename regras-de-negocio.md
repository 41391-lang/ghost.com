# Regras de negócio — GhostDM

## 1. Contagem
Uma mensagem conta quando:
- Foi escrita pelo usuário.
- Não está vazia após remover espaços no início e no fim.
- Foi efetivamente adicionada ao histórico.

Não contam:
- Mensagens da Luna.
- Avisos do sistema.
- Mensagens vazias.
- Mensagens de exemplo inseridas automaticamente.

## 2. Plano grátis
- `plan = "free"`.
- Nenhuma mensagem da Luna pode ser gerada como resposta automática.
- O contador geral pode continuar aumentando, mas não deve gerar respostas.
- Ao mudar para Premium, iniciar um novo contador Premium em zero.

## 3. Plano Premium
- `plan = "premium"`.
- Incrementar `premiumMessageCount` a cada mensagem válida do usuário.
- Quando `premiumMessageCount` chegar a 10:
  1. Selecionar uma resposta aleatória da lista de respostas permitidas.
  2. Adicionar exatamente uma mensagem da Luna ao histórico.
  3. Registrar o marco respondido.
  4. Zerar `premiumMessageCount` para iniciar o próximo ciclo.
- Nunca gerar mais de uma resposta para o mesmo ciclo.
- A resposta deve aparecer depois da décima mensagem do usuário.

## 4. Troca de plano
- Ao ativar Premium, zerar `premiumMessageCount`.
- Não converter mensagens enviadas no plano grátis em progresso Premium.
- Ao voltar para o plano grátis, interromper respostas automáticas.
- Se o usuário voltar ao Premium posteriormente, começar um novo ciclo em zero.

## 5. Persistência e consistência
- Atualizar o estado salvo sempre que uma mensagem for enviada, uma resposta for recebida ou o plano mudar.
- Ao recarregar a página, restaurar o estado sem duplicar respostas.
- Se os dados salvos estiverem inválidos, iniciar um estado padrão seguro.

## 6. Pseudocódigo de referência

```js
function sendUserMessage(text) {
  const cleanText = text.trim();
  if (!cleanText) return;

  addMessage({ sender: "user", text: cleanText });
  state.totalUserMessages += 1;

  if (state.plan === "premium") {
    state.premiumMessageCount += 1;

    if (state.premiumMessageCount === 10) {
      addMessage({
        sender: "luna",
        text: pickRandomReply()
      });

      state.premiumMessageCount = 0;
    }
  }

  saveState();
}
```

A implementação pode usar outra arquitetura, desde que preserve exatamente o comportamento descrito.
