# O que é Fila ou Queue

Uma fila (queue) é uma estrutura de dados onde os elementos são inseridos e removidos seguindo o princípio FIFO (First In, First Out), ou seja, o primeiro elemento a ser inserido é o primeiro a ser removido.

Pense em uma fila de pessoas, onde quem entra primeiro sai primeiro.

# Como fazer no Pawn

### Parte 1°: Criando o cabeçalho

1. Primeiro, precisamos definir o tamanho da nossa fila
	```cpp
	#define MAX_QUEUE_SIZE 100
	```

2. Após isso, precisamos criar um array onde armazenaremos os valores inseridos na fila
	```cpp
	new Queue[MAX_QUEUE_SIZE];
	```

3. Também precisaremos de variáveis para armazenar a posição do início (`head`), do final (`tail`) da fila e do tamanho (`size`) da fila
	```cpp
	new head, tail, size;
	```

Como resultado, esse será o nosso pontapé inicial

```cpp
#define MAX_QUEUE_SIZE 100

new Queue[MAX_QUEUE_SIZE];
new head, tail, size;
```

### Parte 2°: Criando a função Enqueue (Inserir)

1. Primeiro, criaremos o cabeçalho da nossa função
	```cpp
	stock Enqueue(valor)
	{
	}
	```

2. Antes de inserir o valor na fila, precisamos verificar se há espaço suficiente
	```cpp
	if(size >= MAX_QUEUE_SIZE)
	{
		// A fila está cheia
		return 0;
	}
	```

3. Se houver espaço, podemos inserir o valor na posição `tail` e ajustar o `tail` para apontar para a próxima posição
	```cpp
	Queue[tail] = valor;
	```

4. Precisamos também ajustar a próxima posição `tail` para que o próximo valor não seja inserido na mesma posição
	```cpp
	tail = (tail + 1) % MAX_QUEUE_SIZE;
	```

5. E para terminar, devemos aumentar o valor de `size` para a próxima verificação
	```cpp
	size++;
	return 1;
	```

Como resultado, essa será a nossa função `Enqueue`:

```cpp
stock Enqueue(valor)
{
	if(size >= MAX_QUEUE_SIZE) return 0;
	Queue[tail] = valor;
	tail = (tail + 1) % MAX_QUEUE_SIZE;
	size++;
	return 1;
}
```

### Parte 3°: Criando a função Dequeue (Remover)

1. Primeiro, criaremos o cabeçalho da nossa função
	```cpp
	stock Dequeue()
	{
	}
	```

2. Antes de remover o valor da fila, precisamos verificar se há algum valor nela
	```cpp
	if(size == 0)
	{
		// A fila está vazia
		return -1;
	}
	```

3. Se houver algum valor na fila, obtemos o valor que está na posição `head`
	```cpp
	new valor = Queue[head];
	```

4. Precisamos também ajustar a próxima posição `head` para que o próximo valor não seja obtido da mesma posição
	```cpp
	head = (head + 1) % MAX_QUEUE_SIZE;
	```

5. E para terminar, devemos diminuir o valor de `size` para a próxima verificação, e retornar o valor obtido
	```cpp
	size--;
	return valor;
	```

Como resultado, essa será a nossa função `Dequeue`:

```cpp
stock Dequeue()
{
	if(size == 0) return -1;
	new valor = Queue[head];
	head = (head + 1) % MAX_QUEUE_SIZE;
	size--;
	return valor;
}
```

### Parte 4°: Criando funções extras

Podemos criar funções extras para saber o estado da nossa fila. Por exemplo, veja essas duas funções `IsQueueEmpty` e `IsQueueFull`:

```cpp
stock IsQueueEmpty() return (size == 0);

stock IsQueueFull() return (size >= MAX_QUEUE_SIZE);
```

### Parte 5°: Testando o sistema

Eu elaborei um script para testar as funções `Enqueue` e `Dequeue`. Acompanhe abaixo:

```cpp
// código da minha fila
#include <queue> 

main()
{
	Enqueue(5);
	Enqueue(10);
	Enqueue(25);
	
	printf("1° Valor a sair: %d", Dequeue());
	printf("2° Valor a sair: %d", Dequeue());
	printf("3° Valor a sair: %d", Dequeue());
}
```

Como resultado, ao executar o script, receberemos os seguintes registros:

```
1° Valor a sair: 5
2° Valor a sair: 10
3° Valor a sair: 25
```

---

Este pequeno tutorial simples foi elaborado por [DeviceBlack](https://github.com/devicewhite).

Espero que aproveitem esse estilo de armazenamento de dados em arrays usando fila.
