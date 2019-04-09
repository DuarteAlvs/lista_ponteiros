/..--------------Lista de Exercícios (Ponteiros)----------------../
##Discente: Lindoarte Alves Moreira
1  Qual a utilidade do aprendizado do uso de ponteiro para aplicações em engenharia?
               
    A aprendizagem de ponteiros na computação nos fornece técnicas importantes para manipulação de dados. Por vezes precisamos operar a nível de hardware para obtenção de desempenho e soluções de porblemas numéricos. Lidar com ponteiros numa linguagem adequado como C, por exemplo, possibilita adentrar de forma eficiente no pensamento engenhoso de criação e optimização computacional. Além disso, nos propõe obter conhecimento sobre o funcionamento da máquina de cálculos, conhecimento fundamental para programar em qualquer outra linguagem.
   
2 Seja o seguinte trecho de programa:
   int i=3,j=5;
   int *p, *q;
   p = &i;
   q = &j;
Determine o valor das seguintes expressões:

    p == &i;
    O valor de p é o endereço que guarda o valor de i (3). Fazendo uma variável booleana receber essa proposição e exibindo-a, essa irá retornar verdadeiro (1). */
 
    *p - *q;
    O resultado é a soma 3-5 = -2. Visto que p e q são ponteiros, e *p e *q são suas desreferenciações.*/

     **&p;
    Aqui é possível imaginar que '*&' se anulam, restando *p, que é o valor contido na variável i (3)*/

     *p/(*q) + 7;
     Nesta operação, como as variáveis, dadas referenciações *p e *q, são de tipo inteiro, a divisão '*p/(*q)' é zero porque o numerador é menor que o denominador*/

3 Mostre o que será impresso por programa supondo que i ocupa o endereço 4094 na memória

    int i=5, *p;
    p = &i;
    printf("%x %d %d %d %d", p, *p+2,**&p,3**p,**&p+4);
    }
    //72fe4c 7 5 15 9
    //4094 7 5 15 9
         

4 Se i e j são variáveis inteiras e p e q ponteiros para int, quais das seguintes expressões de atribuição são ilegais?

    p = i;            //ilegal
    q = &j;           //legal
    p = &*&i;         //legal
    i = (*&)j;        //ilegal, porque a ordem de precedência começa nos operadores * e & não identificam o tratamento prioritário de ponteiros.
    i = *&j;         //legal. A precedência aqui é feita naturalmente como i = *(&j) depois, seja p = &j, i = (*p), assim i = j.
    i = *&*&j;        //legal. Uma variável (não ponteiro) inteira recebe adequadamente um valor de variável: i = *&*(&j) (seja int *p cujo p = &j), i = *&(*p),//i = *(&j), i = *p.
    q = *p;           //ilegal. O ponteiro tende a aceitar localizações de valroes atribuídas às variáveis.
    i = (*p)++ + *q;  //

5 Determine o que será mostrado pelo seguinte programa (compile-o, execute-o e verifique se foram obtidas as respostas esperadas).

    int main() {
      int    valor;
      int   *p1;
      float  temp;
      float *p2;
      char   aux;
      char  *nome = "Ponteiros";
      char  *p3;
      int    idade;
      int    vetor[3];
      int   *p4;
      int   *p5;
    
      /* (a) */
      valor = 10; //Na variável 'valor' de tipo inteiro é guardado o valor 10
      p1 = &valor; // No ponteiro p1, que aponta pra inteiro, é guardado o endereço de 'valor'. Assim *p1 == valor
      *p1 = 20; // A variável do ponteiro p1 (*p1) recebe 20. Assim valor recebe 20.
      printf("%d \n", valor); // impresso em inteiro decimal o valor de 'valor', que é o valor de *p1, e quebra a linha
                              // imprime 20
    
      /* (b) */
      temp = 26.5; // Na variável 'temp' de tipo float é guardado o valor 26.5
      p2 = &temp; // No ponteiro p2, que aponta pra inteiro, é guardado o endereço de 'temp'. Assim *p2 == temp
      *p2 = 29.0; // A variável do ponteiro p2 (*p2) recebe 29.0. Assim 'temp' recebe 29.0.
      printf("%.1f \n", temp); // Imprime em float com uma casa decimal o valor de 'temp', que é p valor de *p, e quebra a linha
                               // Imprime 29.0
    
      /* (c) */
      p3 = &nome[0]; //p3 recebe o endereço de 'p' da cadeia de careacteres 'ponteiros'
      aux = *p3;// aux (tipo char) recebe 'p'
      printf("%c \n", aux); // Imprime 'P' e quebra a linha.
    
      /* (d) */
      p3 = &nome[4]; // ponteiro p3 recebe o endereço de 'e' de 'ponteiros'
      aux = *p3; // aux (char) guarda 'e'
      printf("%c \n", aux); // Imprime 'e' e quebra a linha
    
      /* (e) */
      p3 = nome; // p3 (ponteiro p/ char) recebe &nome[0] (nome é ponteiro p/ char). Como não tem índice, recebe o endereço da primeira "variável"(char) de valor 'P'.
      printf("%c \n", *p3); // Imprime 'P'
    
      /* (f) */
      p3 = p3 + 4; // Ponteiro p3 guarda o endereço de nome somado com 4 bytes
      printf("%c \n", *p3); // Aqui p3 é desreferenciado, então imprime o quinto caracteres de *nome localizado em &nome[4], 'e'
    
      /* (g) */
      p3--; // p3 agora guarda a localização do caratere anterior a 'e', 't'
      printf("%c \n", *p3); // desreferencia p3 e imprime 't'
    
      /* (h) */
      vetor[0] = 31; // 'vetor', de tamanho 3, guarda 31 no primeiro índice 
      vetor[1] = 45; // 'vetor' guarda 45 no seu segundo índice
      vetor[2] = 27; // 'vetor' agora guarda 27 no seu terceiro índice
      p4 = vetor; // p4 (ponteiro que aponta p/ inteiro) guarda o endereço do primeiro valor de vetor 
      idade = *p4; // 'idade' (int) guarda 31
      printf("%d \n", idade); // imprime 31.
    
      /* (i) */
      p5 = p4 + 1; // p5 (pont) guarda p4 (ponteiro) da segunda posição em diante, '&p4[1] == 45'
      idade = *p5; // 'idade' guarda p5 (com valor 45)
      printf("%d \n", idade); //Imprime 45
    
      /* (j) */
      p4 = p5 + 1; // p4 guarda p5 da segunda posição de inteiros em diante, que é justamente a terceira posição de p4.  'p4[0] = &p5[1]' | '&p5[1] == 27
      idade = *p4; // 
      printf("%d \n", idade); // imprime 27
    
      /* (l) */
      p4 = p4 - 2; // mesmo p4 guardando 27 em ''&p4[0]'', duas posições (de inteiros) atrás desse endereço existe o valor 31
      idade = *p4;
      printf("%d \n", idade); // assim imprime 31 através da variável idade.   
    
      /* (m) */
      p5 = &vetor[2] - 1; // p5 (pont) guarda o valor que está na posição anterior à terceiro do array 'vetor': 45
      printf("%d \n", *p5); // imprime 45
    
      /* (n) */
      p5++; // é incrementado uma posição a mais na posição inicial de p5
      printf("%d \n", *p5); //  Imprime 27
      return(0);
    }
    
6 Determine o que será mostrado pelo seguinte programa (compile-o, execute-o e verifique se foram obtidas as respostas esperadas).

    int main(void){
      float vet[5] = {1.1, 2.2, 3.3, 4.4, 5.5};
      float *f;
      int i;
      f = vet;
      printf("contador|valor|valor|endereco|endereco");
      for(i = 0 ; i <= 4 ; i++){
        printf("\ni = %d | ",i); 
        printf("vet[%d] = %.1f | ",i, vet[i]);
        printf("*(f + %d) = %.1f | ",i, *(f+i));
        printf("&vet[%d] = %X | ",i, &vet[i]);
        printf("(f + %d) = %X",i, f+i);
      }
    }
    
    // i = 0 | vet[0] = 1.1 | *(f + 0) = 1.1 | &vet[0] = endereço &vet[0] em hd | (f+0) = endereço de 1.1
    
    // i = 1 | vet[1] = 2.2 | *(f + 2) = 2.2 | &vet[2] = endereço &vet[2] em hd | (f+2) = endereço de 2.2
    
    // i = 2 | vet[2] = 3.3 | *(f + 3) = 3.3 | &vet[3] = endereço &vet[3] em hd | (f+3) = endereço de 3.3
    
    //...
    
    // Basicamente ensina algumas propriedades dos ponteiros. São noções primordiais sobre o armazenamento de variáveis e o acesso aos endereços
    
    
7 Assumindo que pulo[] é um vetor do tipo int, quais das seguintes expressões referenciam o valor do terceiro elemento do vetor?

    *(pulo + 2); // rasc:...representa o terceiro valor, mas n o referencia
    *(pulo + 4); //representa o quinto valor, mas n o referencia
    pulo + 4; // referencia o valor da quinta posição
    pulo + 2; // referencia o valor do terceiro elemento do vetor
    
8 Considerando a declaração int mat[4], *p, x;, quais das seguintes expressões são válidas? Justifique.
    
    p = mat + 1; // válida: vetor mat recebe um incremento de posição
    p = mat++; //inválida:  errado ...vetor mat recebe um incremento de posição
    p = ++mat; //inválida: vetor mat é incrementado a um valor que não recebe tratamento de tipo
    x = (*mat)++; //válida: errdo... o array mat está sendo tratado e desreferenciado como ponteiro
    
    
9 O que fazem os seguintes programas em C?

    int main(){
      int vet[] = {4,9,13};
      int i;
      for(i=0;i<3;i++){
        printf("%d ",*(vet+i));
      }
    }
    int main(){
      int vet[] = {4,9,13};
      int i;
      for(i=0;i<3;i++){
        printf("%X ",vet+i);
      }
    }
    
    //rascunho: o primeiro apresenta os valores de vet. o segundo, os endereçoes desses valores
    
10 Seja x um vetor de 4 elementos, declarado da forma TIPO x[4];. Suponha que depois da declaração, x esteja armazenado no endereço de memória 4092 (ou seja, o endereço de x[0]). Suponha também que na máquina seja usada uma variável do tipo char ocupa 1 byte, do tipo int ocupa 2 bytes, do tipo float ocupa 4 bytes e do tipo double ocupa 8 bytes. Quais serão os valores de x+1, x+2 e x+3 se:

    x for declarado como char?
    // x+1 = 4093, x+2 = 4094 e x+3 = 4095
    
    x for declarado como int?
    // x+1 = 4094, x+2 = 4096 e x+3 = 4098
    
    x for declarado como float?
    // x+1 = 4096, x+2 = 4100 e x+3 = 4104
    
    x for declarado como double?
    // x+1 = 4100, x+2 = 4108 e x+3 = 4116

11 Implemente um programa de computador para testar estas suposições e compare as respostas oferecidas pelo programa com as respostas que você idealizou.
    
    #include <stdio.h>

    int main ()
    {
    //redefinindo tamnhos dos tipos de dados para nova máquina
    int tam_char = sizeof(char); //continua com mesmo tamanho
    int tam_int = sizeof(int) - 2;
    int tam_float = sizeof(float); //continua com mesmo tamanho
    int tam_double = sizeof(double); //continua com mesmo tamanho


    int tam_x = 4092;

            printf("para o vetor x do tipo char: \n");
            for (int i =1; i<=3; i++)
            {
            printf("x + %d  = %d  \n", i, tam_x + tam_char*i);
            }
        printf("\n\n");
            printf("para o ovetor x do tipo int: \n");
            for (int i =1; i<=3; i++)
            {
            printf("x + %d  = %d  \n", i, tam_x + tam_int*i);
            }
        printf("\n\n");
            printf("para o vetor x do tipo float: \n");
            for (int i =1; i<=3; i++)
            {
            printf("x + %d  = %d  \n", i, tam_x + tam_float*i);
            }
        printf("\n\n");
            printf("para o vetor x do tipo double: \n");
            for (int i =1; i<=3; i++)
            {
            printf("x + %d  = %d  \n", i, tam_x + tam_double*i);
            }
    return 0;
    }

12 Suponha que as seguintes declarações tenham sido realizadas:
    
    float aloha[10], coisas[10][5], *pf, value = 2.2;
    int i=3;
     Identifique quais dos seguintes comandos é válido ou inválido:

    aloha[2] = value; //válido
    scanf("%f", &aloha); //válido
    aloha = value"; // inválido
    printf("%f", aloha); // válido
    coisas[4][4] = aloha[3]; //válido
    coisas[5] = aloha; //inválido valor indevido sendo atribuido a posição indeifinida
    pf = value; //inválido porque pf é um endereço e espera um ponteiro
    pf = aloha; //válido porque um ponteiro está recebendo um array

13 O que é um ponteiro para uma função? Pesquise na Internet referências sobre o assunto e escreva um pequeno programa exemplificando o uso deste recurso.

    Como uma função é um conjunto de instuções armazeanadas na memória da máquina, através de um ponteiro é possível acessar uma função.

    #include <stdio.h>

    //função
    int soma(int a, int b)
    {
    return a + b;
    }

    int main()
    {   int x, y, z;
    int (*p)(int, int);

    printf("Digite dois números para a soma: ");
    scanf("%d %d", &x, &y);

    p=soma; //ponteiro recebe endereço que aponta para função
    z=p(x,y);
    printf("Soma = %d\n", z);

    system("pause");
    return 0;
    }


14 Implemente em linguagem C uma função em um programa de computador que leia n valores do tipo float e os apresente em ordem crescente. Utilize alocação dinâmica de memória para realizar a tarefa.

    #include <stdio.h>
    #include <stdlib.h> //uso do malloc

    int main()
    {
    float *v, aux;
    int n;

    printf("Informe a quantidade de números: ");
    scanf("%d", &n);
    if(n>0)
    {
    v = (float*)malloc(n* sizeof(float));

    for (int i = 0; i < n; i++)
    {
        printf("%d | ", i+1);
        scanf("%f", (v+i));
    }

    for (int i = 0; i < n-1; i++)
    {
        for (int j = i+1; j < n; j++)
        {
            if (v[i] > v[j])
            {
                aux = v[i];
                v[i] = v[j];
                v[j] = aux;
            } 
        } 
    } 
    for (int i = 0; i < n; i++)
    {
        printf("--");
    }
    printf("\n");
    printf("A ordem crescente eh: \n");
    printf("\n");
    for (int i = 0; i < n; i++)
    {
        printf("%.01f ", v[i]);
    }
    printf("\n");

    free(v);// Importante
    }
    else
    printf("\nVoce digitou um numero invalido!\n\n");
    }


15 Reimplemente o programa da questão anterior utilizando a função qsort() do C. Comente o seu código, explicando o que faz cada uma das linhas.

16 Utilize a ideia do ponteiro para função pela função qsort() para implementar sua própria função de ordenação. Para isso, sua função deverá receber, entre outros argumentos, um ponteiro para a função de comparação.

17 Procure na internet mecanismos que possibilitem medir tempos de execução de rotinas computacionais. Geralmente, estas medidas são realizadas com o auxílio de funções em C que lêem a hora no sistema (sistemas Unix e Windows geralmente usam funções diferentes). Utilizando os conhecimentos que você obteve com sua pesquisa, meça os tempos de execução das implementações que você criou para os dois problemas de ordenação anteriores e compare os resultados obtidos.

18 Escreva uma função em c que escreva em um vetor a soma dos elementos correspondentes de outros dois vetores (os tamanhos dos vetores devem ser fornecidos pelo usuário). Por exemplo, se o primeiro vetor contiver os elementos 1, 3, 0 e -2, e o segundo vetor contiver os elementos 3, 5, -3 e 1, o vetor de soma terá valores resultantes iguais a 4, 8, -3 e -1. A função deve receber 4 argumentos: os nomes dos três vetores e o número de elementos presentes em cada vetor.

19 Crie uma função capaz de realizar multiplicação matricial da forma C=ABC=AB. A função deve receber 6 argumentos: os ponteiros para as matrizes A, B e C, o número de linhas e colunas de A e o número de colunas de B (assuma que o número de coluna de A é igual ao número de linhas de B). O resultado da multiplicação deve ficar armazenado em C. Crie um programa para testar sua implementação, capaz de utilizar a função de multiplicação e imprimir as três matrizes. A função criada para multiplicação não deve realizar nenhum tipo de saída de dados no terminal.

20 Pesquise na Internet sobre o uso da biblioteca libGC, que implementa um coletor de lixo em C. O processo de instalação dessa biblioteca em sistemas Windows pode ser um pouco trabalhoso. Entretanto, em sistemas Unix, a instalação é bem simples, de sorte que se recomenda a resolução desta questão em uma máquina, por exemplo, com Linux instalado. Caso seja usuário Windows e não queira instalar sistemas alternativos em seu computador, use uma ferramenta de virtualização (ex: VirtualBox) para instalar e executar o Linux sem alterar a instalação original de seu computador. Prepare um pequeno programa-exemplo demonstrando como usar a biblioteca.

21 Com base no programa-exemplo da questão anterior, proponha uma aplicação que permita comparar o desempenho das funções tradicionais de alocação/liberação de memória da linguagem c (malloc/free) com as funções de gerenciamento de memória da biblioteca que você escolheu. A aplicação deverá ser capaz de ressaltar possíveis atrasos de tempo provenientes do coletor de lixo utilizado.
