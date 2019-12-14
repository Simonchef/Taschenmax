#include <stdio.h>
#include <math.h>


int main(void){
    int lowRange= 1;
    int hightrange = 100;
    int possibleGuess = hightrange + lowRange - 1;
    int maxTurns = ceil(log(possibleGuess) / log(2)  );
    int guess;
    int player;
    int numTurns = 1;

    printf("Think of a number from %d to %d, I can guess your number within %d turns\n",lowRange, hightrange, maxTurns);

    do{
        possibleGuess = hightrange + lowRange - 1;
        guess = (int)ceil(possibleGuess / 2.0);

        printf("Is your number %d ?\n",guess);
        printf("(1) yes, you guessed my number \n");
        printf("(2) No, guess a lower number\n");
        printf("(3) No, guess a higher number\n");
        scanf("%d",&player);

        if (player == 3)
            lowRange = guess + 1;
        else if(player == 2)
            hightrange = guess - 1;
        else if(player == 1)
            break;

        numTurns++;

    } while(player != 1 && numTurns <= maxTurns);

    if(numTurns > maxTurns)
        printf("You made a mistake, you've exceeded the maximum number of turns \n");
    else
        printf("I guessed your number in %d turns! \n", numTurns);

}
