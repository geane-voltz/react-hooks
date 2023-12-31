<div align="center">

# REACT
</div>

<div align="center">
Repositório criado com o objetivo de centralizar estudos de React.
</div>

## Índice
- [1. Hooks](#1-hooks)
- [1.1. useState](#11-usestate)
- [1.2. useEffect](#12-useeffect)
- [1.3. useRef](#13-useref)
- [1.4. useMemo](#14-usememo)
- [1.5. useCallback](#15-usecallback)
- [1.6. useContext](#16-usecontext)
- [1.7. Custom Hooks](#17-custom-hooks)

### 1. Hooks
Os Hooks são funções especiais do React que permitem controlarmos o estado e o ciclo de vida de componentes funcionais. Isso antes só era possível com classes.
#### 1.1. useState
Estado: O estado de uma aplicação representa as características dela naquele momento. Por exemplo: os dados do usuário foram carregados, o botão está ativo, o usuário está na página de contato e etc.
O useState é uma função que retorna uma Array com 2 valores. O primeiro valor guarda o dado do estado atual, pode ser qualquer tipo de dado como strings, arrays, números, boolean, null, undefined e objetos. O segundo valor é uma função que pode ser utilizada para modificarmos o estado do primeiro valor.
Quando a função de modificação do estado é ativada, todos os componentes que dependerem do estado, serão renderizados novamente e os seus filhos também. É isso que garante a reatividade de componentes funcionais no React.
##### Múltiplos Estados
Não existem limites para o uso do useState, podemos definir diversos no mesmo componente.
##### Reatividade
Não modifique o estado diretamente. Utilize sempre a função de atualização do estado, pois ela que garante a reatividade dos componentes.
##### Callback
Podemos passar uma função de callback para atualizar o estado. A função de callback recebe um parâmetro que representa o valor anterior e irá modificar o estado para o valor que for retonado na função.
##### React.StrictMode
O modo estrito invoca duas vezes a renderização do componente, quando o estado é atualizado. Assim é possível identificarmos funções com efeitos coláterais (side effects) e eliminarmos as mesmas.

Funções com efeitos coláterais são aquelas que modificam estados que estão fora das mesmas.

#### 1.2. useEffect
Todo componente possui um ciclo de vida. Os principais momentos acontecem quando o componente é renderizado, atualizado ou destruído. Com o React.useEffect() podemos definir um callback que irá ser executado durante certos momentos do ciclo de vida do componente.
##### Array de Dependências
No useEffect podemos definir dois argumentos, o primeiro é a função de callback que será executada, o segundo é uma array com uma lista de dependências. A lista de dependências serve para informarmos quando o efeito deve ocorrer.
##### Dependências Obrigatórias
Se utilizarmos o valor de um hook ou propriedade dentro de um efeito, ele irá indicar a necessidade de definirmos o mesmo como uma dependência na array.
##### Componente Montou
O useEffect será especialmente utilizado quando precisamos definir um efeito que deve ocorrer uma vez apenas, como o fetch de dados no servidor por exemplo.
##### Múltiplos Efeitos
Podemos ter diversos useEffect no nosso código. O ideal é separarmos efeitos diferentes em useEffect diferentes.
##### Antes de Desmontar
As vezes precisamos executar um efeito sempre que um componente for desmontado. Para isso utilizamos um callback no retorno do callback do efeito.

#### 1.3. useRef
Retorna um objeto com a propriedade current. Esse objeto pode ser utilizado para guardarmos valores que irão persistir durante todo o ciclo de vida do elemento. Geralmente usamos o mesmo para nos referirmos a um elemento do DOM, sem precisarmos utilizar o querySelector ou similar.
##### focus()
É comum utilizarmos em formulários, quando precisamos de uma referência do elemento para colocarmos o mesmo em foco.
##### Referência
O seu uso não é restrito a elementos do dom. Podemos utilizar também para guardarmos a referência de qualquer valor, como de um setTimeout por exemplo.

#### 1.4. useMemo
Memoriza um valor, evitando a recriação do mesmo todas as vezes em que um componente for atualizado. Recebe um callback e uma array de dependências. Serve para casos em que você faz uma operação lenta para retornar um valor.

#### 1.5. useCallback
Permite definirmos um callback e uma lista de dependências do callback. Esse callback só será recriado se essa lista de dependências for modificada, caso contrário ele não irá recriar o callback. Diferente do function usando no "handleClick", o callback é criado só na primeira vez que é renderizado.

#### 1.6. useContext
O useContext é o hook que deve ser utilizado para consumirmos o contexto e termos assim acesso aos dados de value. Devemos passar o contexto criado como seu agumento.
##### GlobalStorage
Exemplo de uso real do context. Podemos passar qualquer coisa no value do context, até estados e funções atualizadoras do useState.

#### 1.7. Custom Hooks
Podemos criar nossos próprios hooks, assim evitamos a repetição de código. Todo custom hook deve começar com a palavra use. Exemplo: useNomeDoHook. Podemos retornar o que quisermos do hook, seja um valor único, uma array ou um objeto.
