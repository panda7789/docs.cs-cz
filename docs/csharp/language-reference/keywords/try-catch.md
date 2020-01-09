---
title: Try-Catch- C# reference
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
ms.openlocfilehash: 5289dbe3aff0a9e1f1024a293ff469df44d34a3b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713024"
---
# <a name="try-catch-c-reference"></a>try-catch (Referenční dokumentace jazyka C#)

Příkaz try-catch se skládá z bloku `try` následovaného jednou nebo více `catch` klauzulími, které určují obslužné rutiny pro různé výjimky.

Je-li vyvolána výjimka, modul CLR (Common Language Runtime) vyhledá příkaz `catch`, který zpracovává tuto výjimku. Pokud aktuálně spuštěná metoda neobsahuje takový blok `catch`, CLR vyhledá metodu, která volala aktuální metodu, a tak dále v zásobníku volání. Pokud není nalezen žádný blok `catch`, modul CLR zobrazí uživateli neošetřenou zprávu o výjimce a zastaví provádění programu.

Blok `try` obsahuje chráněný kód, který může způsobit výjimku. Blok je proveden, dokud není vyvolána výjimka nebo je úspěšně dokončen. Například následující pokus o přetypování `null` objektu vyvolá výjimku <xref:System.NullReferenceException>:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

I když je možné použít klauzuli `catch` bez argumentů k zachycení jakéhokoliv typu výjimky, toto použití se nedoporučuje. Obecně platí, že byste měli zachytit pouze ty výjimky, ze kterých víte, jak provést obnovení. Proto byste měli vždy zadat argument objektu odvozený z <xref:System.Exception?displayProperty=nameWithType> například:

```csharp
catch (InvalidCastException e)
{
}
```

Ve stejném příkazu try-catch je možné použít více než jednu konkrétní klauzuli `catch`. V tomto případě je pořadí klauzulí `catch` důležité, protože `catch` klauzule jsou zkontrolovány v pořadí. Zachyťte konkrétnější výjimky před méně specifickými výjimkami. Kompilátor vytvoří chybu, Pokud seřadíte bloky catch tak, aby k nim nikdy nebylo možné získat přístup později.

Použití `catch` argumentů je jedním ze způsobů, jak filtrovat výjimky, které chcete zpracovat.  Můžete také použít filtr výjimek, který dále prověřuje výjimku k rozhodnutí, zda je zpracována.  Pokud filtr výjimek vrátí hodnotu false, hledání obslužné rutiny pokračuje.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Filtry výjimek jsou vhodnější pro zachycení a opětovné vyvolání (vysvětlení níže), protože filtry ponechají zásobník neškodný.  Pokud později obslužná rutina vypíše zásobník, můžete zjistit, kde výjimka původně pochází z, nikoli jenom poslední místo, které bylo znovu vyvoláno.  Běžné použití výrazů filtru výjimky je protokolování.  Můžete vytvořit filtr, který vždycky vrátí hodnotu false, která také vrací výstup do protokolu, a to tak, že se výjimky zaprotokolují, aniž byste je museli zpracovávat a znovu vyvolat.

Příkaz [throw](throw.md) lze použít v bloku `catch` k opětovnému vyvolání výjimky, která je zachycena příkazem `catch`. Následující příklad extrahuje informace o zdroji z výjimky <xref:System.IO.IOException> a poté vyvolá výjimku z nadřazené metody.

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

Můžete zachytit jednu výjimku a vyvolat jinou výjimku. V takovém případě určete výjimku, kterou jste zachytil jako vnitřní výjimku, jak je znázorněno v následujícím příkladu.

```csharp
catch (InvalidCastException e) 
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Můžete také znovu vyvolat výjimku, pokud je zadaná podmínka pravdivá, jak je znázorněno v následujícím příkladu.

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

> [!NOTE]
> Je také možné použít filtr výjimek a získat tak podobný výsledek často čisticím způsobem (a také Neupravovat zásobník, jak je vysvětleno výše v tomto dokumentu). Následující příklad má podobné chování jako v předchozím příkladu pro volající. Funkce vyvolá `InvalidCastException` zpět volajícímu, když je `e.Data` `null`.
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

V rámci `try` bloku inicializujte pouze proměnné, které jsou deklarovány v rámci. V opačném případě může výjimka nastat před dokončením provádění bloku. Například v následujícím příkladu kódu je proměnná `n` inicializována uvnitř bloku `try`. Pokus o použití této proměnné mimo blok `try` v příkazu `Write(n)` vyvolá chybu kompilátoru.

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

Další informace o catch naleznete v tématu [try-catch-finally](try-catch-finally.md).

## <a name="exceptions-in-async-methods"></a>Výjimky v asynchronních metodách

Asynchronní metoda je označena modifikátorem [Async](async.md) a obvykle obsahuje jeden nebo více výrazů nebo příkazů await. Výraz Await aplikuje operátor [await](../operators/await.md) na <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.

Když ovládací prvek dosáhne `await` v asynchronní metodě, je průběh metody pozastaven až do dokončení očekávané úlohy. Po dokončení úlohy může provádění pokračovat v metodě. Další informace naleznete v tématu [asynchronní programování pomocí asynchronního a operátoru await](../../programming-guide/concepts/async/index.md) a [řízení toku v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Dokončený úkol, na který je použit `await`, může být v chybovém stavu z důvodu neošetřené výjimky v metodě, která vrací úlohu. Čekání na úkol vyvolá výjimku. Úloha může také končit ve zrušeném stavu, pokud asynchronní proces, který je vrátí, je zrušen. Očekává se, že zrušená úloha vyvolá `OperationCanceledException`. Další informace o tom, jak zrušit asynchronní proces, naleznete v tématu [jemné ladění asynchronní aplikace](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Chcete-li zachytit výjimku, můžete očekávat úlohu v bloku `try` a zachytit výjimku v přidruženém bloku `catch`. Příklad naleznete v části [příklad asynchronní metody](#async-method-example) .

Úloha může být v chybném stavu, protože v očekávané asynchronní metodě došlo k více výjimkám. Například úloha může být výsledkem volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Při čekání na takovou úlohu je zachycena pouze jedna z výjimek a nelze předpovědět, která výjimka bude zachycena. Příklad naleznete v části [Task. WhenAll example](#taskwhenall-example) .

## <a name="example"></a>Příklad

V následujícím příkladu blok `try` obsahuje volání metody `ProcessString`, která může způsobit výjimku. Klauzule `catch` obsahuje obslužnou rutinu výjimky, která pouze zobrazí zprávu na obrazovce. Když je v rámci `MyMethod`volán příkaz `throw`, systém vyhledá příkaz `catch` a zobrazí `Exception caught`zprávy.

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>Příklad dvou bloků catch

V následujícím příkladu jsou použity dva bloky catch a nejvíc specifická výjimka, která je první, je zachycena.

Chcete-li zachytit minimální specifickou výjimku, můžete nahradit příkaz throw v `ProcessString` následujícím příkazem: `throw new Exception()`.

Pokud umístíte blok catch, který je nejméně specifický, jako první v příkladu, zobrazí se následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Příklad asynchronní metody

Následující příklad znázorňuje zpracování výjimek pro asynchronní metody. Chcete-li zachytit výjimku, kterou asynchronní úloha vyvolá, umístěte výraz `await` do bloku `try` a zachytit výjimku v bloku `catch`.

Odkomentujte `throw new Exception` řádek v příkladu k demonstraci zpracování výjimek. Vlastnost `IsFaulted` úlohy je nastavena na hodnotu `True`, vlastnost `Exception.InnerException` úlohy je nastavena na výjimku a výjimka je zachycena v bloku `catch`.

Odkomentujte `throw new OperationCanceledException` řádek k předvedení toho, co se stane, když zrušíte asynchronní proces. Vlastnost `IsCanceled` úlohy je nastavena na hodnotu `true`a výjimka je zachycena v bloku `catch`. Za určitých podmínek, které se na tento příklad nevztahují, má vlastnost `IsFaulted` úlohy nastavenou hodnotu `true` a `IsCanceled` je nastavená na `false`.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Příklad Task. WhenAll

Následující příklad znázorňuje zpracování výjimek, kde více úloh může mít za následek vícenásobné výjimky. Blok `try` očekává úkol, který je vrácen voláním <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Úkol je dokončen, když jsou dokončeny tři úkoly, na které se WhenAll aplikuje.

Každá ze tří úkolů způsobuje výjimku. Blok `catch` prochází výjimkami, které se nacházejí ve vlastnosti `Exception.InnerExceptions` úlohy, která byla vrácena <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
