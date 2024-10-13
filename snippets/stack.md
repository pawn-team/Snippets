# O que é Pilha ou Stack

Uma pilha (stack) é uma estrutura de dados onde os elementos são inseridos e removidos seguindo o princípio LIFO (Last In, First Out), ou seja, o último elemento a ser inserido é o primeiro a ser removido.

Pense em um baralho de cartas, a última carta é a primeira a ser removida.

# Como fazer no Pawn

### Parte 1°: Criando o cabeçalho

1. Primeiro precisamos definir o tamanho da nossa pilha
	```cpp
	#define MAX_STACK_SIZE 100
	```

2. Após isso precisamos criar um array, onde armazenaremos os valores inseridos na pilha
	```cpp
	new Stack[MAX_STACK_SIZE];
	```

3. Também vamos precisar de uma variavel que armazene a posição do ultimo valor inserido
	```cpp
	new top = -1; // -1 significará vazio
	```

Como resultado, esse será o nosso pontapé inicial:

```cpp
#define MAX_STACK_SIZE 100

new Stack[MAX_STACK_SIZE];
new top = -1;
```

### Parte 2°: Criando função Push (Inserir)

1. Primeiros criaremos o cabeçalho da nossa função 
	```cpp
	stock Push(valor)
	{
	}
	```

2. Antes de inserir o valor na pilha, precisamos saber se tem espaço suficiente
	```cpp
	if(top >= (MAX_STACK_SIZE - 1))
	{
		// A pilha está cheia
		return 0;
	}
	```

3. Se a pilha estiver vazia, então podemos inserir o valor na pilha
	```cpp
	Stack[++top] = valor;
	return 1;
	```

Como resultado, essa será a nossa função Push

```cpp
stock Push(valor)
{
	if(top >= (MAX_STACK_SIZE - 1)) return 0;
	Stack[++top] = valor;
	return 1;
}
```

### Parte 3°: Criando função Pop (Remover)

1. Primeiros criaremos o cabeçalho da nossa função 
	```cpp
	stock Pop()
	{
	}
	```

2. Antes de remover o valor da pilha, precisamos saber se tem algum valor nela
	```cpp
	if(top == -1)
	{
		// A pilha está vazia
		return -1;
	}
	```

3. Caso tenha algum valor na pilha, retornamos e removemos o seu valor
	```cpp
	return Stack[top--];
	```

Como resultado, essa será nossa função Pop

```cpp
stock Pop()
{
	if(top == -1) return -1;
	return Stack[top--];
}
```

### Parte 4°: Criando funções extras

Podemos criar funções extras para saber o estado da nossa pilha

Por exemplo, veja essas duas funções `IsStackEmpty` e `IsStackFull`

```cpp
stock IsStackEmpty() return (top == -1);

stock IsStackFull() return (top >= (MAX_STACK_SIZE - 1));
```

### Parte 5°: Testando o sistema

Eu elaborei um script para testar as funções `push` e `pop`, acompanhe abaixo

```cpp
// codigo da minha pilha
#include <stack> 

main()
{
	Push(5);
	Push(10);
	Push(25);
	
	printf("1° Valor a sair: %d", Pop());
	printf("2° Valor a sair: %d", Pop());
	printf("3° Valor a sair: %d", Pop());
}
```

Como resultado, ao executar o script receberemos os seguintes registros
```
1° Valor a sair: 25
2° Valor a sair: 10
3° Valor a sair: 5
```

---

Este pequeno tutorial simples foi elaborado por [DeviceBlack](https://github.com/devicewhite)

Espero que façam um bom proveito desse estilo de armazenamento de dados em arrays
