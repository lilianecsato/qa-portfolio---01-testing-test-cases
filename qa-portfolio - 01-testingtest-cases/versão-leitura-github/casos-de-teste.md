# Casos de teste – Login (SauceDemo)

> Versão para leitura direta no GitHub. A planilha completa está em [`teste-login-saucedemo.xlsx`](teste-login-saucedemo.xlsx).

**Site:** https://www.saucedemo.com  
**Navegador:** Google Chrome, versão 154.0.8037.57 (64 bits)  
**Data:** 11/10/2026  
**Executado por:** Liliane Costa

## Resumo

| Total | Passou | Falhou | Bloqueado | Bugs encontrados |
|---|---|---|---|---|
| 10 | 10 | 0 | 0 | 1 |

## Execução dos cenários

| # | Cenário | Tipo | Usuário / Senha | Passos | Resultado esperado | Resultado obtido | Status | Observação |
|---|---|---|---|---|---|---|---|---|
| 1 | Login com usuário e senha válidos | Positivo | `standard_user`<br>`secret_sauce` | 1) Abrir o site<br>2) Digitar usuário e senha<br>3) Clicar em Login | Abre a lista de produtos | Logou e abriu a lista de produtos (inventory.html), com a imagem correta em cada produto. | ✅ Passou | — |
| 2 | Login com outro usuário válido | Positivo | `problem_user`<br>`secret_sauce` | 1) Abrir o site<br>2) Digitar usuário e senha<br>3) Clicar em Login | Abre a lista de produtos | Logou e abriu a lista de produtos, mas todos os produtos mostram a mesma imagem (um cachorro com uma bola). | ✅ Passou | Defeito na lista de produtos: a mesma imagem aparece em todos os produtos. Registrado como BUG-001. Este usuário de treino tem defeitos de propósito. |
| 3 | Senha incorreta | Negativo | `standard_user`<br>`senha_errada` | 1) Abrir o site<br>2) Digitar usuário e a senha errada<br>3) Clicar em Login | Mensagem de erro; não entra | Apareceu "Epic sadface: Username and password do not match any user in this service" e o usuário não entrou. | ✅ Passou | Mesma mensagem para usuário ou senha errados: boa prática de segurança, pois não revela qual dado está errado. Mensagem em inglês é padrão do site de treino; não é bug. |
| 4 | Usuário inexistente | Negativo | `usuario_falso`<br>`secret_sauce` | 1) Abrir o site<br>2) Digitar usuário e senha<br>3) Clicar em Login | Mensagem de erro; não entra | Apareceu "Epic sadface: Username and password do not match any user in this service" e o usuário não entrou. | ✅ Passou | Mesma mensagem do cenário 3: o site não revela se o usuário ou a senha está errado (boa prática de segurança). |
| 5 | Os dois campos vazios | Negativo | `(vazio)`<br>`(vazio)` | 1) Abrir o site<br>2) Não digitar nada<br>3) Clicar em Login | Aviso de campo obrigatório | Apareceu "Epic sadface: Username is required"; os campos Username e Password ficaram em vermelho. | ✅ Passou | — |
| 6 | Só o usuário preenchido | Negativo | `standard_user`<br>`(vazio)` | 1) Abrir o site<br>2) Digitar só o usuário<br>3) Clicar em Login | Aviso de senha obrigatória | Apareceu "Epic sadface: Password is required"; só o campo Password ficou em vermelho. | ✅ Passou | — |
| 7 | Usuário bloqueado | Negativo | `locked_out_user`<br>`secret_sauce` | 1) Abrir o site<br>2) Digitar usuário e senha<br>3) Clicar em Login | Mensagem informando que o usuário está bloqueado; não entra | Apareceu "Epic sadface: Sorry, this user has been locked out." e o usuário não entrou. | ✅ Passou | — |
| 8 | Usuário com maiúsculas trocadas | Negativo | `Standard_User`<br>`secret_sauce` | 1) Abrir o site<br>2) Digitar usuário com a inicial maiúscula<br>3) Clicar em Login | Não entra (anote como o site tratou) | Apareceu "Epic sadface: Username and password do not match any user in this service". O site diferencia maiúsculas de minúsculas. | ✅ Passou | Conclusão: o site diferencia maiúsculas de minúsculas no nome de usuário. |
| 9 | Senha aparece mascarada | Não funcional (segurança) | `standard_user`<br>`secret_sauce` | 1) Abrir o site<br>2) Digitar a senha e olhar o campo | Caracteres ocultos (bolinhas) | Os caracteres da senha aparecem como bolinhas. | ✅ Passou | — |
| 10 | Login pelo celular | Não funcional (usabilidade) | `standard_user`<br>`secret_sauce` | 1) F12<br>2) Ctrl+Shift+M (modo celular)<br>3) Fazer login | Campos e botão visíveis e clicáveis; entra normalmente | Logou e a lista de produtos abriu no modo celular (400 x 498): menu, carrinho, filtro e produtos visíveis. | ✅ Passou | Layout se adapta bem ao celular: o filtro mostra só o ícone. |

## Relatório de bug

### BUG-001 – Lista de produtos: a mesma imagem de cachorro aparece em todos os produtos para o problem_user

| Campo | Detalhe |
|---|---|
| Cenário | #2 |
| Passos para reproduzir | 1) Abrir https://www.saucedemo.com<br>2) Digitar problem_user e secret_sauce<br>3) Clicar em Login<br>4) Olhar a lista de produtos |
| Resultado esperado | Cada produto mostra a sua própria imagem (mochila, luz de bicicleta, camiseta, jaqueta...), como acontece com o standard_user |
| Resultado atual | Todos os produtos mostram a mesma foto de um cachorro com uma bola de tênis; nome, descrição e preço estão corretos |
| Severidade | Média |
| Prioridade | Média |
| Evidência | [`cenario-02-problem-user.png`](evidencias/cenario-02-problem-user.png) (atual) e [`cenario-01-login-valido.png`](evidencias/cenario-01-login-valido.png) (esperado) |

![BUG-001](evidencias/cenario-02-problem-user.png)

## Evidências

**Cenário 1 – Login com usuário e senha válidos**

![cenario-01-login-valido.png](evidencias/cenario-01-login-valido.png)

**Cenário 2 – Login com outro usuário válido**

![cenario-02-problem-user.png](evidencias/cenario-02-problem-user.png)

**Cenário 3 – Senha incorreta**

![cenario-03-senha-incorreta.png](evidencias/cenario-03-senha-incorreta.png)

**Cenário 4 – Usuário inexistente**

![cenario-04-usuario-inexistente.png](evidencias/cenario-04-usuario-inexistente.png)

**Cenário 5 – Os dois campos vazios**

![cenario-05-campos-vazios.png](evidencias/cenario-05-campos-vazios.png)

**Cenário 6 – Só o usuário preenchido**

![cenario-06-senha-vazia.png](evidencias/cenario-06-senha-vazia.png)

**Cenário 7 – Usuário bloqueado**

![cenario-07-usuario-bloqueado.png](evidencias/cenario-07-usuario-bloqueado.png)

**Cenário 8 – Usuário com maiúsculas trocadas**

![cenario-08-usuario-maiusculas.png](evidencias/cenario-08-usuario-maiusculas.png)

**Cenário 9 – Senha aparece mascarada**

![cenario-09-senha-mascarada.png](evidencias/cenario-09-senha-mascarada.png)

**Cenário 10 – Login pelo celular**

![cenario-10-modo-celular.png](evidencias/cenario-10-modo-celular.png)
