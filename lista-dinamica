#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node* next;
} Node;

Node* criar_lista() {
    return NULL;
}

int lista_vazia(Node* head) {
    return head == NULL;
}

int obter_tamanho(Node* head) {
    int tamanho = 0;
    Node* temp = head;
    while (temp != NULL) {
        tamanho++;
        temp = temp->next;
    }
    return tamanho;
}

int obter_elemento(Node* head, int posicao) {
    if (posicao < 1) {
        printf("Posição inválida!\n");
        return -1;
    }
    Node* temp = head;
    int i = 1;
    while (temp != NULL && i < posicao) {
        temp = temp->next;
        i++;
    }
    if (temp == NULL) {
        printf("Posição fora do alcance!\n");
        return -1;
    }
    return temp->data;
}

void modificar_elemento(Node* head, int posicao, int novo_valor) {
    if (posicao < 1) {
        printf("Posição inválida!\n");
        return;
    }
    Node* temp = head;
    int i = 1;
    while (temp != NULL && i < posicao) {
        temp = temp->next;
        i++;
    }
    if (temp == NULL) {
        printf("Posição fora do alcance!\n");
        return;
    }
    temp->data = novo_valor;
}

void inserir_elemento(Node** head, int posicao, int valor) {
    if (posicao < 1 || posicao > obter_tamanho(*head) + 1) {
        printf("Posição inválida!\n");
        return;
    }

    Node* novo = (Node*)malloc(sizeof(Node));
    novo->data = valor;
    
    if (posicao == 1) {
        novo->next = *head;
        *head = novo;
    } else {
        Node* temp = *head;
        int i = 1;
        while (temp != NULL && i < posicao - 1) {
            temp = temp->next;
            i++;
        }
        novo->next = temp->next;
        temp->next = novo;
    }
}

void remover_elemento(Node** head, int posicao) {
    if (posicao < 1 || lista_vazia(*head)) {
        printf("Posição inválida ou lista vazia!\n");
        return;
    }
    
    Node* temp = *head;
    if (posicao == 1) {
        *head = temp->next;
        free(temp);
        return;
    }

    int i = 1;
    while (temp != NULL && i < posicao - 1) {
        temp = temp->next;
        i++;
    }
    
    if (temp == NULL || temp->next == NULL) {
        printf("Posição fora do alcance!\n");
        return;
    }
    
    Node* to_remove = temp->next;
    temp->next = to_remove->next;
    free(to_remove);
}

void imprimir_lista(Node* head) {
    if (lista_vazia(head)) {
        printf("Lista vazia!\n");
        return;
    }
    Node* temp = head;
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    Node* lista = criar_lista();
    
    inserir_elemento(&lista, 1, 10);
    inserir_elemento(&lista, 2, 20);
    inserir_elemento(&lista, 2, 15);
    imprimir_lista(lista);
    
    modificar_elemento(lista, 2, 25);
    imprimir_lista(lista);
    
    remover_elemento(&lista, 1);
    imprimir_lista(lista);
    
    printf("Elemento na posição 2: %d\n", obter_elemento(lista, 2));
    
    return 0;
}
