# Poker Hands

I'm going to walk you through my assignment on poker hands in C and improvements I made.


## About Poker Hands
![image](https://github.com/user-attachments/assets/59e32163-6247-4d29-acca-7b6f7d60f840)

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
    int r1, r2, r3, r4, r5;
    char s1, s2, s3, s4, s5;
    int a=0, b=0, c=0, d=0, e=0, f=0, g=0, h=0, i=0, j=0;
    scanf("%d %c", &r1, &s1);
    scanf("%d %c", &r2, &s2);
    scanf("%d %c", &r3, &s3);
    scanf("%d %c", &r4, &s4);
    scanf("%d %c", &r5, &s5);

    if (r1==r2) {a=1;}
    if (r1==r3) {b=1;}
    if (r1==r4) {c=1;}
    if (r1==r5) {d=1;}
    if (r2==r3) {e=1;}
    if (r2==r4) {f=1;}
    if (r2==r5) {g=1;}
    if (r3==r4) {h=1;}
    if (r3==r5) {i=1;}
    if (r4==r5) {j=1;} 
    
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
    } else {printf("No combination");}

    
    return 0;
}
```

Here we don't use any library except for the standard input/output. 
```
#include <stdio.h>
```

I defined integers r1 to r5 and characters s1 to s5 for each card's rank and suit. 
```
int r1, r2, r3, r4, r5;
char s1, s2, s3, s4, s5;
```

I initialized integers a to j as 0. Here a to j is to symbolize connection between any two card's rank. It will make sense later.
```
int a=0, b=0, c=0, d=0, e=0, f=0, g=0, h=0, i=0, j=0;
```

Pretty basic receiving input of an integer and a character.
```
scanf("%d %c", &r1, &s1);
scanf("%d %c", &r2, &s2);
scanf("%d %c", &r3, &s3);
scanf("%d %c", &r4, &s4);
scanf("%d %c", &r5, &s5);
```

This is the connection I meant. Because any card from any position could be the same, so rather than checking every possibility of a combination and having an if else nightmare, I made a "boolean" variable for every connection possible between 2 cards. If 1st and 2nd card's rank, then a is true (or 1), etc. 
```
    if (r1==r2) {a=1;}
    if (r1==r3) {b=1;}
    if (r1==r4) {c=1;}
    if (r1==r5) {d=1;}
    if (r2==r3) {e=1;}
    if (r2==r4) {f=1;}
    if (r2==r5) {g=1;}
    if (r3==r4) {h=1;}
    if (r3==r5) {i=1;}
    if (r4==r5) {j=1;}
```

For a one pair, the sum of a to j will be 1, because only 1 combination is true.
```
if (a+b+c+d+e+f+g+h+i+j==1) {
printf("One Pair"); }
```

For a two pair, the sum of a to j will be 2, because there will be 2 combinations. For example, a and j is true means 1st & 2nd card is a pair, so is 4th & 5th.
```
if (a+b+c+d+e+f+g+h+i+j==2) {
printf("Two Pair"); }
```

For a three of a kind, the sum of a to j will be 3, because for 3 cards to be the same rank, that must mean 1st & 2nd card is a pair, so is 2nd & 3rd and 1st & 3rd.
```
if (a+b+c+d+e+f+g+h+i+j==3) {
printf("Three of a Kind");
```

For a four of a kind, the sum of a to j will be 6, because for 4 cards to be the same rank, there <sub>4</sub>C<sub>2</sub> = 6. 
```
if (a+b+c+d+e+f+g+h+i+j==6) {
printf("Four of a Kind");
```

For a full house, the sum of a to j will be 4, because a full house consists of a pair (1) and a three of a kind (3).
```
if (a+b+c+d+e+f+g+h+i+j==4) {
printf("Full House");
```

For a straight, I just check if every card's suuit is the same.
```
if (s1==s2&&s2==s3&&s3==s4&&s4==s5) {
printf("Straight");
```

And lastly, we order them from highest ranking (which is Four of a Kind) to No combination for the if-else chain.
```
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
    } else {printf("No combination");}
```


## Improvements

### Clean up
Simplest improvent that can be done is to clean up the original code. By rearranging the code for better readability and intoducing sum variable for simplicity.

```
#include <stdio.h>
int main() {
    int r1, r2, r3, r4, r5;
    char s1, s2, s3, s4, s5;

    scanf("%d %c", &r1, &s1);
    scanf("%d %c", &r2, &s2);
    scanf("%d %c", &r3, &s3);
    scanf("%d %c", &r4, &s4);
    scanf("%d %c", &r5, &s5);

    int a=0, b=0, c=0, d=0, e=0, f=0, g=0, h=0, i=0, j=0;
    if (r1==r2) a=1;
    if (r1==r3) b=1;
    if (r1==r4) c=1;
    if (r1==r5) d=1;
    if (r2==r3) e=1;
    if (r2==r4) f=1;
    if (r2==r5) g=1;
    if (r3==r4) h=1;
    if (r3==r5) i=1;
    if (r4==r5) j=1;
    int sum = a+b+c+d+e+f+g+h+i+j;
    
    if (sum == 6) printf("Four of a Kind"); 
    else if (sum == 4) printf("Full House"); 
    else if (s1==s2 && s2==s3 && s3==s4 && s4==s5) printf("Flush");
    else if (sum == 3) printf("Three of a Kind"); 
    else if (sum == 2) printf("Two Pair"); 
    else if (sum == 1) printf("One Pair"); 
    else printf("No combination");

    return 0;
}
```


