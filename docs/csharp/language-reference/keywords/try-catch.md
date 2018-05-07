---
title: try-catch (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: f917d662366dc8ff540cdee6222199fe8f5606c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="try-catch-c-reference"></a>try-catch (Referenční dokumentace jazyka C#)
Try-catch – příkaz se skládá z `try` bloku, za nímž následuje jeden nebo více `catch` klauzule, které určují obslužné rutiny pro různé výjimky.  
  
## <a name="remarks"></a>Poznámky  
 Když je vyvolána výjimka, modul CLR (CLR) hledá `catch` příkaz, který zpracovává výjimku. Pokud například neobsahuje metodu aktuálně prováděné `catch` blok CLR vypadá na metodu, která volá metodu aktuální, a tak dále zásobníkem volání. Pokud žádné `catch` blok a pak modulu CLR, zobrazí se zpráva neošetřené výjimky pro uživatele a zastaví provádění tohoto programu.  
  
 `try` Blok obsahuje chráněného kód, který může způsobit výjimku. Blok je provést, dokud je vyvolána výjimka, nebo je byla úspěšně dokončena. Například následující pokus přetypovat `null` objektu vyvolá <xref:System.NullReferenceException> výjimka:  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 I když `catch` klauzuli lze použít bez argumentů k zachycení jakýkoli typ výjimky, toto využití se nedoporučuje. Obecně platí by měla pouze zachytit tyto výjimky, kterých víte, jak jej obnovit. Proto musíte vždycky zadat argument objekt odvozené z <xref:System.Exception?displayProperty=nameWithType> například:  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 Je možné použít více než jeden konkrétní `catch` klauzule v jednom příkazu try-catch. V tomto případě pořadí `catch` klauzule je důležité, protože `catch` klauzule se zkontrolují v pořadí. Před méně konkrétní ty catch konkrétnější výjimky. Kompilátor vyvolá chybu, je-li pořadí, že vaše catch blokuje tak, aby nikdy dostupný novější blok.  
  
 Pomocí `catch` argumentů je jeden způsob, jak filtrovat výjimky, které chcete zpracovávat.  Můžete také použít výraz predikátu, která prověřuje další výjimka můžete rozhodnout, jestli se nezdařilo.  Výraz predikátu vrací hodnotu false, potom pokračuje hledání pro obslužnou rutinu.  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 Filtry výjimek, je vhodnější zachytávání a opětné vyvolání (vysvětleno níže), protože zásobník nepoškozená nechte filtry.  Pokud obslužnou rutinu novější výpisy zásobníku, uvidíte, kde výjimka původně pochází, nikoli pouze poslední, který byl znovu vyvolány místo.  Běžně se používají výrazy filtru výjimek je protokolování.  Můžete vytvořit predikátem funkci, která vždy vrátí hodnotu false, který také výstupy do protokolů, jako přejde bez nutnosti mohli je zpracovat a opětovné můžete protokolovat výjimky.  
  
 A [throw](../../../csharp/language-reference/keywords/throw.md) příkaz lze použít v `catch` blok k znovu vyvolání výjimky, která bude zachycena `catch` příkaz. Následující příklad extrahuje informace o zdroji ze <xref:System.IO.IOException> výjimka a potom vyvolá výjimku pro nadřazenou metodu.  
  
```csharp  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    if (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 Můžete zachytit jednu výjimku a vyvolat různé výjimky. Když to uděláte, zadejte výjimku, která zachycena jako v popisu vnitřní výjimky, jak je znázorněno v následujícím příkladu.  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 Můžete také znovu vyvolat výjimku, pokud je zadaná podmínka hodnotu true, jak je znázorněno v následujícím příkladu.  
  
```csharp  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
 }  
```  
  
 Z uvnitř `try` blokovat, inicializovat pouze proměnné, které jsou deklarované v něm. Výjimku, jinak může dojít, než bude dokončeno spuštění bloku. Například v následujícím příkladu kódu proměnnou `n` je inicializován uvnitř `try` bloku. Pokus o použití této proměnné mimo `try` blokovat `Write(n)` příkaz vygeneruje se chybová zpráva kompilátoru.  
  
```csharp  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 Další informace o catch najdete v tématu [try-catch-finally –](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
## <a name="exceptions-in-async-methods"></a>Výjimky v asynchronní metody  
 Asynchronní metody je označena kvalifikátorem [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor a obvykle obsahuje jeden nebo více await výrazy nebo příkazy. Await výraz se vztahuje [await](../../../csharp/language-reference/keywords/await.md) operátorovi <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.  
  
 Při řízení dosáhnou `await` v asynchronní metody, je průběh v metodě pozastaveno, dokud dokončení awaited úlohy. Po dokončení úlohy provádění může pokračovat v metodě. Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md) a [řízení toku v asynchronních programech](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Dokončené úlohy, ke kterému `await` platí může být v chybovém stavu z důvodu neošetřené výjimce v metodě, který vrátí úlohu. Systém čeká na úlohu vyvolá výjimku. Úlohu můžete také skončit ve zrušené stavu, pokud se zruší asynchronní proces, který vrátí ji. Systém čeká na zrušené úlohy vyvolá `OperationCanceledException`. Další informace o tom, jak zrušit asynchronní proces najdete v tématu [Fine-Tuning vaše asynchronní aplikace](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 K zachycení výjimky, kde čekají na úlohu v `try` blokovat a zachycení výjimky v přidruženém `catch` bloku. Příklad najdete v části "Příklad".  
  
 Úloha může být v chybovém stavu, protože několik výjimek došlo k chybě v očekávané asynchronní metody. Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Když jste await takových úloh, pouze jeden z výjimky je zachycena a nemůžete předpovědět, které k výjimce. Příklad najdete v části "Příklad".  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `try` blok obsahuje volání `ProcessString` metoda, která může způsobit výjimku. `catch` Klauzule WHERE obsahuje jenom na obrazovce se objeví zpráva obslužná rutina výjimky. Když `throw` příkaz je volána z uvnitř `MyMethod`, hledá v systému `catch` příkaz a zobrazí zprávu `Exception caught`.  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se používají dva bloky catch a nejvíce výjimka, která dodává první, je zachycena.  
  
 K zachycení výjimky nejméně specifická, můžete nahradit v příkazu throw `ProcessString` s následující příkaz: `throw new Exception()`.  
  
 Pokud nejprve umístit blok catch nejmenší konkrétní v příkladu se zobrazí následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje zpracování výjimek pro asynchronní metody. Zachytit výjimku, která vyvolá asynchronní úlohy, umístit `await` výrazu v `try` blokovat a zachycení výjimky v `catch` bloku.  
  
 Zrušením komentáře u `throw new Exception` řádku v příkladu za účelem ukázky zpracování výjimek. Úkolu `IsFaulted` je nastavena na `True`, úkolu `Exception.InnerException` je nastavena na výjimku a je výjimka zachycena v `catch` bloku.  
  
 Zrušením komentáře u `throw new OperationCancelledException` řádku k předvedení toho, co se stane, když zrušíte asynchronní proces. Úkolu `IsCanceled` je nastavena na `true`, a je výjimka zachycena v `catch` bloku. Za určitých podmínek, které se nevztahují na tomto příkladu úlohu na `IsFaulted` je nastavena na `true` a `IsCanceled` je nastaven na `false`.  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje zpracování výjimek, kde více úloh může mít za následek více výjimek. `try` Bloku čeká úloha, která se vrátí po volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Po dokončení tři úloh, pro které je použito WhenAll dokončení úkolu.  
  
 Jednotlivé tři úlohy dojde k výjimce. `catch` Bloku iteruje výjimky, které jsou součástí `Exception.InnerExceptions` vlastnost úloha, která vrátila <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [Příkazy zpracování výjimek](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
