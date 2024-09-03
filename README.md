#include <stdio.h>
int token = 0, tokens[50], payment_counter = 0;
int main_page()
{
    printf("\nQuality food...Serves good.(^_^)\n");

    printf("1.New Order\n");
    printf("2.Bill Payment\n");
    printf("3.Exit \n");

    printf("\nEnter Your Choice:");
    int choice;
    scanf("%d", &choice);
    return choice;
}
void Bill_show(int id[], int q[], int counter)
{
    int n;
    int i, sum = 0;
    int costs[8] = {120, 40, 70, 90, 65, 230, 25, 25};

    char items[8][16] = {"Beef Burger", "Hot Dog", "Donuts", "French Fries", "Ice Cream", "Sweets", "Coca-Cola", "Mirinda"};
    printf("\nYour Bill:\n      Item(s)     Quantity   Cost\n");

    for (i = 0; i < counter; i++)
    {
        printf("%d. %s _%d piece(s) _ %d\n", i + 1, items[id[i] - 1], q[i], q[i] * costs[id[i] - 1]);
        sum = sum + (costs[id[i] - 1] * q[i]);
    }

    printf("\nTotal = %d\n", sum);
    token++;
    tokens[token] = sum;
    printf("\tYour token number is %d. \nUse this token while paying the bill.\nEnter 1 to give another order\n", token);
    printf("Enter 2 to go to the main menu>\nEnter your choice: ");
    scanf("%d", &n);

    if (n == 1)
    {
        menu_order();
    }
    else if (n == 2)
    {
        main();
    }
}

int menu_order()
{
    int id[8], decision, q[8], Bill[8], counter = 0;
d:

    printf("\nFOOD MENU\n\n");

    printf("**\n");
    printf("1.Burger .............................120/-\t \n");
    printf("2.Hot Dog ............................40/-\n");
    printf("3.Donuts .............................70/-\t \n");
    printf("4.French Fries .......................90/-\t \n");
    printf("5.Ice Cream ..........................65/-\t  \n");
    printf("6.Sweets .............................230/-\t \n");
    printf("7.Coca-Cola ..........................25/-\n");
    printf("8.Mirinda   ..........................25/-\n");
    printf("**\n");

    printf("Order your dish: (Enter 0 to finish order)\n");
    for (;;)
    {
        counter++;
        printf("Enter Food ID: ");
        scanf("%d", &id[counter - 1]);
        if (id[counter - 1] == 0)
        {
            break;
        }
        printf("Enter Quantity: ");
        scanf("%d", &q[counter - 1]);
    }

    printf("\nThanks for your order.\n We are getting ready the dishes.Until then, have some selfies with friends.");
    printf("Enjoy!!!!\n\nEnter 1 to check your bill\n Enter 2 to check main menu\n\n Enter your choice: ");
    scanf("%d", &decision);

    counter--;
    if (decision == 1)
    {
        Bill_show(id, q, counter);
    }
    else if (decision == 2)
    {
        goto d;
    }
    else if (decision == 3)
    {
        main();
    }
}

void Bill_Payment()
{
    int k, i, cash, changer, n;
d:
    payment_counter++;

    printf("\nEnter your token number: ");
    scanf("%d", &k);
    printf("\nYour Total Bill is = %d", tokens[k]);
work:
    printf("\nPay your bill: ");
    scanf("%d", &cash);
    if (cash != tokens[k])
    {
        printf("You have to pay ", cash - tokens[k]);
    }

    printf("\nThanks for your payment. Have a great day!!!!\n");
    printf("\n<Enter 1 to pay another bill.>\n<Enter 2 to go back main menu>\nEnter your choice: \t");
    scanf("%d", &n);
    if (n == 2)
    {
        main();
    }
    else if (n == 1)
        goto d;
}
int main()
{
    printf("###################################\n");
    printf("###################################\n");
    printf("##  Welcome to Akshar's Cafe ^_^ ##\n");
    printf("###################################\n");
    printf("###################################\n");
    int k;
    k = main_page();
    if (k == 1)
    {
        menu_order();
    }
    else if (k == 2)
    {
        Bill_Payment();
    }
    else
    {
        printf("\nDipali's Cafe\n\n");
        printf("This session order recieved : %d\n", token);
        printf("This session bill paid      : %d\n\n", payment_counter);
        if (payment_counter < token)
        {
            printf("No. of payment remaining: %d\n", token - payment_counter);
        }
        printf("\nThank You..!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!\n");
    }
    return 0;
}
