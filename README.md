#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LINE_LENGTH 1000

int main() {
    char filename[100];
    char search_string[100];
    char line[MAX_LINE_LENGTH];
    FILE *file;

    printf("Enter the name of the file: ");
    scanf("%s", filename);

    printf("Enter the search string: ");
    scanf("%s", search_string);

    file = fopen(filename, "r");
    if (file == NULL) {
        printf("Error: Unable to open file %s.\n", filename);
        return 1;
    }

    while (fgets(line, MAX_LINE_LENGTH, file) != NULL) {
        if (strstr(line, search_string) != NULL) {
            printf("%s", line);
        }
    }

    fclose(file);

    return 0;
}
