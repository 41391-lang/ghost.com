# Funcionalidades — GhostDM

## 1. Tela inicial
- Exibir o nome GhostDM e uma frase curta de apresentação.
- Mostrar um botão para abrir a conversa.
- Mostrar o plano atual: Grátis ou Premium.
- Mostrar um botão para conhecer/ativar o Premium.

## 2. Tela de conversa
A tela deve conter:
- Cabeçalho com avatar fictício, nome "Luna" e status.
- Área de histórico de mensagens.
- Campo de texto.
- Botão Enviar.
- Indicador do plano atual.
- Contador de mensagens enviadas e progresso até a próxima resposta Premium.

## 3. Envio de mensagens
- O usuário pode enviar mensagens de texto.
- Mensagens vazias ou compostas apenas por espaços não podem ser enviadas.
- Ao enviar, a mensagem aparece imediatamente no lado do usuário.
- Cada mensagem válida enviada pelo usuário incrementa o contador em 1.
- Mensagens automáticas do sistema e respostas da Luna não incrementam esse contador.

## 4. Plano grátis
- O usuário pode enviar mensagens ilimitadas.
- Luna nunca responde.
- Exibir pequenas pistas de humor, sem fingir que houve uma resposta.
- Exemplo de aviso: "Luna recebeu sua mensagem. O retorno não faz parte do plano grátis."

## 5. Plano Premium
- O usuário pode enviar mensagens ilimitadas.
- A cada 10 mensagens válidas enviadas pelo usuário, Luna envia uma única resposta.
- Depois da resposta, o progresso recomeça para o próximo grupo de dez mensagens.
- Exibir progresso como "7/10 mensagens para a próxima resposta".
- Não enviar resposta retroativa ao ativar o Premium. A contagem Premium começa no momento da ativação.

## 6. Assinatura simulada
- Criar uma tela ou modal explicando o Premium.
- Mostrar preço demonstrativo e lista de benefícios.
- Botão "Assinar Premium" ativa o plano localmente, sem pagamento.
- Incluir aviso: "Demonstração escolar. Nenhuma cobrança será realizada."
- Permitir voltar ao plano grátis por um controle de demonstração, se isso ajudar na apresentação.

## 7. Persistência
Salvar no armazenamento local do navegador:
- Histórico da conversa.
- Plano selecionado.
- Contador de mensagens Premium desde a última resposta.
- Total de mensagens válidas enviadas.
- Identificador ou registro dos marcos de dez mensagens já respondidos.

## 8. Reiniciar conversa
- Disponibilizar uma opção para limpar a conversa e reiniciar os contadores.
- Pedir confirmação antes de apagar o histórico.
