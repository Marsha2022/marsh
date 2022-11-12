# Отчет по лабораторной работе №9 по направлению 
# "Фундаментальная информатика"

Выполнил: Кудрявов Леонид Вадимович\
Группа: М8О-108Б-22\
Почта: leonid.kudryavov@mail.ru\
Преподаватель: Сахарин Никита Александрович\

## 1. Тема

Системы программирования на языке Си

## 2. Цель работы

Составление и отрладка простейших программ на языке Си интеративного характера с целочисленными рекурсивными соотношениями.

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
 
int main(void)
{
    int sign(int value) {
        if (value<0){
            return -1;
            } else if (value > 0)
        {
            return 1;
        } else if (value == 0)
        {
            return 0;
        }
    }
    
    int abs(int value) {
        if (value < 0)
        {
            return -value;
        } else {
            return value;
        }
    }
    
    int mod (int value, int moder){
        if(moder < 0)
            return mod(value, -moder); 
        int ret = value % moder;
        if(ret < 0)
            ret+=moder;
        return ret;
    }
    
    int max(int v1, int v2) {
        if (v1 > v2){
            return v1;
        } else {
            return v2;
        }
    }   
    int min(int v1, int v2) {
        if (v1 < v2){
            return v1;
        } else {
            return v2;
        }
    }
 
    int fi(int a, int b, int c, int d){
        return ( mod((a + b),30)/(mod(abs(c),5)+1) + mod((a + b),30)/(mod(abs(c),5)+1));
    }
 
    int fj(int a, int b, int c, int d){
        return ( mod(max(d*a,(d + 1)*b),25) - abs(b - c)/10);
    }
 
    int fl(int a, int b, int c, int d){
        return( abs(b - c)/10 + min(mod((a + c),20),mod((b * d),20)) - 10 );
    }





 
    int i;
    int I;
    int j;
    i=13;
    I=-4;
    j=-9;





 
    int d1, d2;
    int m = 0;
    for (int k = 0; k < 50; ++k)
    {   
        int tmpi, tmpj, tmpl;
        d1 = (i+10)*(i+10)+(j+10)*(j+10);
        d2 = (i+20)*(i+20)+(j+20)*(j+20);
        if ((d1<=100) && (d2<=400)){
            printf ("The point hit the intersection of the circles in the values ");
            printf("%i", i);
            printf(" ");
            printf("%i", j);
            printf(" ");
            printf("on ");
            printf("%i", m);
            printf(" iterations");
 
            break;
        } else{
            tmpi = fi(i, j, I, k);
            tmpj = fj(i, j, I, k);
            tmpl = fl(i, j, I, k);
            i = tmpi;
            j = tmpj;
            I = tmpl;
            m+=1;
        }
        
    }
    if (m == 50){
        puts ("The point did not fall into the intersection of the circles");
    }
    
    
    return 0;
}

```

## 8. Вывод

Были изучены методы написание простых программ на языке Си. 
