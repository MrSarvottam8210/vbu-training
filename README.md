#include <stdio.h>
#include <stdlib.h>

struct student {
    int roll;
    char name[50];
    float marks;
};

int main() {
    struct student s[100];
    int choice, count = 0, i, roll, found;

    while (1) {
        printf("\n===== Student Management System =====\n");
        printf("1. Add Student\n");
        printf("2. Display Students\n");
        printf("3. Search Student\n");
        printf("4. Delete Student\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            printf("Enter Roll No: ");
            scanf("%d", &s[count].roll);
            printf("Enter Name: ");
            scanf("%s", s[count].name);
            printf("Enter Marks: ");
            scanf("%f", &s[count].marks);
            count++;
            printf("Student Added Successfully!\n");
            break;

        case 2:
            if (count == 0) {
                printf("No Records Found!\n");
            } else {
                for (i = 0; i < count; i++) {
                    printf("\nRoll: %d", s[i].roll);
                    printf("\nName: %s", s[i].name);
                    printf("\nMarks: %.2f\n", s[i].marks);
                }
            }
            break;

        case 3:
            found = 0;
            printf("Enter Roll No to Search: ");
            scanf("%d", &roll);
            for (i = 0; i < count; i++) {
                if (s[i].roll == roll) {
                    printf("\nRecord Found!");
                    printf("\nName: %s", s[i].name);
                    printf("\nMarks: %.2f\n", s[i].marks);
                    found = 1;
                    break;
                }
            }
            if (!found)
                printf("Student Not Found!\n");
            break;

        case 4:
            found = 0;
            printf("Enter Roll No to Delete: ");
            scanf("%d", &roll);
            for (i = 0; i < count; i++) {
                if (s[i].roll == roll) {
                    for (int j = i; j < count - 1; j++) {
                        s[j] = s[j + 1];
                    }
                    count--;
                    found = 1;
                    printf("Student Deleted Successfully!\n");
                    break;
                }
            }
            if (!found)
                printf("Student Not Found!\n");
            break;

        case 5:
            printf("Exiting Program...\n");
            exit(0);

        default:
            printf("Invalid Choice!\n");
        }
    }
    return 0;
}
