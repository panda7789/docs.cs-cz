---
title: Try-Catch- C# reference
ms.custom: seodec18
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
ms.openlocfilehash: 8f901bd8ab5dcdcf4f5674e3f235267c9f535725
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168722"
---
# <a name="try-catch-c-reference"></a>try-catch (Referenční dokumentace jazyka C#)

Příkaz try-catch se skládá z `try` bloku následovaného jednou nebo více `catch` klauzulemi, které určují obslužné rutiny pro různé výjimky.

Je-li vyvolána výjimka, modul CLR (Common Language Runtime) vyhledá `catch` příkaz, který zpracovává tuto výjimku. Pokud aktuálně spuštěná metoda neobsahuje takový `catch` blok, CLR vyhledá metodu, která volala aktuální metodu, a tak dále v zásobníku volání. Pokud není `catch` nalezen žádný blok, modul CLR zobrazí uživateli neošetřenou zprávu o výjimce a zastaví provádění programu.

`try` Blok obsahuje chráněný kód, který může způsobit výjimku. Blok je proveden, dokud není vyvolána výjimka nebo je úspěšně dokončen. Například následující pokus o přetypování `null` objektu <xref:System.NullReferenceException> vyvolá výjimku:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

Přestože lze `catch` klauzuli použít bez argumentů k zachycení jakéhokoliv typu výjimky, toto použití se nedoporučuje. Obecně platí, že byste měli zachytit pouze ty výjimky, ze kterých víte, jak provést obnovení. Proto byste měli vždy zadat argument objektu odvozený z <xref:System.Exception?displayProperty=nameWithType> například:

```csharp
catch (InvalidCastException e)
{
}
```

Ve stejném příkazu try-catch je možné použít `catch` více než jednu konkrétní klauzuli. V tomto případě je pořadí `catch` klauzulí důležité, `catch` protože klauzule jsou zkontrolovány v pořadí. Zachyťte konkrétnější výjimky před méně specifickými výjimkami. Kompilátor vytvoří chybu, Pokud seřadíte bloky catch tak, aby k nim nikdy nebylo možné získat přístup později.

Použití `catch` argumentů je jedním ze způsobů, jak filtrovat výjimky, které chcete zpracovat.  Můžete také použít filtr výjimek, který dále prověřuje výjimku k rozhodnutí, zda je zpracována.  Pokud filtr výjimek vrátí hodnotu false, hledání obslužné rutiny pokračuje.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Filtry výjimek jsou vhodnější pro zachycení a opětovné vyvolání (vysvětlení níže), protože filtry ponechají zásobník neškodný.  Pokud později obslužná rutina vypíše zásobník, můžete zjistit, kde výjimka původně pochází z, nikoli jenom poslední místo, které bylo znovu vyvoláno.  Běžné použití výrazů filtru výjimky je protokolování.  Můžete vytvořit filtr, který vždycky vrátí hodnotu false, která také vrací výstup do protokolu, a to tak, že se výjimky zaprotokolují, aniž byste je museli zpracovávat a znovu vyvolat.

Příkaz [throw](throw.md) lze použít v `catch` bloku k opětovnému vyvolání výjimky, která `catch` je zachycena příkazem. Následující příklad extrahuje informace o zdroji z <xref:System.IO.IOException> výjimky a poté vyvolá výjimku z nadřazené metody.

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
> Je také možné použít filtr výjimek a získat tak podobný výsledek často čisticím způsobem (a také Neupravovat zásobník, jak je vysvětleno výše v tomto dokumentu). Následující příklad má podobné chování jako v předchozím příkladu pro volající. Funkce vyvolá `InvalidCastException` zpětné volání volajícímu, pokud `e.Data` je `null`.
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

V rámci `try` bloku inicializujte pouze proměnné, které jsou deklarovány v tomto případě. V opačném případě může výjimka nastat před dokončením provádění bloku. Například v následujícím příkladu kódu je proměnná `n` inicializována `try` uvnitř bloku. Pokus o použití této proměnné mimo `try` blok `Write(n)` v příkazu vytvoří chybu kompilátoru.

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

Když ovládací prvek dosáhne `await` v asynchronní metodě, je průběh metody pozastaven, dokud se nedokončí dokončená úloha. Po dokončení úlohy může provádění pokračovat v metodě. Další informace naleznete v tématu [asynchronní programování pomocí asynchronního a operátoru await](../../programming-guide/concepts/async/index.md) a [řízení toku v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Dokončený úkol, ke `await` kterému je použito, může být v chybovém stavu z důvodu neošetřené výjimky v metodě, která vrací úlohu. Čekání na úkol vyvolá výjimku. Úloha může také končit ve zrušeném stavu, pokud asynchronní proces, který je vrátí, je zrušen. Čekání na zrušený úkol vyvolá výjimku `OperationCanceledException`. Další informace o tom, jak zrušit asynchronní proces, naleznete v tématu [jemné ladění asynchronní aplikace](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Chcete-li zachytit výjimku, očekávat úlohu v `try` bloku a zachytit výjimku v přidruženém `catch` bloku. Příklad naleznete v části [příklad asynchronní metody](#async-method-example) .

Úloha může být v chybném stavu, protože v očekávané asynchronní metodě došlo k více výjimkám. Například úloha může být výsledkem volání metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Při čekání na takovou úlohu je zachycena pouze jedna z výjimek a nelze předpovědět, která výjimka bude zachycena. Příklad naleznete v části [Task. WhenAll example](#taskwhenall-example) .

## <a name="example"></a>Příklad

V následujícím příkladu `try` blok obsahuje volání `ProcessString` metody, která může způsobit výjimku. `catch` Klauzule obsahuje obslužnou rutinu výjimky, která pouze zobrazí zprávu na obrazovce. Když je `MyMethod` `catch` příkaz volán zevnitř, systém vyhledá příkaz a zobrazí zprávu `Exception caught`. `throw`

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>Příklad dvou bloků catch

V následujícím příkladu jsou použity dva bloky catch a nejvíc specifická výjimka, která je první, je zachycena.

Chcete-li zachytit minimální specifickou výjimku, můžete nahradit příkaz `ProcessString` throw příkazem pomocí následujícího příkazu:. `throw new Exception()`

Pokud umístíte blok catch, který je nejméně specifický, jako první v příkladu, zobrazí se následující chybová zpráva `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`:.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Příklad asynchronní metody

Následující příklad znázorňuje zpracování výjimek pro asynchronní metody. Chcete-li zachytit výjimku, kterou asynchronní úloha vyvolá, umístěte `await` výraz `try` do bloku a `catch` Zachyťte výjimku v bloku.

Odkomentujte `throw new Exception` řádek v příkladu k demonstraci zpracování výjimek. `IsFaulted` Vlastnost úlohy je nastavena na `True`hodnotu, `Exception.InnerException` vlastnost úlohy je nastavena na výjimku a výjimka je zachycena v `catch` bloku.

Odkomentujte `throw new OperationCanceledException` řádek k předvedení toho, co se stane, když zrušíte asynchronní proces. `IsCanceled` Vlastnost úlohy je nastavena na `true`hodnotu a `catch` výjimka je zachycena v bloku. Za určitých podmínek, které se nevztahují na tento příklad, `IsFaulted` je vlastnost úlohy nastavena `true` na `IsCanceled` hodnotu a je `false`nastavena na.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Příklad Task. WhenAll

Následující příklad znázorňuje zpracování výjimek, kde více úloh může mít za následek vícenásobné výjimky. Blok čeká na úlohu vrácenou <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>voláním. `try` Úkol je dokončen, když jsou dokončeny tři úkoly, na které se WhenAll aplikuje.

Každá ze tří úkolů způsobuje výjimku. Blok prochází výjimky, které jsou umístěny `Exception.InnerExceptions` ve vlastnosti <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>úkolu, který vrátil. `catch`

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
- [Postupy: Explicitně vyvolat výjimky](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
