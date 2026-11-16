# Plano de desenvolvimento e testes — GhostDM

## Etapa 1 — Estrutura
- Criar a estrutura inicial do projeto.
- Definir a tecnologia adequada ao ambiente já existente.
- Criar componentes separados para cabeçalho, conversa, mensagens, campo de envio e assinatura.
- Não substituir arquivos existentes sem antes entender o projeto.

## Etapa 2 — Conversa
- Implementar envio de mensagens.
- Diferenciar visualmente mensagens do usuário, da Luna e do sistema.
- Implementar rolagem automática para a mensagem mais recente.
- Bloquear envio de texto vazio.

## Etapa 3 — Planos
- Implementar plano grátis sem respostas.
- Implementar ativação simulada do Premium.
- Implementar contador de dez mensagens.
- Garantir uma resposta por ciclo, sem duplicações.

## Etapa 4 — Persistência
- Salvar histórico, plano e contadores localmente.
- Restaurar os dados ao recarregar.
- Implementar limpeza com confirmação.

## Etapa 5 — Acabamento
- Ajustar visual desktop e mobile.
- Revisar textos e estados vazios.
- Verificar acessibilidade básica: contraste, foco e rótulos dos controles.
- Remover botões sem função.

## Testes obrigatórios

| Teste | Ação | Resultado esperado |
|---|---|---|
| 1 | Enviar mensagem no plano grátis | Mensagem aparece; Luna não responde |
| 2 | Enviar 20 mensagens no plano grátis | Luna continua sem responder |
| 3 | Ativar Premium | Contador começa em 0/10 |
| 4 | Enviar 9 mensagens Premium | Nenhuma resposta; contador 9/10 |
| 5 | Enviar a 10ª mensagem Premium | Luna envia exatamente uma resposta |
| 6 | Enviar mais 10 mensagens Premium | Luna envia exatamente mais uma resposta |
| 7 | Atualizar a página | Histórico, plano e contador permanecem |
| 8 | Enviar mensagem vazia | Nada é enviado e contador não muda |
| 9 | Ativar Premium após usar o plano grátis | Mensagens antigas não contam |
| 10 | Limpar conversa | Histórico e contadores são reiniciados |

## Critério final
O projeto só está concluído quando todos os testes acima funcionarem e a experiência principal puder ser demonstrada sem depender de serviços externos.
