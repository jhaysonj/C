# Descrição do Guia de Low-Level
Idealizado por [Jhayson Jales]
Dificuldade do Guia [Medium]
Material de Apoio [https://www.youtube.com/watch?v=oZeezrNHxVo&list=PLIfZMtpPYFP5qaS2RFQxcNVkmJLGQwyKE&index=1]
Ano de inicio [2024 - ∞]
Obs: O guia será realizado em linux, especificamente em distro ubuntu-base
## Pré Requisitos
Para verificar se esse guia é para você, verifique se possui conhecimento básico em:
[Lógica de programação, Linux]

# Semana 1
Definimos o retorno de 0 a execução bem sucedida do programa, qualquer coisa diferente de 0, indica que houve um erro na execução.

Programa `hello.c`
```c
#include <stdio.h>
int main(void){

	printf("C-GRIS\n");
	return 0;
}
```
Compilamos o programa
```
gcc -o hello hello.c
```


**Status de Saída**
Após a execução de um comando, o shell armazena o status de saída desse comando em uma variável especial chamada `$?`. Um valor de `0` geralmente indica que o comando foi executado com sucesso, enquanto qualquer outro valor indica que ocorreu algum tipo de erro durante a execução do comando.
```
┌──(romio@pop-os)-[~/Documents/C/semana 1]
└─$ ls      
hello  hello.c
                                                                                                                                        
┌──(romio@pop-os)-[~/Documents/C/semana 1]
└─$ echo $?
0

```

Com isso, fazemos a operação AND entre o executável e o comando echo, ou seja, se o executável retornar 0, indica que o programa foi executado corretamente  e, consequentemente, o AND entre o executável (true) e o comando echo (true) será true
```
./hello && echo funcionou
C-GRIS
funcionou

```

**Operação AND:**

| A     | B     | A AND B |
|-------|-------|---------|
| false | false |  false  |
| false | true  |  false  |
| true  | false |  false  |
| true  | true  |  true   |
Por outro lado, se alterarmos o programa `hello.c` para retornar 1, o resultado da operação and será false.
Programa hello_false.c
```
#include <stdio.h>

int main(void){

	printf("C-GRIS\n");
	return 1;
}

```

Verificando status de saida:
```
┌──(romio@pop-os)-[~/Documents/C/semana 1]
└─$ gcc -o hello_false hello_false.c 

┌──(romio@pop-os)-[~/Documents/C/semana 1]
└─$ ./hello_false                  
C-GRIS
                                                                                                                                        
┌──(romio@pop-os)-[~/Documents/C/semana 1]
└─$ echo $?
1

```


Compilando e fazendo a operação AND com o comando echo
```
┌──(romio@pop-os)-[~/Documents/C/semana 1]
└─$ ./hello_false && echo funcionou
C-GRIS
                        
```

Obs: Como a operação AND retornou false, o comando echo não foi executado