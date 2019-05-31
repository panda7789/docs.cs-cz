---
title: try-catch - C# odkaz
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
ms.openlocfilehash: 28bf939cb7da760400486c52bb07649826628c1c
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422584"
---
# <a name="try-catch-c-reference"></a>try-catch (Referenční dokumentace jazyka C#)

Příkaz try-catch se skládá z `try` bloku, za nímž následuje jedna nebo více `catch` klauzule, které určují obslužné rutiny pro různé výjimky.

## <a name="remarks"></a>Poznámky

Když je vyvolána výjimka, modul CLR (CLR) hledá `catch` příkaz, který zpracovává tuto výjimku. Pokud aktuálně prováděné metody neobsahuje, `catch` blokovat, vyhledá CLR na metodu, která volá metodu aktuální výše v zásobníku volání a tak dále. Pokud ne `catch` nalezen blok a pak zobrazí uživateli zprávu neošetřené výjimky CLR a zastaví provádění programu.

`try` Blok obsahuje chráněné kód, který může způsobit výjimku. Blok je udělat, dokud je vyvolána výjimka nebo je byla úspěšně dokončena. Například následující pokusili přetypovat `null` objektu vyvolá <xref:System.NullReferenceException> výjimka:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

I když `catch` klauzuli lze použít bez argumentů pro zachycení jakéhokoli typu výjimky, toto využití se nedoporučuje. Obecně platí měli byste zachytit pouze takové výjimky, které víte, jak provést obnovení. Proto musíte vždycky zadat argument objekt odvozený od <xref:System.Exception?displayProperty=nameWithType> například:

```csharp
catch (InvalidCastException e)
{
}
```

Je možné použít více než jeden konkrétní `catch` klauzule ve stejném příkazu try-catch. V takovém případě pořadí `catch` klauzulí je důležité, protože `catch` klauzule jsou zkoumány podle pořadí. Zachycení více specifické výjimky než těch, které jsou specifické pro less. Kompilátor vytvoří chybu, pokud řazení, že vaše catch blokuje tak, aby novější bloku můžou být nikdy dosažen.

Pomocí `catch` argumentů je jedním ze způsobů filtrování pro výjimky, kterou chcete zpracovat.  Můžete také použít filtr výjimek, který prověří další výjimky můžete rozhodnout, jestli ji zpracovat.  Pokud filtr výjimek vrací hodnotu false, pak hledání pro obslužnou rutinu, bude pokračovat.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Filtry výjimek jsou upřednostňovány vůči zachytávání a opětné vyvolání (vysvětleno níže), protože filtry ponechte nepoškozená zásobníku.  Pokud je novější rutinu výpisy zásobníku, naleznete v tématu výjimka původně, odkud, ne jenom poslední místo, které byla vyvolána.  Běžné použití výrazu filtru výjimky je protokolování.  Můžete vytvořit filtr, která vždy vrátí hodnotu false, která také výstup protokolu, může protokolování výjimek, jako jsou přejít bez nutnosti jejich zpracování a znovu vyvolat.

A [throw](throw.md) příkaz lze použít v `catch` pro opětovné vyvolání výjimky, která je zachycena `catch` příkazu. Následující příklad extrahuje informace o zdroji ze <xref:System.IO.IOException> výjimky a potom vyvolá výjimku pro nadřazenou metodu.

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

Můžete zachytit jednu výjimku a jinou výjimku. Když toto provedete, zadejte výjimku, která je zachycena jako vnitřní výjimku, jak je znázorněno v následujícím příkladu.

```csharp
catch (InvalidCastException e) 
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Můžete také znovu vyvolat výjimku při je zadaná podmínka pravdivá, jak je znázorněno v následujícím příkladu.

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
> Je také možné použít k získání výsledku podobně jako v často přehlednější způsobem (stejně jako místo abyste upravili zásobníku, jak je popsáno dříve v tomto dokumentu) filtr výjimek. Následující příklad je podobné chování pro volající jako předchozí příklad. Funkce vyvolá `InvalidCastException` zpět do volajícího při `e.Data` je `null`.
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

Z uvnitř `try` blokovat, inicializovat pouze proměnné, které jsou deklarovány v něm. V opačném případě výjimce může dojít předtím, než se dokončí provádění bloku. Například v následujícím příkladu kódu proměnné `n` je inicializován uvnitř `try` bloku. Pokus o použití této proměnné mimo `try` blokovat `Write(n)` příkaz vygeneruje chybu kompilátoru.

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

Další informace o catch, naleznete v tématu [konstrukce try-catch-finally](try-catch-finally.md).

## <a name="exceptions-in-async-methods"></a>Výjimky v asynchronních metodách
Asynchronní metoda je označena [asynchronní](async.md) modifikátor a obvykle obsahuje jeden nebo více await výrazy nebo příkazy. Výraz await se vztahuje [await](await.md) operátor <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.

Když ovládací prvek dosáhne `await` v asynchronní metodě, je pozastavený průběh v metodě, až do dokončení očekávané úlohy. Po dokončení úlohy se provádění může pokračovat v metodě. Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../programming-guide/concepts/async/index.md) a [tok řízení v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Dokončené úlohy, ke kterému `await` platí může být v chybovém stavu kvůli neošetřené výjimce v metodě, která vrátí úkol. Čekání na výjimku. Úkol může také skončit ve zrušeném stavu Pokud se zruší asynchronní proces, který vrátí jej. Čeká na zrušenou úlohu vyvolá `OperationCanceledException`. Další informace o tom, jak zrušit asynchronní proces najdete v tématu [asynchronní aplikace Fine-Tuning](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

K zachycení výjimky, await úkol v `try` blokovat a zachytit výjimku v přidruženém `catch` bloku. Příklad najdete v části "Vzorový".

Úloha může být v chybovém stavu, protože došlo k více výjimek v očekávaná asynchronní metody. Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Když budete očekávat takový úkol, je zachycena pouze jednu z výjimek a nelze předpovědět, které k výjimce. Příklad najdete v části "Vzorový".

## <a name="example"></a>Příklad

V následujícím příkladu `try` blok obsahuje volání `ProcessString` metodu, která může způsobit výjimku. `catch` Klauzule obsahujícím obslužnou rutinu výjimky, která zobrazuje pouze zprávu na obrazovce. Při `throw` příkazu je volána z uvnitř `MyMethod`, hledá systému `catch` příkaz a zobrazí se zpráva `Exception caught`.

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="example"></a>Příklad

V následujícím příkladu se používají dva bloky catch a nejspecifičtější výjimku, která nastane dřív, je zachycena.

K zachycení nejméně konkrétní výjimky, můžete nahradit příkaz throw v `ProcessString` pomocí následujícího příkazu: `throw new Exception()`.

Pokud v příkladu nejdřív umístíte blok catch nejméně specifická, zobrazí se následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="example"></a>Příklad

Následující příklad ukazuje zpracování výjimek pro asynchronní metody. Pokud chcete zachytit výjimku, která vyvolá asynchronní úlohy, umístěte `await` výrazu v `try` blokovat a zachytit výjimku v `catch` bloku.

Zrušením komentáře u `throw new Exception` řádek v příkladu předvést zpracování výjimek. Úkolu `IsFaulted` je nastavena na `True`, úkolu `Exception.InnerException` je nastavena na výjimky a výjimky je zachycena v `catch` bloku.

Zrušením komentáře u `throw new OperationCanceledException` řádku předvést, co se stane, když zrušíte asynchronní proces. Úkolu `IsCanceled` je nastavena na `true`, která je zachycena výjimka v `catch` bloku. Za určitých podmínek, které se nevztahují na tohoto příkladu, úloha `IsFaulted` je nastavena na `true` a `IsCanceled` je nastavena na `false`.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="example"></a>Příklad

Následující příklad ukazuje zpracování výjimek, kde více úkolů může vést k více výjimek. `try` Bloku očekává úkol, který je vrácen voláním <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Po dokončení tři úkolů, u kterých je použitá WhenAll je úloha dokončena.

Všechny tři úkoly dojde k výjimce. `catch` Bloku prochází výjimky, které jsou součástí `Exception.InnerExceptions` vlastnosti úkolu, který byl vrácen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
