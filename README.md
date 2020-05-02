# Отчёт о тестировании приложения "Money Transfer"

## Краткое описание

02.05.2020 г. было проведено тестирование банковского приложения "Money Transfer". 
На тестирование потрачено 1 час.
"Money Transfer" описывает процесс пополнение счета VIP-клиента.
В качестве входных данных в приложении выбраны следующие переменные:
* Текущий баланс ```int``` (sum)  со значением 2_000_000_000
* Перевод денег ```int``` (transaction) со значением 500_000_000
* Итоговое значение ```int``` (balance)

```public class Main {
       public static void main(String[] args) {
           int sum = 2_000_000_000;
           int transaction = 500_000_000;
           int balance = sum + transaction;
   
           System.out.println(balance);
   
       }
   }
```
В результате тестирования приложения итоговое значение int выдало результат: -1794967296
Данный результат не соответствует действительности. Верный результат 2_500_000_000. 
Для итогового значения неверно выбрана переменная ```int```, так как ее диапазон значений меньше, чем 2_500_000_000. Для получения верного результата необходимо выбрать переменную ```long``` в итоговом значении, имеющую больший диапазон.


## Описание тестов
* Проведено функциональное тестирование приложения "Money Transfer" с использованием как входных, так и подобранных данных
* Протестирована работа переменной ```int```
* Проведено позитивное и негативное тестирование приложения "Money Transfer"
* Проведено тестирование граничных значений переменной ```int```

## Результаты

1. Проведено 3 успешных теста, где менялось значение ```int``` transaction:
  
    ```public class Main {
             public static void main(String[] args) {
                 int sum = 2_000_000_000;
                 int transaction = 50_000_000;
                 int balance = sum + transaction;
         
                 System.out.println(balance);
         
             }
         }
      ``` 
    
   ```public class Main {
             public static void main(String[] args) {
                 int sum = 2_000_000_000;
                 int transaction = 147_483_647;
                 int balance = sum + transaction;
         
                 System.out.println(balance);
         
             }
         }
      ```
   ``` public class Main {
          public static void main(String[] args) {
              int sum = 2_000_000_000;
              int transaction = 5_000_000;
              int balance = sum + transaction;
      
              System.out.println(balance);
      
          }
      }
   ```
Проведено 3 негативных теста, где менялось значение ```int``` transaction:
    
    public class Main {
        public static void main(String[] args) {
            int sum = 2_000_000_000;
            int transaction = 500_000_000;
            int balance = sum + transaction;
    
            System.out.println(balance);
    
        }
    }

``` public class Main {
    public static void main(String[] args) {
        int sum = 2_000_000_000;
        int transaction = 147_483_648;
        int balance = sum + transaction;

        System.out.println(balance);

    }
}
```

``` public class Main {
     public static void main(String[] args) {
         int sum = 2_000_000_000;
         int transaction = 148_483_647;
         int balance = sum + transaction;
 
         System.out.println(balance);
 
     }
 }
```
2. В результате тестирования выявлены следующие дефекты:
[int balance](https://github.com/TanyaKomyakova/Banker/issues/1)

## Общие рекомендации

При написании приложения для пополнения счета, необходимо использовать те типы переменных с диапазоном значений, которые вмещают количество значений для получения верного результата
Значение  ```int``` будет верным в том случае если, тип ```int```  принимает диапазон  от -2 147 483 648 до 2 147 483 647.