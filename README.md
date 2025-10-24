# ajax-comparacao
# Comparação de Requisições Assíncronas em JavaScript: XHR, fetch, Promises e async/await

Este projeto tem como objetivo comparar a evolução das técnicas de requisições assíncronas (AJAX) em JavaScript, analisando a sintaxe, usabilidade e desempenho de `XmlHttpRequest` (XHR), `fetch`, `Promises` e `async/await`.

## 1. XmlHttpRequest (XHR)

**Descrição:**
O mecanismo original e baseado em eventos para requisições HTTP assíncronas no navegador. É a base histórica do AJAX.

**Características:**
* **Vantagens:** Ampla compatibilidade com navegadores legados e controle granular (abortar, monitorar progresso).
* **Desvantagens:** Sintaxe complexa, verbosa e propensa ao problema de "Callback Hell" em cadeias de operações.

## 2. Promises (Promessas)

**Descrição:**
Um objeto que representa o resultado (sucesso ou falha) eventual de uma operação assíncrona. Promises são um padrão de controle de fluxo, não um método de requisição.

**Características:**
* **Vantagens:** Resolve o "Callback Hell", oferecendo encadeamento limpo (`.then()`) e tratamento de erros unificado (`.catch()`). É a base para `fetch` e `async/await`.
* **Desvantagens:** O encadeamento ainda pode exigir aninhamento e o conceito pode ser abstrato para iniciantes.

## 3. fetch API

**Descrição:**
A API moderna e baseada em Promises para requisições de rede.

**Características:**
* **Vantagens:** Sintaxe muito mais limpa e moderna que o XHR. Integração nativa com o padrão Promises.
* **Desvantagens:** A Promise só é rejeitada em falhas de rede; erros HTTP (como 404 ou 500) devem ser tratados manualmente verificando `response.ok`. Não possui suporte nativo simples para recursos avançados como progresso.

## 4. async/await

**Descrição:**
Uma sintaxe que permite escrever código assíncrono que se comporta e parece síncrono, tornando a lógica mais legível. É construído sobre Promises.

**Características:**
* **Vantagens:** Superior em legibilidade e manutenção. Permite o uso de `try...catch` para tratamento de erros, simplificando o fluxo de controle.
* **Desvantagens:** Só pode ser usado dentro de uma função declarada com a palavra-chave `async`.

---

## Implementação e Comparação de Desempenho

Os arquivos `ajax3-fetch.html`, `ajax3-promises.html` (XHR com Promise Wrapper) e `ajax3-async-await.html` replicam a funcionalidade básica de requisição (similar ao antigo `ajax3.html`) utilizando as técnicas modernas.

### 5. Comparação de Desempenho e Facilidade de Uso

| Método | Facilidade de Uso (1 a 5 - 5 sendo mais fácil) | Desempenho (Tempo Médio de Resposta) | Vantagens em Cenários Complexos |
| :--- | :---: | :---: | :--- |
| **XHR (Legacy)** | 1 | \1,7 ms| Controle de requisição no nível mais baixo (abortar, progresso). |,
| **fetch + Promises** | 3 | \3,7 ms | Sintaxe limpa para requisições sequenciais (`.then().then()`). |
| **fetch + async/await** | 5 | \5,6 ms | Melhor fluxo de controle, usando lógica `try/catch` síncrona. |

**Conclusão sobre Desempenho:**
Em ambientes modernos, a diferença de desempenho entre as APIs de requisição (`fetch` vs. XHR) é geralmente mínima, pois o fator limitante costuma ser a latência da rede. A escolha entre `Promises` e `async/await` deve se basear principalmente na **legibilidade e manutenção** do código, sendo `async/await` o padrão preferido atualmente.
