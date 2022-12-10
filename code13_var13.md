```
#include <stdio.h>
#include <stdbool.h>
#include <assert.h>
#include <ctype.h>

#define N 9
#define MAX 499999999

typedef unsigned uint;

uint get_reverse_code(uint n, bool is_positive) {
  assert(n <= MAX);
  if (is_positive) return n;

  uint result = 0;
  for (int i = 0;i < N;i++) {
    result *= 10;
    uint k = n;
    for (int j = 0;j < N - i - 1;j++) k /= 10;
    result += 9 - (k % 10);
  }

  return result;
}

void test(uint n, bool is_positive, uint result) {
  assert(get_reverse_code(n, is_positive) == result);
}

void run_tests() {
  test(0, true, 0);
  test(0, false, 999999999);

  test(499999999, true, 499999999);
  test(499999999, false, 500000000);

  test(123456789, true, 123456789);
  test(123456789, false, 876543210);
  test(12345678, false, 987654321);
}

typedef enum {
  LOOK,
  READ
} State;

int main() {
  run_tests();

  State s = LOOK;
  uint num = 0;
  bool is_negative = false;

  char prev = '\0';
  for (char c = getchar();c != EOF;c = getchar()) {
    switch (s) {
      case LOOK:
        if (isdigit(c)) {
          s = READ;
          num = c - '0';
          is_negative = prev == '-';
        }
        break;
      case READ:
        if (isdigit(c)) {
          num *= 10;
          num += c - '0';
        } else {
          s = LOOK;
         
          uint reverse_code = get_reverse_code(num, !is_negative);
          printf("%u\n", reverse_code);

          is_negative = false;
          num = 0;
        }
        break;
    }
    prev = c;
  }

  if (s == READ) {
    uint reverse_code = get_reverse_code(num, !is_negative);
    printf("%u\n", reverse_code);
  }

  return 0;
}
```
