```
#include <stdio.h>
#include <stdbool.h>
#include <assert.h>
#include <ctype.h>

#define N 31

typedef enum {
  ZERO,
  NUM
} State;

int main() {

  State s = ZERO;

  int zeros = 0;
  int num = 0;

  for (int c = getchar();c != EOF;c = getchar()) {
    switch (s) {
      case ZERO:
        if (c == '0') {
          ++zeros;
        } else {
          num += c - '0';
          s = NUM;
        }
        break;
      case NUM:
        if (!isdigit(c)) continue;
        num *= 10;
        num += c - '0';
        break;
    }
  }

  if (num <= 1) printf("%d\n", num);

  char bin[N] = { 0 };

  for (int i = N - 1;i >= 0;i--) {
    int pow = 1 << i;
    if (num >= pow) {
      num -= pow;
      bin[N - i - 1] = '1';
    } else {
      bin[N - i - 1] = '0';
    }
  }

  int middle = -1;
  int result = 0;

  for (int i = 0;i < N;i++) {
    if (middle == -1 && bin[i] == '1') {
      middle = (N + i) / 2;
    }
    if (i == middle) {
      for (int j = 0;j < zeros;j++) result <<= 1;
    }
    if (middle != -1) {
      result <<= 1;
      result += bin[i] - '0';
    }
  }
  printf("Result: %d\n", result);
  return 0;
}
```
