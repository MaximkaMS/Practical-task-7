# Practical-task-7
#include <stdio.h>
#include <math.h>

int calculateIntersectionPoints(int x1, int y1, int r1, int x2, int y2, int r2) {
    // Відстань між центрами кола
    double distance = sqrt(pow(x2 - x1, 2) + pow(y2 - y1, 2));

    // Радіуси кола не мають спільних точок перетину
    if (distance > r1 + r2) {
        return 0;
    }

    // Одне коло повністю міститься всередині іншого кола
    if (distance < fabs(r1 - r2)) {
        return 0;
    }

    // Радіуси кола однакові і центри збігаються
    if (distance == 0 && r1 == r2) {
        return -1;
    }

    // Визначаємо кількість точок перетину
    if (distance == r1 + r2 || distance == fabs(r1 - r2)) {
        return 1;
    }

    // Два точки перетину
    return 2;
}

int main() {
    int x1, y1, r1, x2, y2, r2;

    printf("Введіть координати та радіус першого кола (x1, y1, r1): ");
    scanf("%d %d %d", &x1, &y1, &r1);

    printf("Введіть координати та радіус другого кола (x2, y2, r2): ");
    scanf("%d %d %d", &x2, &y2, &r2);

    // Обчислюємо кількість точок перетину
    int intersectionPoints = calculateIntersectionPoints(x1, y1, r1, x2, y2, r2);

    printf("Кількість точок перетину: %d\n", intersectionPoints);

    return 0;
}
