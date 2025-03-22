# Guia Básico de Terminal Linux e Programação em C

## Parte 1: Comandos Básicos do Terminal

### O que é o Terminal?
O Terminal é uma interface de texto onde você pode digitar comandos para o computador executar. É como conversar diretamente com o sistema, sem precisar de botões ou menus.

### Comandos Essenciais do Dia a Dia

#### Navegação
- `pwd` - **Onde estou?** Mostra o diretório (pasta) atual
  ```
  $ pwd
  /home/usuario
  ```

- `ls` - **O que tem aqui?** Lista os arquivos e pastas do diretório atual
  ```
  $ ls
  Documentos  Downloads  Imagens  Música  Vídeos
  ```

- `cd` - **Mudar de lugar** Navega entre diretórios
  ```
  $ cd Documentos    # Entra na pasta Documentos
  $ cd ..            # Volta uma pasta acima
  $ cd ~             # Vai para sua pasta pessoal
  ```

#### Arquivos e Pastas
- `mkdir` - **Criar pasta** Cria um novo diretório
  ```
  $ mkdir MeusProjetos
  ```

- `touch` - **Criar arquivo** Cria um arquivo vazio
  ```
  $ touch meu_programa.c
  ```

- `cp` - **Copiar** Copia arquivos ou pastas
  ```
  $ cp arquivo.txt copia_arquivo.txt
  ```

- `mv` - **Mover ou renomear** Move arquivos ou renomeia
  ```
  $ mv arquivo.txt novo_nome.txt       # Renomear
  $ mv arquivo.txt ~/Documentos/       # Mover
  ```

- `rm` - **Remover** Apaga arquivos (cuidado: não vai para a lixeira!)
  ```
  $ rm arquivo.txt            # Remove um arquivo
  $ rm -r pasta/              # Remove uma pasta e todo seu conteúdo
  ```

#### Visualização de Arquivos
- `cat` - **Ver conteúdo** Mostra o conteúdo completo de um arquivo
  ```
  $ cat arquivo.txt
  ```

- `less` - **Ver por partes** Para arquivos grandes (use Q para sair)
  ```
  $ less arquivo_grande.txt
  ```

#### Sistema
- `clear` - **Limpar tela** Limpa a tela do terminal
  ```
  $ clear
  ```

- `sudo` - **Super poderes** Executa comandos como administrador
  ```
  $ sudo apt update
  ```

## Parte 2: Usando o VSCodium e Compilando em C

### Abrindo o VSCodium em uma Pasta Específica

1. **Abrir o terminal** (Ctrl+Alt+T na maioria das distribuições)

2. **Navegar até a pasta desejada**
   ```
   $ cd ~/Documentos/MeusProjetos #
   ```
   Letras maiusculas e minusculas são diferentes,
   e podem influienciar no nomes das coisas

4. **Abrir o VSCodium na pasta atual**
   ```
   $ codium .
   ```
   (O ponto `.` significa "pasta atual")

### Compilando e Executando um Programa em C

1. **Criar um arquivo C** (dentro do VSCodium ou pelo terminal)
   ```
   $ touch hello.c
   ```

2. **Compilar o programa** usando gcc
   ```
   $ gcc hello.c -o hello
   ```
   Explicação:
   - `gcc` é o compilador
   - `hello.c` é o arquivo fonte
   - `-o hello` especifica o nome do programa executável

3. **Executar o programa**
   ```
   $ ./hello
   ```
   (O `./` indica "executar arquivo nesta pasta")

## Parte 3: Introdução à Programação em C

### Primeiro Programa: Hello World

Vamos criar um programa simples que mostra uma mensagem:

```c
// Arquivo: hello.c
#include <stdio.h>

int main() {
    printf("Olá, mundo!\n");
    return 0;
}
```

Explicação:
- `#include <stdio.h>` - Inclui a biblioteca para entrada/saída
- `int main()` - Função principal onde o programa começa
- `printf()` - Função para mostrar texto na tela
- `\n` - Caractere especial para nova linha
- `return 0` - Indica que o programa terminou com sucesso

### Variáveis em C

Variáveis são como caixas na memória do computador que guardam valores:

```c
// Arquivo: variaveis.c
#include <stdio.h>

int main() {
    // Declarando variáveis
    int idade = 25;                  // Números inteiros
    float altura = 1.75;             // Números decimais
    char letra = 'A';                // Caracteres únicos
    char nome[50] = "Maria Silva";   // Texto (string)
    
    // Mostrando as variáveis
    printf("Nome: %s\n", nome);
    printf("Idade: %d anos\n", idade);
    printf("Altura: %.2f metros\n", altura);
    printf("Primeira letra: %c\n", letra);
    
    return 0;
}
```

Explicação dos tipos:
- `int` - Números inteiros (sem decimais)
- `float` - Números com decimais
- `char` - Caractere único
- `char nome[50]` - Array de caracteres (texto)

Explicação dos marcadores no printf:
- `%s` - Para strings (textos)
- `%d` - Para números inteiros
- `%f` - Para números decimais (%.2f mostra 2 casas decimais)
- `%c` - Para caracteres

### Entrada de Dados (Input)

Vamos criar um programa que pede informações ao usuário:

```c
// Arquivo: input.c
#include <stdio.h>

int main() {
    char nome[50];
    int idade;
    
    // Pedindo nome
    printf("Digite seu nome completo: ");
    // fgets é mais seguro para ler textos com espaços
    fgets(nome, 50, stdin);
    
    // Pedindo idade
    printf("Digite sua idade: ");
    scanf("%d", &idade);
    
    // Mostrando os dados
    printf("\nSeu nome é %s", nome);
    printf("Você tem %d anos.\n", idade);
    
    return 0;
}
```

Explicação:
- `fgets(nome, 50, stdin)` - Lê uma linha de texto até 49 caracteres
- `scanf("%d", &idade)` - Lê um número inteiro
- O símbolo `&` pega o endereço da variável na memória

### Estruturas Condicionais (if-else)

Vamos criar um programa que toma decisões:

```c
// Arquivo: decisoes.c
#include <stdio.h>

int main() {
    int idade;
    
    printf("Digite sua idade: ");
    scanf("%d", &idade);
    
    if (idade < 0) {
        printf("Idade inválida!\n");
    } 
    else if (idade < 18) {
        printf("Você é menor de idade.\n");
    } 
    else if (idade < 60) {
        printf("Você é adulto.\n");
    } 
    else {
        printf("Você é idoso.\n");
    }
    
    return 0;
}
```

Explicação:
- `if` - Se a condição for verdadeira, execute o código
- `else if` - Se a condição anterior for falsa, teste esta
- `else` - Se todas as condições anteriores forem falsas

### Loops (Repetições)

#### Loop For
Usado quando sabemos quantas vezes queremos repetir algo:

```c
// Arquivo: loop_for.c
#include <stdio.h>

int main() {
    int i;
    
    printf("Contagem de 1 a 5:\n");
    
    for (i = 1; i <= 5; i++) {
        printf("%d ", i);
    }
    printf("\n");
    
    return 0;
}
```

Explicação:
- `for (início; condição; incremento)` - Repete enquanto a condição for verdadeira
- `i = 1` - Valor inicial
- `i <= 5` - Condição para continuar
- `i++` - Incrementa i cada vez (i++ é o mesmo que i = i + 1)

#### Loop While
Usado quando queremos repetir enquanto uma condição for verdadeira:

```c
// Arquivo: loop_while.c
#include <stdio.h>

int main() {
    int numero = 1;
    
    printf("Números ímpares até 10:\n");
    
    while (numero <= 10) {
        if (numero % 2 != 0) {  // Verifica se é ímpar
            printf("%d ", numero);
        }
        numero++;
    }
    printf("\n");
    
    return 0;
}
```

Explicação:
- `while (condição)` - Repete enquanto a condição for verdadeira
- `numero % 2 != 0` - Verifica se o resto da divisão por 2 não é zero (ímpar)

### Funções

Funções são blocos de código reutilizáveis:

```c
// Arquivo: funcoes.c
#include <stdio.h>

// Declaração da função
int somar(int a, int b);
void saudacao(char nome[]);

int main() {
    int resultado = somar(5, 3);
    printf("5 + 3 = %d\n", resultado);
    
    saudacao("Carlos");
    
    return 0;
}

// Definição das funções
int somar(int a, int b) {
    return a + b;  // Retorna a soma dos valores
}

void saudacao(char nome[]) {
    printf("Olá, %s! Bem-vindo(a) ao C!\n", nome);
    // void significa que não retorna valor
}
```

Explicação:
- `int somar(int a, int b)` - Função que recebe dois inteiros e retorna um inteiro
- `void saudacao(char nome[])` - Função que recebe um texto e não retorna valor
- As funções precisam ser declaradas antes de serem usadas

### Programa Completo: Sistema de Cadastro Simples

Vamos juntar tudo em um pequeno programa de cadastro:

```c
// Arquivo: cadastro.c
#include <stdio.h>
#include <string.h>  // Para funções de string

#define MAX_PESSOAS 5  // Constante para o máximo de cadastros

int main() {
    // Declaração de variáveis para armazenar dados
    char nomes[MAX_PESSOAS][50];
    int idades[MAX_PESSOAS];
    float alturas[MAX_PESSOAS];
    int cadastros = 0;
    int opcao;
    
    // Menu principal
    do {
        printf("\n===== SISTEMA DE CADASTRO =====\n");
        printf("1. Cadastrar pessoa\n");
        printf("2. Listar todos os cadastros\n");
        printf("3. Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &opcao);
        
        // Limpar o buffer de entrada
        while (getchar() != '\n');
        
        switch (opcao) {
            case 1:  // Cadastrar pessoa
                if (cadastros < MAX_PESSOAS) {
                    printf("\n-- Novo Cadastro --\n");
                    
                    printf("Nome completo: ");
                    fgets(nomes[cadastros], 50, stdin);
                    nomes[cadastros][strcspn(nomes[cadastros], "\n")] = 0;  // Remove o \n
                    
                    printf("Idade: ");
                    scanf("%d", &idades[cadastros]);
                    
                    printf("Altura (m): ");
                    scanf("%f", &alturas[cadastros]);
                    
                    cadastros++;
                    printf("\nCadastro realizado com sucesso!\n");
                } else {
                    printf("\nLimite de cadastros atingido!\n");
                }
                // Limpar o buffer novamente
                while (getchar() != '\n');
                break;
                
            case 2:  // Listar cadastros
                if (cadastros > 0) {
                    printf("\n-- Pessoas Cadastradas --\n");
                    for (int i = 0; i < cadastros; i++) {
                        printf("\nCadastro #%d:\n", i+1);
                        printf("Nome: %s\n", nomes[i]);
                        printf("Idade: %d anos\n", idades[i]);
                        printf("Altura: %.2f metros\n", alturas[i]);
                    }
                } else {
                    printf("\nNenhum cadastro encontrado!\n");
                }
                break;
                
            case 3:  // Sair
                printf("\nEncerrando o programa...\n");
                break;
                
            default:
                printf("\nOpção inválida! Tente novamente.\n");
        }
    } while (opcao != 3);
    
    return 0;
}
```

Este programa demonstra:
- Uso de arrays para armazenar múltiplos dados
- Estrutura de menu com `do-while`
- Comando `switch` para múltiplas opções
- Interatividade com o usuário
- Aplicação de condicionais (`if-else`)
- Loops (`for`) para listar cadastros

## Dicas Finais

1. **Salve frequentemente** seu trabalho no VSCodium

2. **Compile frequentemente** para identificar erros cedo
   ```
   $ gcc programa.c -o programa
   ```

3. **Use comentários** para explicar seu código
   ```c
   // Isso é um comentário de uma linha
   
   /*
    * Isso é um comentário
    * de múltiplas linhas
    */
   ```

4. **Identar o código** (usar espaços ou tabs) para maior legibilidade

5. Quando ocorrer um erro de compilação, **leia atentamente a mensagem**
   - Geralmente indica a linha e o tipo do erro

6. Para obter **ajuda sobre comandos** do terminal:
   ```
   $ man comando      # Mostra o manual do comando
   $ comando --help   # Mostra ajuda rápida
   ```

Bons estudos e boa programação!
