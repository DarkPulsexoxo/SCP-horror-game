# SCP-horror-game
A text-based horror game in C where you explore SCP facilities. Your sanity decreases with each encounter with multiple ending.
#include<stdio.h>
#include<stdlib.h>
int sanity = 100;

void checkSanity() {
    if(sanity <= 0) {
        printf("\n[ENDING: LOST MIND]\nYou stare into nothing... something now speaks through you.\n");
        exit(0);
    }
}
//SCP 1: The Second Listener
void scp7924() {
    int choice;
    printf("\n--- SCP-7924: The Second Listener ---\n");
    printf("A pale figure sits silently.\n");

    printf("1. Speak to it\n2. Stay silent\n3. Observe\nChoice:  ");
    scanf("%d", &choice);

    if (choice == 1) {
        printf("\nYou: 'Hello?'\n");
        printf("SCP--7924: 'Hello.' (before you finish speaking)\n");
        sanity -= 20;
        printf("It spoke before you did...\n");
    }
    else if (choice == 2) {
        printf("\nYou remain silent.\n");
        printf("It whispers anyway... in your voice.\n");
        sanity -= 25;
    }
    else {
        printf("\nIt doesnt move...\nBut you feel like it already heard you.\n");
        sanity -= 10;
    }
    checkSanity();
}

//SCP 2: The page that finishes you
void scp9031() {
    int choice;
    printf("\n--- SCP-9031: The Page That Finishes You ---\n");
    printf("1. Read Document\n2. Close it\n3. Tear Page\nChoice: ");
    scanf("%d", &choice);

    if(choice == 1) {
        printf("\nIt starts describing you...\n");
        printf("You continue reading even though you shouldnt.\n");
        sanity -=30;
    }
    else if (choice == 2) {
        printf("\nYou close it.\n");
        printf("...You feel like you already read it.\n");
        sanity -= 15;
    }
    else {
        printf("\nThe page reforms instantly.\n");
        printf("It now skips to the ending.\n");
        sanity -= 40;
    }
    checkSanity();
}

// SCP 3: The Unsent Message
void scp9142() {
    int choice;
    printf("\n--- SCP-9142: The Unsent Message ---\n");

    printf("1. Watch typing\n2. Turn off device\n3. Reply\nChoice: ");
    scanf("%d", &choice);

    if (choice == 1) {
        printf("\nThe message types your thoughts...\n");
        sanity -= 25;
    } else if (choice == 2) {
        printf("\nScreen goes black.\nThen turns back on...\nStill typing.\n");
        sanity -= 20;
    } else {
        printf("\nYou try to reply...\nBut it replies first.\n");
        sanity -= 35;
    }

    checkSanity();
}

// SCP 4: The Breathing Room
void scp8801() {
    int choice;
    printf("\n--- SCP-8801: The Breathing Room ---\n");
    printf("The walls... move slightly.\n");

    printf("1. Stay inside\n2. Leave immediately\n3. Touch wall\nChoice: ");
    scanf("%d", &choice);

    if (choice == 1) {
        printf("\nThe room breathes slower...\nmatching you.\n");
        sanity -= 20;
    } else if (choice == 2) {
        printf("\nYou leave quickly.\nYou swear the door moved closer.\n");
        sanity -= 10;
    } else {
        printf("\nThe wall pulses.\nIt feels... alive.\n");
        sanity -= 30;
    }

    checkSanity();
}

// SCP 5: The Shadow That Waits
void scp9902() {
    int choice;
    printf("\n--- SCP-9902: The Shadow That Waits ---\n");
    printf("There is a shadow behind you.\nIt does not move.\n");

    printf("1. Turn around\n2. Ignore it\n3. Walk forward\nChoice: ");
    scanf("%d", &choice);

    if (choice == 1) {
        printf("\nYou turn.\n\nNothing.\n\nSanity drops anyway.\n");
        sanity -= 25;
    } else if (choice == 2) {
        printf("\nIt gets closer.\nYou don't look.\n");
        sanity -= 20;
    } else {
        printf("\nIt follows.\nExactly one step behind.\n");
        sanity -= 30;
    }

    checkSanity();
}

int main() {
    char name[50];
    int room;

    printf("Enter your name, Researcher: ");
    scanf("%s", name);

    printf("\nWelcome, Dr. %s.\n", name);
    printf("Sanity Level: %d\n", sanity);

    while (1) {
        printf("\nChoose SCP to interact with:\n");
        printf("1. SCP-7924\n2. SCP-9031\n3. SCP-9142\n4. SCP-8801\n5. SCP-9902\n6. Exit\nChoice: ");
        scanf("%d", &room);

        switch (room) {
            case 1: scp7924(); break;
            case 2: scp9031(); break;
            case 3: scp9142(); break;
            case 4: scp8801(); break;
            case 5: scp9902(); break;
            case 6:
                printf("\n[ENDING: ESCAPE]\nYou leave the facility...\nBut something leaves with you.\n");
                return 0;
            default:
                printf("Invalid choice.\n");
        }

        printf("\nCurrent Sanity: %d\n", sanity);

        if (sanity < 40) {
            printf("\n...You feel watched.\n");
        }
    }

    return 0;
}
