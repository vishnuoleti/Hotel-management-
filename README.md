#include <stdio.h>
#include <string.h>

struct Hotel {
    int room_no;
    char name[30];
    char address[50];
    char phone[15];
};

int main() {
    struct Hotel h[100];
    int i = 0, choice, searchRoom, found = 0;

    while (1) {
        printf("\n--- HOTEL MANAGEMENT SYSTEM ---\n");
        printf("1. Add Customer\n");
        printf("2. View All Customers\n");
        printf("3. Search Customer\n");
        printf("4. Delete Customer\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {

        case 1:
            printf("\nEnter Room Number: ");
            scanf("%d", &h[i].room_no);
            printf("Enter Name: ");
            scanf("%s", h[i].name);
            printf("Enter Address: ");
            scanf("%s", h[i].address);
            printf("Enter Phone: ");
            scanf("%s", h[i].phone);
            i++;
            printf("Customer Added Successfully!\n");
            break;

        case 2:
            printf("\n--- Customer Records ---\n");
            for (int j = 0; j < i; j++) {
                printf("\nRoom No: %d", h[j].room_no);
                printf("\nName: %s", h[j].name);
                printf("\nAddress: %s", h[j].address);
                printf("\nPhone: %s\n", h[j].phone);
            }
            break;

        case 3:
            printf("\nEnter Room Number to Search: ");
            scanf("%d", &searchRoom);
            found = 0;
            for (int j = 0; j < i; j++) {
                if (h[j].room_no == searchRoom) {
                    printf("\nCustomer Found!");
                    printf("\nName: %s", h[j].name);
                    printf("\nAddress: %s", h[j].address);
                    printf("\nPhone: %s\n", h[j].phone);
                    found = 1;
                    break;
                }
            }
            if (!found) {
                printf("\nCustomer Not Found!\n");
            }
            break;

        case 4:
            printf("\nEnter Room Number to Delete: ");
            scanf("%d", &searchRoom);
            found = 0;
            for (int j = 0; j < i; j++) {
                if (h[j].room_no == searchRoom) {
                    for (int k = j; k < i - 1; k++) {
                        h[k] = h[k + 1];
                    }
                    i--;
                    printf("Record Deleted Successfully!\n");
                    found = 1;
                    break;
                }
            }
            if (!found) {
                printf("Record Not Found!\n");
            }
            break;

        case 5:
            printf("Exiting...\n");
            return 0;

        default:
            printf("Invalid Choice! Try again.\n");
        }
    }
}
