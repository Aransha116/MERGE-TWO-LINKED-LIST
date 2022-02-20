# MERGE-TWO-LINKED-LIST
MERGE OF TWO SORTED LINKED LIST
#include<iostream>
using namespace std;
 
  class linked {
      public:
     int data;
    linked *next ;
    linked(int val){
        data = val;
        next = NULL;
    }
 };
 void createll(linked* &head,int val){
     linked* n = new linked(val);
     if(head==NULL){
         head = n;
         return;
     }
     linked *temp = head;
     while (temp->next!=NULL){
         temp = temp->next;
     }
     temp->next = n;
 }
 void printll(linked *head)
 {

     linked *temp = head;
     while(temp!=NULL){
         cout << temp->data << " ";
         temp = temp->next;
     }
     cout << endl;
 }
 linked* merge(linked* &head1,linked* &head2){
     linked *ptr1 = head1;
     linked *ptr2 = head2;
     linked *firstnode = new linked(-1);
     linked *ptr3 = firstnode;
     while(ptr1!=NULL && ptr2!=NULL){
         if(ptr1->data<ptr2->data){
             ptr3->next = ptr1;
             ptr1 = ptr1->next;
         }
         else{
             ptr3->next = ptr2;
         ptr2 = ptr2->next;
         }
          ptr3 = ptr3->next;
     }
     while(ptr1!=NULL){
         ptr3->next = ptr1;
         ptr1 = ptr1->next;
         ptr3 = ptr3->next;
     }
     while(ptr2!=NULL){
         ptr3->next = ptr1;
         ptr2 = ptr2->next;
         ptr3 = ptr3->next;
     }
     return firstnode->next;
 }
 int main(){
     linked *head1 = NULL;
     linked *head2 = NULL;
     int arr1[] = {3, 4, 7, 8};
     int arr2[] = {1, 2, 5, 9};
     for (int i = 0; i < 4;i++){
         createll(head1, arr1[i]);
     }
     for (int i = 0; i < 3;i++){
         createll(head2, arr2[i]);
     }
         
     printll(head1);
     printll(head2);
     linked* newHead = merge(head1, head2);
     printll(newHead);

     return 0;
 }
