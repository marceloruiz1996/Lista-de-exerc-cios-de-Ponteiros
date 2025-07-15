#include <stdio.h>
#include <string.h>

void ex1() {
    int a = 10, b = 20;
    if (&a > &b)
        printf("Maior endereco: %p\n", (void*)&a);
    else
        printf("Maior endereco: %p\n", (void*)&b);
}

void ex2() {
    int a, b;
    printf("Digite dois inteiros: ");
    scanf("%d %d", &a, &b);
    if (&a > &b)
        printf("Conteudo no maior endereco: %d\n", a);
    else
        printf("Conteudo no maior endereco: %d\n", b);
}

void ex3() {
    float v[10];
    for (int i = 0; i < 10; i++)
        printf("Endereco de v[%d]: %p\n", i, (void*)&v[i]);
}

void ex4() {
    float m[3][3];
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            printf("Endereco de m[%d][%d]: %p\n", i, j, (void*)&m[i][j]);
}

void ex5() {
    int v[5];
    int *p = v;
    for (int i = 0; i < 5; i++)
        scanf("%d", p + i);
    for (int i = 0; i < 5; i++)
        printf("%d ", 2 * (*(p + i)));
    printf("\n");
}

void ex6() {
    int v[5];
    int *p = v;
    for (int i = 0; i < 5; i++)
        scanf("%d", p + i);
    for (int i = 0; i < 5; i++)
        if (*(p + i) % 2 == 0)
            printf("Endereco de valor par %d: %p\n", *(p + i), (void*)(p + i));
}

int ocorre(char *str, char *sub) {
    for (; *str; str++) {
        char *s = str, *t = sub;
        while (*s && *t && *s == *t) {
            s++;
            t++;
        }
        if (!*t) return 1;
    }
    return 0;
}

void ex7() {
    char str[100], sub[100];
    printf("Digite a string principal: ");
    scanf("%s", str);
    printf("Digite a substring: ");
    scanf("%s", sub);
    if (ocorre(str, sub))
        printf("A substring ocorre na string.\n");
    else
        printf("A substring nao ocorre na string.\n");
}

void preencher(int *v, int val, int tamanho) {
    int *fim = v + tamanho;
    while (v < fim) {
        *v = val;
        v++;
    }
}

void ex8() {
    int v[5];
    int val;
    printf("Digite o valor para preencher: ");
    scanf("%d", &val);
    preencher(v, val, 5);
    for (int i = 0; i < 5; i++)
        printf("%d ", v[i]);
    printf("\n");
}

void imprimir(int *v, int tamanho) {
    int *fim = v + tamanho;
    while (v < fim) {
        printf("%d ", *v);
        v++;
    }
    printf("\n");
}

void ex9() {
    int v[5];
    for (int i = 0; i < 5; i++)
        scanf("%d", &v[i]);
    imprimir(v, 5);
}

void ex10() {
    int a, *b, **c, ***d;
    b = &a;
    c = &b;
    d = &c;
    printf("Digite um valor para a: ");
    scanf("%d", &a);
    printf("Dobro: %d\n", 2 * (*b));
    printf("Triplo: %d\n", 3 * (**c));
    printf("Quadruplo: %d\n", 4 * (***d));
}

int main() {
    int opcao;
    do {
        printf("\nMenu de Exercicios\n");
        printf("1 - Exercicio 1\n");
        printf("2 - Exercicio 2\n");
        printf("3 - Exercicio 3\n");
        printf("4 - Exercicio 4\n");
        printf("5 - Exercicio 5\n");
        printf("6 - Exercicio 6\n");
        printf("7 - Exercicio 7\n");
        printf("8 - Exercicio 8\n");
        printf("9 - Exercicio 9\n");
        printf("10 - Exercicio 10\n");
        printf("0 - Sair\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        switch (opcao) {
            case 1: ex1(); break;
            case 2: ex2(); break;
            case 3: ex3(); break;
            case 4: ex4(); break;
            case 5: ex5(); break;
            case 6: ex6(); break;
            case 7: ex7(); break;
            case 8: ex8(); break;
            case 9: ex9(); break;
            case 10: ex10(); break;
        }
    } while (opcao != 0);
    return 0;
}
