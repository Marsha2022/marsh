# марш
Лабы
# Отчет по лабораторной работе №8 по направлению  
# "Фундаментальная информатика"

Выполнил: Кудрявов Леонид Вадимович\
Группа: М8О-108Б-22\
Почта: leonid.kudryavov@mail.ru\
Преподаватель: Сахарин Никита Александрович\

## 1. Тема

Системы программирования на языке Си

## 2. Цель работы

Системы программирования на языке Си

## 3. Задание

Составить и отладить простейшую программу на языке Си

## 4. Оборудование

Процессор: intel i5 11400F
Оп: DDR4, 16gb
Память: 425gb


## 5. Программное обеспечение

Операционная система семейства UNIX, наименование Manjaro Linux, версия 5.15.65-1-MANJARO Интерпритатор команд bash, версия 5.1.16 Редактор текстов nano

## 6. Идея, метод, алгоритм решения

Написать программу и скомпилировать её.

## 7. Ход работы:


```
#include <stdio.h>
 
int main()
{
    printf("enter a number:\n 1) sum\n 2) def\n 3) mult\n 4) div\n");
    int num;
    int a;
    int b;
    int c;
    scanf("%d", &num);
    if(num == 1) {
        printf("Enter a number\n");
        scanf("%d", &a);
        scanf("%d", &b);
        c = a + b;
        printf("Answer: %d", c);
    }
    if(num == 2) {
        printf("Enter a number\n");
        scanf("%d", &a);
        scanf("%d", &b);
        c = a - b;
        printf("Answer: %d", c);
    }
    if(num == 3) {
        printf("Enter a number\n");
        scanf("%d", &a);
        scanf("%d", &b);
        c = a * b;
        printf("Answer: %d", c);
    }
    if(num == 4) {
        printf("Enter a number\n");
        scanf("%d", &a);
        scanf("%d", &b);
        if(b == 0) {
            printf("Input error!");
        }
        else {
            c = a / b;
            printf("Answer: %d", c);
        }  
    }
    if(num > 4 || num < 1) {
        printf("No operation!");
    }
    return 0;
}
```

## 8. Вывод

Были изучены методы написание простых программ на языке Си. 

