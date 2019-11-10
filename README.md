1. 리스트(dynamic array)

1.1 리스트의 종류

1.1.1  single linked list
노드당 다음노드를 알려주는 링크가 1개
한방향으로밖에 이동 못함
사진

1.1.2 doubly linked list
노드당 다음 노드를 알려주는 링크가 2개
양방향으로 움직임이 가능
사진

1.1.3 circular linked list
마지막 노드가 처음 노드를 가르켜서 계속 순환할 수 있음 
사진

1.2 리스트의 예제
#include <stdio.h>
#include <stdlib.h>
typedef struct list {
 int d;
 struct list* p;
} LIST;
LIST* root = NULL;
LIST* last = NULL;
void AddList(int a){
 LIST* r = (LIST*)malloc(sizeof(LIST));
 r->d = a;
 r->p = NULL;
 if(root==NULL) root = r;
 else           last->p = r;
 last = r;
}
int main(void){
 AddList(35);
 AddList(40);
 AddList(45);
 while(root){
  printf("%d\n", root->d);
  root = root->p;
 }
}

1.3 리스트와 배열의 차이
인풋사이즈를 모를때 메모리 할당 효율 배열 < 리스트

데이터 저장 값  배열 < 리스트

중간 데이터 추가, 삭제 효율성 배열 < 리스트
