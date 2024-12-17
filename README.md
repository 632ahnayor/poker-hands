# Poker Hands

I'm going to walk you through my assignment on poker hands in C and improvements I made.


## About Poker Hands
![image](https://github.com/user-attachments/assets/59e32163-6247-4d29-acca-7b6f7d60f840 | width=100)

Here's a handy diagram for a quick overview.


Quick Tips: 

Suit is a card's group. Think of Hearts, Spades, Clubs, and Diamonds.

Rank is a card's value. From highest: A, K, Q, J, 10-2.

Hand is the cards the player is holding. In poker, a typical hand consists of five cards.


- A **High Card** is any card with letter ranks (A, K, Q, J). 
- A **Pair** is when two cards have the same rank, regardless of suit.


## My Assignment

My Assignment was to receive 5 lines of integer R and character S for 5 cards, with R indicating a card's rank, and S a card's suit. 
Because of the letter ranks, we were to substitute it with 11 for Jacks, 12 for Queens, 13 for Kings, and 1 for Aces.
The assignment only asked to detect One Pair, Two Pair, Three of a Kind, Four of a Kind, Full House, and Flush combination from the inputted hand. 
We were to output the detected combination (or No combination, if no combination detected at all).
Another thing is we weren't allowed to use arrays yet.

So, Here is my code.

```
#include <stdio.h>
int main() {
    int n1, n2, n3, n4, n5;
    char s1, s2, s3, s4, s5;
    int a=0, b=0, c=0, d=0, e=0, f=0, g=0, h=0, i=0, j=0;
    scanf("%d %c", &n1, &s1);
    scanf("%d %c", &n2, &s2);
    scanf("%d %c", &n3, &s3);
    scanf("%d %c", &n4, &s4);
    scanf("%d %c", &n5, &s5);

    if (n1==n2) {a=1;}
    if (n1==n3) {b=1;}
    if (n1==n4) {c=1;}
    if (n1==n5) {d=1;}
    if (n2==n3) {e=1;}
    if (n2==n4) {f=1;}
    if (n2==n5) {g=1;}
    if (n3==n4) {h=1;}
    if (n3==n5) {i=1;}
    if (n4==n5) {j=1;} 
    
    if (a+b+c+d+e+f+g+h+i+j == 6) {
        printf("Four of a Kind"); 
    } else if (a+b+c+d+e+f+g+h+i+j == 4) {
        printf("Full House"); 
    } else if (s1==s2&&s2==s3&&s3==s4&&s4==s5) {
        printf("Flush");
    } else if (a+b+c+d+e+f+g+h+i+j==3) {
        printf("Three of a Kind"); 
    } else if (a+b+c+d+e+f+g+h+i+j==2) {
        printf("Two Pair"); 
    } else if (a+b+c+d+e+f+g+h+i+j==1) {
        printf("One Pair"); 
    } else {printf("Tidak ada kombinasi khusus");}

    
    return 0;
}
```


## Improvements

