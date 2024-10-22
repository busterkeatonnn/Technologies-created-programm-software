# Технологии разработки программного обеспечения
### Ефимов Е.А. ПИМО-01-24

### Практическая работа №5
1. **Проверка на простоту**  
   Напишите функцию, которая проверяет, является ли переданное число простым. Ваша программа должна использовать циклы для проверки делителей, и если число не является простым, выводить первый найденный делитель.
```go
package main

import "fmt"

// isPrime проверяет, является ли число n простым
func isPrime(n int) (bool, int) {
 if n <= 1 {
  return false, -1 // Числа <= 1 не являются простыми
 }

 // Проверяем делители от 2 до sqrt(n)
 for i := 2; i*i <= n; i++ {
  if n%i == 0 {
   return false, i // Если нашли делитель, возвращаем false и делитель
  }
 }
 return true, -1 // Если делителей не нашли, возвращаем true
}

func main() {
 var number int
 fmt.Print("Введите число: ")
 fmt.Scan(&number)
 isPrimeNum, divisor := isPrime(number)

 if isPrimeNum {
  fmt.Printf("%d является простым числом", number)
 } else {
  fmt.Printf("%d не является простым числом. Первый найденный делитель: %d", number, divisor)
 }
}
```

2. **Наибольший общий делитель (НОД)**  
   Напишите программу для нахождения наибольшего общего делителя (НОД) двух чисел с использованием алгоритма Евклида. Используйте цикл `for` для вычислений.
```go
package main

import "fmt"

func gcd(a int, b int) int {
 for b != 0 {
  a, b = b, a%b
 }
 return a
}

func main() {
 var num1, num2 int

 fmt.Print("Введите первое число: ")
 fmt.Scan(&num1)
 fmt.Print("Введите второе число: ")
 fmt.Scan(&num2)

 result := gcd(num1, num2)
 fmt.Printf("Наибольший общий делитель чисел %d и %d равен %d", num1, num2, result)
}
```

3. **Сортировка пузырьком**  
   Реализуйте сортировку пузырьком для списка целых чисел. Программа должна выполнять сортировку на месте и выводить каждый шаг изменения массива.
```go
package main

import "fmt"

func bubbleSort(arr []int) {
 n := len(arr)
 for i := 0; i < n; i++ {
  for j := 0; j < n-i-1; j++ {
   if arr[j] > arr[j+1] {
    // Меняем местами если элемент больше следующего
    arr[j], arr[j+1] = arr[j+1], arr[j]
    // Выводим состояние массива на каждом шаге
    fmt.Println(arr)
   }
  }
 }
}

func main() {
 // Инициализируем массив целых чисел
 arr := []int{64, 34, 25, 12, 22, 11, 90}

 fmt.Println("Исходный массив:", arr)
 bubbleSort(arr)
 fmt.Println("Отсортированный массив:", arr)
}

```

4. **Таблица умножения в формате матрицы**  
   Напишите программу, которая выводит таблицу умножения в формате матрицы 10x10. Используйте циклы для генерации строк и столбцов.
```go
package main

import "fmt"

func main() {
 // Задаем размеры матрицы
 const size = 10

 // Проходим по строкам
 for i := 1; i <= size; i++ {
  // Проходим по столбцам
  for j := 1; j <= size; j++ {
   // Вычисляем произведение и формируем строку
   fmt.Printf("%d*%d=%d | ", j, i, j*i)
  }
  // Переходим на новую строку после вывода всех столбцов
  fmt.Println()
 }
}
```

5. **Фибоначчи с мемоизацией**  
   Напишите функцию для вычисления числа Фибоначчи с использованием мемоизации (сохранение ранее вычисленных результатов). Программа должна использовать рекурсию и условные операторы.
```go
package main

import "fmt"

// Функция для вычисления числа Фибоначчи с использованием мемоизации ()
func fibonacci(n int, memo map[int]int) int {
 // Проверка на наличие уже вычисленного значения в мапе
 if val, exists := memo[n]; exists {
  return val
 }

 // Базовые случаи
 if n <= 0 {
  return 0
 } else if n == 1 {
  return 1
 }

 // Рекурсивный вызов с сохранением результата
 memo[n] = fibonacci(n-1, memo) + fibonacci(n-2, memo)
 return memo[n]
}

func main() {
 // Создаем мапу для мемоизации
 memo := make(map[int]int)

 var n int
 fmt.Print("Введите номер числа в последовательности Фибоначчи: ")
 fmt.Scan(&n)

 // Вычисляем число Фибоначчи
 result := fibonacci(n, memo)
 fmt.Printf("Число Фибоначчи под номером %d равно %d", n, result)
}
```

6. **Обратные числа**  
   Напишите программу, которая принимает целое число и выводит его в обратном порядке. Например, для числа 12345 программа должна вывести 54321. Используйте цикл для обработки цифр числа.
```go

```

7. **Треугольник Паскаля**  
   Напишите программу, которая выводит треугольник Паскаля до заданного уровня. Для этого используйте цикл и массивы для хранения предыдущих значений строки треугольника.
```go

```

8. **Число палиндром**  
   Напишите программу, которая проверяет, является ли число палиндромом (одинаково читается слева направо и справа налево). Не используйте строки для решения этой задачи — работайте только с числами.
```go

```

9. **Нахождение максимума и минимума в массиве**  
   Напишите функцию, которая принимает массив целых чисел и возвращает одновременно максимальный и минимальный элемент с использованием одного прохода по массиву.
```go

```

10. **Игра "Угадай число"**  
   Напишите программу, которая загадывает случайное число от 1 до 100, а пользователь пытается его угадать. Программа должна давать подсказки "больше" или "меньше" после каждой попытки. Реализуйте ограничение на количество попыток.
```go

```

11. **Числа Армстронга**  
   Напишите программу, которая проверяет, является ли число числом Армстронга (число равно сумме своих цифр, возведённых в степень, равную количеству цифр числа). Например, 153 = 1³ + 5³ + 3³.
```go

```

12. **Подсчет слов в строке**  
   Напишите программу, которая принимает строку и выводит количество уникальных слов в ней. Используйте `map` для хранения слов и их количества.
```go

```

13. **Игра "Жизнь" (Conway's Game of Life)**  
   Реализуйте клеточный автомат "Жизнь" Конвея для двухмерного массива. Каждая клетка может быть либо живой, либо мертвой. На каждом шаге состояния клеток изменяются по следующим правилам:
   - Живая клетка с двумя или тремя живыми соседями остаётся живой, иначе умирает.
   - Мёртвая клетка с тремя живыми соседями оживает.
   Используйте циклы для обработки клеток.
```go

```

14. **Цифровой корень числа**  
   Напишите программу, которая вычисляет цифровой корень числа. Цифровой корень — это рекурсивная сумма цифр числа, пока не останется только одна цифра. Например, цифровой корень числа 9875 равен 2, потому что 9+8+7+5=29 → 2+9=11 → 1+1=2.
```go

```

15. **Римские цифры**  
   Напишите функцию, которая преобразует арабское число (например, 1994) в римское (например, "MCMXCIV"). Программа должна использовать циклы и условные операторы для создания римской записи.
```go

```