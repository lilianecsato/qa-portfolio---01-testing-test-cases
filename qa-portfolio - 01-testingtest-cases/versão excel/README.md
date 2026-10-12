Teste de Login – SauceDemo (QA Manual)

Projeto prático de **teste funcional manual** da tela de login do [SauceDemo](https://www.saucedemo.com), um site de e-commerce criado para treino de QA. 

Objetivo:
Validar o fluxo de login com cenários positivos, negativos e de usabilidade, documentar os resultados como em um time de qualidade e registrar os defeitos encontrados.

O que foi testado
10 cenários de login: login válido, senha incorreta, usuário inexistente, campos vazios, senha vazia, usuário bloqueado, diferença entre maiúsculas e minúsculas, senha mascarada e uso em modo celular.

| Resultado | Quantidade |
|-----------|-----------|
| Passou    | 10 |
| Falhou    | 0 |

1 defeito encontrado: `BUG-001` – a mesma imagem aparece em todos os produtos para o usuário `problem_user`.

Conteúdo
  - `teste-login-saucedemo.xlsx`
  - Execução - Login: cenários, passos, resultado esperado x obtido, status e evidência.
  - Bugs: relatório do defeito com passos para reproduzir, severidade e prioridade.
  - Evidências: prints de cada cenário.

Como testei
- Navegador: Google Chrome (versão 154) e modo celular do DevTools (400 x 498)
- Técnicas: cenários positivos e negativos, análise de mensagens de erro, teste de usabilidade
- Documentação: planilha com casos de teste e relatório de bug

O que aprendi
- Escrever cenários claros, com resultado esperado.
- Em cenário negativo, o teste passa quando o sistema rejeita corretamente.
- Registrar bug com título objetivo, passos, esperado x atual, severidade e prioridade.
- Organizar evidências por cenário.


Autora
Liliane Costa – QA em formação · [LinkedIn](https://www.linkedin.com/in/lilianecsato) · [GitHub](https://github.com/lilianecsato/qa-portfolio)
