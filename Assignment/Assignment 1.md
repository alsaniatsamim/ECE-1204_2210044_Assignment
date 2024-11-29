#include <stdio.h>
int main()
{
    int choice;
    float balance = 0, amount;

    while (1)
    {
        printf("1. Deposit\n2. Withdraw\n3. Balance Inquiry\n4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 4)
        {
            break;
        }

        switch (choice)
        {

        case 1:
            printf("Enter amount to deposit: ");
            scanf("%f", &amount);
            if (amount > 0)
            {
                balance += amount;
                printf("Deposit successful\n");
            }
            else
            {
                printf("Error Deposit\n");
            }

            break;

        case 2:
            printf("Enter amount to withdraw:\n");
            scanf("%f", &amount);
            if (amount <= balance && amount > 0)
            {
                balance -= amount;
                printf("Withdraw Success\n");
            }
            else
            {
                printf("Error Withdraw\n");
            }

            break;

        case 3:
            printf("Balance: %.2f\n", balance);
            break;

        default:
            printf("Invalid Choice\n");
        }
    }
}

Output:
![image](https://github.com/user-attachments/assets/57e605ca-0f64-478c-8f94-b2ea29cdc7c8)
