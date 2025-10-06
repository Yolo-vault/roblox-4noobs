# Fundamentos de Lua e Noções Básicas de Script

## Sobre a Linguagem (Lua x Luau, uso em Roblox)

### O que é Lua?
Lua é uma linguagem de programação criada no Brasil, conhecida por ser leve, rápida e fácil de aprender. Ela é utilizada em diversos jogos e softwares pelo mundo, principalmente para scripts em tempo real, automação e customização de sistemas.

### O que é Luau?
Luau (lê-se “lu-au”) é uma versão aprimorada da linguagem Lua, desenvolvida especialmente para o Roblox Studio. Ela traz recursos adicionais, mais segurança e melhor desempenho para scripts dentro dos jogos Roblox.

> Principais diferenças:
 - Luau é compatível com Lua 5.1, mas pode ter comandos e recursos próprios do Roblox.
 - Luau oferece checagem de tipos opcional (type checking), o que ajuda a encontrar erros durante o desenvolvimento.
 - Algumas bibliotecas padrão do Lua tradicional podem não funcionar em Luau.

> Por que Roblox usa Lua/Luau?
 - Rápida e eficiente para scripts de jogos
 - Fácil para iniciantes entenderem lógica de programação
 - Permite criar sistemas avançados e interativos dentro dos games Roblox
 - Grande comunidade de suporte e muitos exemplos prontos
Em Roblox, você pode programar scripts para criar mecânicas de jogo, sistemas de interface, controles de personagem, inteligência artificial, etc.

## Comentários e Boas Práticas de Documentação
### Hello World Lua/Luau no Roblox
```lua
  -- Isso é um comentário. Comentários não afetam o código.
  print("Olá, Roblox!") -- Imprime uma mensagem no console do Roblox Studio
```

---

## Variáveis

### O que são variáveis?
Variáveis são “caixinhas” que guardam informações (dados) que queremos usar depois. Elas facilitam a organização e o reaproveitamento de valores no código. Toda linguagem de programação usa variáveis!

> Como criar e usar variáveis em Lua/Luau:
```luau
  -- Criando uma variável chamada "nome"
  local nome = "Roblox"

  -- Criando uma variável com número
  local idade = 10

  -- Imprimindo as variáveis no console
  print(nome)
  print(idade)
```

> Dicas importantes:
 - O nome da variável não pode começar com número e não pode ter espaço (use underline _ se quiser separar).
 - É possível mudar o valor de uma variável ao longo do script.
   - Exemplo: 
      ```lua
        local pontos = 0
        pontos = pontos + 5    -- Agora, pontos vale 5
        pontos = pontos * 2    -- Agora, pontos vale 10
      ```

---

## Operadores

### O que são operadores?
Operadores são símbolos que executam operações matemáticas, comparações ou operações lógicas entre valores. São essenciais para criar condições, cálculos e tomar decisões no código.

### Aritméticos
Usados para operações matemáticas.
```luau
  local a = 10
  local b = 3

  print(a + b)  -- 13 (adição)
  print(a - b)  -- 7  (subtração)
  print(a * b)  -- 30 (multiplicação)
  print(a / b)  -- 3.333... (divisão)
  print(a % b)  -- 1  (resto da divisão - módulo)
  print(a ^ b)  -- 1000 (exponenciação - 10³)
```

### Comparação
Retornam `true` ou `false`.
```luau
  local x = 5
  local y = 10

  print(x == y)  -- false (igual a)
  print(x ~= y)  -- true  (diferente de)
  print(x < y)   -- true  (menor que)
  print(x > y)   -- false (maior que)
  print(x <= y)  -- true  (menor ou igual)
  print(x >= y)  -- false (maior ou igual)
```

### Lógicos
Combinam condições booleanas.
- `and` (E) Retorna `true` apenas se ambas as condições forem verdadeiras.
  ```luau
    local idade = 18
    local temCarteira = true

    if idade >= 18 and temCarteira then
      print("Pode dirigir!")
    end
  ```
- `or` (OU) Retorna `true` se pelo menos uma das condições for verdadeira.
  ```luau
    local nivel = 25
    local vip = true

    if nivel >= 30 or vip then
      print("Acesso liberado!")
    end
  ```
- `not` (NÃO) Inverte o valor booleano.
  ```luau
    local online = false

    if not online then
      print("Jogador está offline")
    end
  ```

### Operador de Concatenação
`..` junta strings.
```luau
  local nome = "João"
  local sobrenome = "Silva"
  local completo = nome .. " " .. sobrenome
  print(completo)  -- "João Silva"
```

### Operador de Tamanho
`#` retorna o tamanho de strings ou tabelas.
```luau
  local texto = "Roblox"
  local lista = {1, 2, 3, 4}

  print(#texto)  -- 6
  print(#lista)  -- 4
```

### Precedência de operadores
A ordem de execução (do maior para menor):

- 1. `^` (exponenciação)
- 2. `not`, `-` (negação unária)
- 3. `*`, `/`, `%`
- 4. `+`, `-`
- 5. `<`, `<=`, `>`, `>=`, `==`, `~=`
- 6. `and`
- 7. `or`

> Exemplo:
```luau
local resultado = 2 + 3 * 4  -- resultado = 14 (não 20!)
local resultado2 = (2 + 3) * 4  -- resultado2 = 20
```

> Dicas importantes:
- `==` compara valores, `=` atribui valores
- Em Lua, `0` e `""` são considerados `true` (diferente de outras linguagens)
- Operadores lógicos fazem "short-circuit": `and` para no primeiro `false`, `or` para no primeiro `true`

---

## Condicionais

### O que são condicionais?
Condicionais permitem que o código tome decisões baseadas em certas condições. É como fazer perguntas ao computador: "Se isso for verdade, faça aquilo. Senão, faça outra coisa."

> Estrutura básica do if (se)
```luau
  if condição then
    -- código que executa se a condição for verdadeira
  end 
```
**__Exemplo Simples__**:
```luau
  local idade = 16

  if idade >= 18 then
    print("Maior de idade!")
  end
```

> else (senão)
```luau
  local pontos = 85

  if pontos >= 100 then
    print("Parabéns! Você ganhou!")
  else
    print("Continue tentando!")
  end
```

> elseif (senão se, digamos que e um else porem voce pode passar uma condicao)
```luau
  local nota = 7.5

  if nota >= 9 then
    print("Excelente!")
  elseif nota >= 7 then
    print("Bom trabalho!")
  elseif nota >= 5 then
    print("Aprovado!")
  else
    print("Precisa estudar mais!")
  end
```

---

## Escopo Léxico

### O que é escopo?
Escopo é a área do código onde uma variável ou função é visível e pode ser utilizada. Saber isso é super importante para evitar que variáveis interfiram no funcionamento do seu script sem querer!

> Tipos principais de escopo em Lua/Luau
 - Escopo global: variável pode ser acessada de qualquer parte do código (evite)
 - Escopo local: variável só existe dentro do bloco onde foi criada (recomendado)
 - Exemplo simples:
    ```luau
      -- Variável global (evite)
      nome = "Roblox"

      -- Variável local (recomendado)
      local idade = 10
    ```
  - Use sempre local ao declarar variáveis e funções!

> Exemplo escopo:
```luau
  local pontos = 0

  function adicionarPontos()
    local pontos = 10   -- variável pontos só existe dentro da função
    print("Pontos dentro da função:", pontos)
  end

  adicionarPontos()
  print("Pontos fora da função:", pontos)
```

---

## Strings

### O que são strings?
Strings são sequências de caracteres (texto) em programação. Em Lua/Luau, sempre colocamos texto entre aspas para criar uma string.

> Como criar strings
```luau
  local nome = "João"
  local sobrenome = 'Silva' -- Aspas simples também funcionam
  local frase = "Bem-vindo ao Roblox!"
```

### Concatenação (juntar strings)
Use `..` (dois pontos) para juntar strings:
```luau
  local nome = "Maria"
  local sobrenome = "Santos"
  local nomeCompleto = nome .. " " .. sobrenome
  print(nomeCompleto) -- "Maria Santos"

  -- Juntando string com número
  local pontos = 150
  local mensagem = "Você tem " .. pontos .. " pontos!"
  print(mensagem) -- "Você tem 150 pontos!"
```

### Principais funções para manipular strings
- `string.len()` - Tamanho da string
  ```luau
    local texto = "Roblox"
    print(string.len(texto)) -- 6
    -- ou simpemente: #texto
    print(#texto) -- 6
  ```
- `string.upper()` - Deixar maiúsculo
  ```luau
    local nome = "joão"
    print(string.upper(nome)) -- "JOÃO"
  ```
- `string.lower()` - Deixar minúsculo
  ```luau
    local nome = "MARIA"
    print(string.lower(nome)) -- "maria"
  ```
- `string.sub()` - Extrair parte da string
  ```luau
    local frase = "Aprendendo Lua"
    print(string.sub(frase, 1, 10)) -- "Aprendendo"
    print(string.sub(frase, 12))    -- "Lua"
  ```
- `string.find()` - Encontrar texto dentro da string
  ```luau
    local frase = "Eu amo programar"
    local posicao = string.find(frase, "amo")
    print(posicao) -- 4 (posição onde "amo" começa)
  ```
- `string.gsub()` - Substituir texto
  ```luau
    local frase = "Luau é difícil"
    local novaFrase = string.gsub(frase, "difícil", "fácil")
    print(novaFrase) -- "Luau é fácil"
  ```
- Formatação de strings com `string.format()`
  ```luau
    local nome = "Pedro"
    local idade = 15
    local pontos = 1250

    local mensagem = string.format("Olá %s! Você tem %d anos e %d pontos.", nome, idade, pontos)
    print(mensagem) -- "Olá Pedro! Você tem 15 anos e 1250 pontos."
  ```

> Caracteres especiais
```luau
-- Quebra de linha
local texto = "Primeira linha\nSegunda linha"

-- Aspas dentro de string
local fala = "Ele disse: \"Oi!\""
local fala2 = 'Ele disse: "Oi!"'  -- Mais fácil com aspas simples
```

> Dicas importantes:
- Strings são imutáveis (não mudam). Operações como `string.upper()` retornam uma nova string
- Use `#` para obter o tamanho da string (mais rápido que `string.len()`)
- Concatenação com `..` é útil, mas para muitas concatenações, prefira `table.concat()`

---

## Tabelas

### O que são tabelas?
Tabelas são estruturas de dados muito poderosas em Lua/Luau. Elas podem funcionar como arrays (listas ordenadas), dicionários (pares chave-valor), ou ambos ao mesmo tempo!

> Criando tabelas simples
```luau
  -- Array com números
  local pontuacoes = {100, 250, 175, 300}

  -- Array com strings
  local nomes = {"João", "Maria", "Pedro", "Ana"}

  -- Array misto
  local inventario = {"Espada", 50, "Poção", true}
```

> Acessando elementos de um array
```luau
  local frutas = {"maçã", "banana", "laranja"}

  print(frutas[1]) -- "maçã" (Lua começa no índice 1, não 0!)
  print(frutas[2]) -- "banana"
  print(frutas[3]) -- "laranja"
```

> Modificando elementos
```luau
  local pontos = {10, 20, 30}
  pontos[2] = 50  -- Muda o segundo elemento
  print(pontos[2]) -- 50
```

### Tabelas como dicionários (chave-valor)
```luau
  local jogador = {
    nome = "Alex",
    nivel = 15,
    vida = 100,
    experiencia = 2500
  }

  print(jogador.nome)        -- "Alex"
  print(jogador["nivel"])    -- 15 (outra forma de acessar)
```

### Tabelas mistas (array + dicionário)
```luau
  local personagem = {
    nome = "Guerreiro",
    nivel = 20,
    "Espada",      -- índice 1
    "Escudo",      -- índice 2
    "Armadura"     -- índice 3
  }

  print(personagem.nome)     -- "Guerreiro"
  print(personagem[1])       -- "Espada"
```

### Principais funções para tabelas
- `table.insert()` - Adicionar elemento
  ```luau
    local lista = {"a", "b"}
    table.insert(lista, "c")        -- Adiciona no final
    table.insert(lista, 2, "x")     -- Adiciona na posição 2
    print(lista[2]) -- "x"
  ```
- `table.remove()` - Remover elemento
  ```luau
    local numeros = {10, 20, 30, 40}
    table.remove(numeros, 2)  -- Remove o elemento na posição 2
    -- numeros agora é {10, 30, 40}
  ```
- `table.concat()` - Juntar elementos em string
  ```luau
    local palavras = {"Lua", "é", "incrível"}
    local frase = table.concat(palavras, " ")
    print(frase) -- "Lua é incrível"
  ```
- # (operador de tamanho tambem funciona em tabelas)
  ```luau
  local lista = {1, 2, 3, 4, 5}
  print(#lista) -- 5 (tamanho da tabela)
  ```

> Dicas importantes:
- Índices começam em `1`, não `0` (diferente de muitas linguagens)
- `nil` remove um elemento da tabela
- Tabelas são passadas por referência, não por valor

---

## Laços de Repetição (Loops)

### O que são loops?
Loops executam um bloco de código várias vezes automaticamente. Muito úteis para listas, animações, contadores, e repetições em jogos.

### Tipos de loops em Lua/Luau
- Loop `for`
  - Estrutura básica do `for`
    ```lua
    for contador = início, fim, incremento opcional do
      -- bloco de código
    end
    ```
    - O valor de incremento é opcional e, caso omitido, será considerado `1`.
    - O loop termina quando o contador ultrapassa o valor final (se incremento positivo) ou fica abaixo do final (se incremento negativo).
  - Exemplo Simples
    ```luau
      for i = 1, 5 do
        print("Contador:", i)
      end
      -- RESULTADO: 1, 2, 3, 4, 5
    ```
  - Exemplo Percorrendo tabelas.
    ```luau
      local frutas = {"maçã", "banana", "laranja"}
      for i = 1, #frutas do
        print(i, frutas[i])
      end

      -- Ou usando ipairs no lugar de # (recomendado):
      for i, fruta in ipairs(frutas) do
        print(i, fruta)
      end
    ```
- Loop `for in` (chave-valor)
  ```luau
    local stats = {vida = 100, mana = 50, forca = 25}

    for chave, valor in pairs(stats) do
      print(chave .. ": " .. valor)
    end
  ```
- `while loop` Repete o código enquanto a condição for verdadeira.
  ```luau
    local energia = 100

    while energia > 0 do
      print("Energia atual: " .. energia)
      energia = energia - 20
    end
  ```
- `repeat until` Repete o código pelo menos uma vez e só para quando a condição virar verdadeira.
  ```luau
  local tentativas = 0

  repeat
    print("Tentativa:", tentativas)
    tentativas = tentativas + 1
  until tentativas > 3
  ```

### Palavras-chave
- `break`: para o loop imediatamente
  ```luau
    for i = 1, 10 do
      if i == 5 then
        break   -- Para o loop quando i chega em 5
      end
      print(i)
    end
  ```
- `continue`:
  ```luau
  for i = 1, 10 do
    if i % 2 == 0 then
      continue
    end
    print(i)
  end
  ```

> Dicas importantes:
- Loops infinitos cuidado para não criar loops sem condição de parada!
- Use `pairs()` para iterar sobre chaves-valores
- Use `ipairs()` para iterar apenas sobre índices

---

## Funções (anônimas, argumentos variáveis)

### O que são funções?
Funções são blocos de código reutilizáveis que executam uma tarefa específica. Elas ajudam a organizar e evitar repetição no seu código.

> Como criar uma função
```luau
  function saudacao()
    print("Bem-vindo ao Roblox!")
  end

  -- Usando (chamando) a função
  saudacao()
```

> Funções com parâmetros (valores de entrada)
```luau
  function mostrarPontuacao(jogador, pontos)
    print(jogador .. " tem " .. pontos .. " pontos!")
  end

  mostrarPontuacao("Alex", 100) -- "Alex tem 100 pontos!"
```

> Funções com valor de retorno
```luau
  function soma(a, b)
    return a + b
  end

  local resultado = soma(3, 7)
  print("3 + 7 =", resultado) -- "3 + 7 = 10"
```

> Parâmetros padrão e opcionais
```luau
  function boasVindas(nome, mensagem)
    mensagem = mensagem or "Bem-vindo(a)!"
    print(nome .. ": " .. mensagem)
  end

  boasVindas("Maria") -- "Maria: Bem-vindo(a)!"
  boasVindas("Lucas", "Olá!") -- "Lucas: Olá!"
```

> Funções anônimas (sem nome)
```luau
  local dobro = function(x)
    return x * 2
  end

  print(dobro(5)) -- 10
```

> Funções dentro de tabelas
```luau
  local mathUtils = {}

  function mathUtils.quadrado(n)
    return n * n
  end

  print(mathUtils.quadrado(4)) -- 16
```

> Closures (função que retorna função)
```luau
  function multiplicador(fator)
    return function(x)
      return x * fator
    end
  end

  local duplica = multiplicador(2)
  print(duplica(10)) -- 20
```

> Dicas importantes:
- Use nomes claros e minúsculos, separados por underline ou camelCase: `funcao_legal` ou `funcaoLegal`
- Sempre prefira `local function` em scripts para evitar conflito global
- Funções podem retornar múltiplos valores:
  ```luau
    function info()
      return "João", 20
    end
    local nome, idade = info()
  ```
- Funções podem ser salvas em variáveis, passadas como argumento ou retorno de outra função

---

## Metatables

### O que são metatables?
Metatables são tabelas especiais que permitem mudar o comportamento de outras tabelas em Lua. Com elas, você pode criar operações personalizadas, herança, e até operadores especiais. É avançado, mas super útil!

> Por que usar metatables?
- Criar objetos com comportamentos próprios (programação orientada a objetos)
- Customizar como tabelas lidam com índices, operadores, eventos
- Simular classes e herança

> Como associar uma metatable a uma tabela
```luau
  local t = {}             -- Tabela comum
  local mt = {}            -- Metatable

  setmetatable(t, mt)      -- Liga a metatable à tabela
```

### Operador `__index`: Herança e busca
Permite que, se a tabela não tem um valor, ela procura na metatable.
```luau
  local base = {saudacao = function() print("Olá!") end}
  local objeto = {}
  setmetatable(objeto, {__index = base})

  objeto.saudacao()  -- "Olá!"  (procura na base)
```

### Operadores especiais (overloading)
Com metatables, sua tabela pode reagir a operadores (+, -, .. etc.)
```luau
  local vetorA = {x = 1, y = 2}
  local vetorB = {x = 3, y = 4}

  local mt = {
    __add = function(a, b)
      return {x = a.x + b.x, y = a.y + b.y}
    end
  }

  setmetatable(vetorA, mt)
  setmetatable(vetorB, mt)

  local resultado = vetorA + vetorB  -- Usa a função __add
  print(resultado.x, resultado.y)    -- 4  6
```

> Principais metamethods
- `__index`: Busca valor em outra tabela
- `__newindex`: Controla atribuição
- `__add`, `__sub`, `__mul`, etc.: Personaliza operadores aritméticos
- `__tostring`: Personaliza conversão para string
- `__eq`, `__lt`, `__le`: Comparações personalizadas

---

## Classes & Construtores (OOP em Roblox)

### O que são Classes?
Classes não existem “prontas” em Lua como em outras linguagens, mas podemos simular esse comportamento usando tabelas e funções. Uma classe é um modelo para criar vários objetos com características e comportamentos parecidos.

### O que é um Construtor?
Um construtor é uma função especial usada para criar novos objetos baseados em uma “classe”. Ele define os valores iniciais (estado) do objeto.

> Exemplo simples de classe e construtor
```luau
  -- Definindo a "classe" Pessoa
  local Pessoa = {}
  Pessoa.__index = Pessoa  -- importante para herança de métodos

  -- Construtor
  function Pessoa.new(nome, idade)
    local self = setmetatable({}, Pessoa)
    self.nome = nome or "Sem Nome"
    self.idade = idade or 0
    return self
  end

  -- Método da classe
  function Pessoa:falar()
    print("Olá! Meu nome é " .. self.nome)
  end

  -- Criando objetos
  local p1 = Pessoa.new("Alice", 22)
  local p2 = Pessoa.new("Bob", 18)

  p1:falar() -- "Olá! Meu nome é Alice"
  p2:falar() -- "Olá! Meu nome é Bob"
```

> O que significa self?
self é uma referência ao próprio objeto.

> Dicas importantes:
- Com `:` (dois pontos) você define implicitamente e chama métodos que usam self.
- Sempre use setmetatable(obj, Classe) e Classe.__index = Classe para ativar os métodos
- Prefira function `Classe:método()` ao invés de `function Classe.método(self)`
- Para projetos maiores, divida suas “classes” em ModuleScripts.

---

## Corrotinas (Coroutines)

### O que são corrotinas?
Corrotinas são funções que podem pausar e continuar sua execução, permitindo criar tarefas assíncronas (que avançam em partes, não tudo de uma vez). São úteis para animações, processos longos e sistemas que não podem bloquear o jogo esperando terminar.

> Por que usar corrotinas?
- Para fazer tarefas que precisam esperar ou executar em etapas (ex: animações, loading, ações sequenciais)
- Para evitar travamentos ou lentidão no seu jogo

### Principais funções para corrotinas em Lua/Luau
- `coroutine.create()` — cria uma nova corrotina
- `coroutine.resume()` — começa ou continua a execução da corrotina
- `coroutine.yield()` — pausa a corrotina e retorna para quem chamou
- `coroutine.status()` — verifica o estado atual

> Exemplo básico:
```luau
  function processo()
    print("Iniciando...")
    coroutine.yield()         -- Pausa aqui
    print("Metade feita!")
    coroutine.yield()         -- Pausa aqui
    print("Finalizado!")
  end

  local co = coroutine.create(processo)
  coroutine.resume(co)     -- Saída: "Iniciando..."
  coroutine.resume(co)     -- Saída: "Metade feita!"
  coroutine.resume(co)     -- Saída: "Finalizado!"
```
> Usando corrotina para esperar sem travar
```luau
  function esperarSegundos(segundos)
    print("Esperando " .. segundos .. " segundos...")
    local t = os.time()
    while os.time() - t < segundos do
      coroutine.yield()
    end
    print("Tempo acabou.")
  end

  local co = coroutine.create(function()
    esperarSegundos(3)
    print("Continuando trabalho!")
  end)

  -- Em Roblox, isso seria chamado em partes dentro de loops (pouco usado diretamente)
  coroutine.resume(co)   -- "Esperando 3 segundos..."
  -- Chamaria resume em cada frame ou evento até acabar
```

> Dicas importantes:
- Evite corrotinas para lógica simples ou scripts de gameplay padrão — prefira `wait()`, `delay()`, e eventos do Roblox
- Corrotina é ideal quando você precisa dividir trabalho em partes para não travar o servidor ou cliente

---

## Biblioteca Math & Operações Matemáticas

### Biblioteca Math (math)
A biblioteca math oferece funções matemáticas prontas para cálculos, física de games, movimentação, efeitos de partículas e mais.

> Principais funções do módulo math
```luau
  local x = 3.7
  print(math.floor(x))     -- 3  (arredonda para baixo)
  print(math.ceil(x))      -- 4  (arredonda para cima)
  print(math.abs(-10))     -- 10 (valor absoluto)
  print(math.max(4, 8))    -- 8  (pega o maior valor)
  print(math.min(4, 8))    -- 4  (pega o menor valor)
  print(math.sqrt(16))     -- 4  (raiz quadrada)
  print(math.pi)           -- 3.141592...
  print(math.random())     -- Número aleatório entre 0 e 1
  print(math.random(1,10)) -- Número aleatório entre 1 e 10
```
> Arredondamentos e limites
```luau
  local valor = 5.67
  print(math.floor(valor))    -- 5
  print(math.ceil(valor))     -- 6
  print(math.round(valor))    -- 6 (arredonda para o mais próximo, Luau)
```
> Trigonometria
```luau
  local anguloGraus = 30
  local anguloRadianos = math.rad(anguloGraus)
  local seno = math.sin(anguloRadianos)
  print(seno) -- 0.5
```
> Constantes úteis
- `math.pi` — valor de π (pi)
- `math.huge` — representa infinito
> Funções de conversão
- `math.rad(graus)` — graus para radianos
- `math.deg(radianos)` — radianos para graus

> Dicas importantes
- Consulte sempre a documentação: Documentação Luau Math

---

## Tratamento de Erros, Debugging e Boas Práticas

### O que são erros?
Erros (bugs) acontecem quando o código não funciona como esperado. Aprender a identificar, corrigir e até mesmo prevenir erros é fundamental para qualquer desenvolvedor!

### Tipos comuns de erros
- Sintaxe: erro quando "escreveu errado" a linguagem, ex: esqueceu end, parêntese, vírgula
- Execução: erro ao rodar o script, ex: tentou acessar uma variável que não existe
- Lógica: erro no resultado, ex: cálculo ou condição errada (o código roda mas faz algo inesperado!)

> Mensagens de erro mais frequentes em Roblox/Lua
- 'attempt to index nil value' — tentou usar algo que não existe
- 'expected near' — falta de ponto e vírgula, parêntese, palavra-chave
- 'attempt to call a nil value' — tentou chamar como função algo indefinido

### Como lidar e identificar erros?
1. Leia sempre a mensagem de erro
  - O Roblox Studio mostra a linha do erro
  - Veja o nome da função, da variável e a linha indicada
2. Use `print()` para debugar
 - Printando valores, nomes de variáveis, você descobre onde o script está quebrando
    ```lua
      local nome = nil
      print(nome)  -- nil
      print(nome:sub(1, 3))  -- ERRO: attempt to index nil value
    ```
3. Use `pcall()` (Protected Call) para tratar erros sem travar o script
  ```lua
    local sucesso, resultado = pcall(function()
      return 10 / 0
    end)
    print(sucesso, resultado)  -- false   inf (erro capturado, não trava tudo)
  ```

> Exemplo prático: function segura
  ```lua
    function dividir(a, b)
      local ok, res = pcall(function()
        return a / b
      end)
      if ok then
        return res
      else
        print("Erro ao dividir:", res)
        return nil
      end
    end

    dividir(10, 2)   -- 5
    dividir(5, 0)    -- Erro ao dividir: [mensagem de erro]
  ```

> Técnicas basicas de debugging
- **Isolar o problema**: comente partes do código para ver onde está o bug
- **Testar aos poucos**: escreva código em pedaços, testando cada etapa

