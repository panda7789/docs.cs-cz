---
title: try-catch - C# Reference
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
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173468"
---
# <a name="try-catch-c-reference"></a>try-catch (Referenční dokumentace jazyka C#)

Příkaz try-catch se skládá `try` z bloku následovaného jednou nebo více `catch` klauzulemi, které určují obslužné rutiny pro různé výjimky.

Při vyvolání výjimky, clr (CLR) společného `catch` jazyka hledá příkaz, který zpracovává tuto výjimku. Pokud aktuálně spuštěná metoda neobsahuje `catch` takový blok, CLR se podívá na metodu, která volala aktuální metodu a tak dále nahoru zásobníku volání. Pokud `catch` není nalezen žádný blok, zobrazí CLR neošetřenou zprávu o výjimce uživateli a zastaví provádění programu.

Blok `try` obsahuje střežený kód, který může způsobit výjimku. Blok je spuštěn, dokud není vyvolána výjimka nebo dokud není úspěšně dokončena. Například následující pokus o `null` přetypovat <xref:System.NullReferenceException> objekt vyvolá výjimku:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

Přestože `catch` klauzule lze použít bez argumentů zachytit jakýkoli typ výjimky, toto použití se nedoporučuje. Obecně platí, že byste měli zachytit pouze ty výjimky, ze kterých víte, jak se zotavit. Proto byste měli vždy zadat argument <xref:System.Exception?displayProperty=nameWithType> objektu odvozený například:

```csharp
catch (InvalidCastException e)
{
}
```

Je možné použít více než `catch` jednu konkrétní klauzuli ve stejném příkazu try-catch. V tomto případě je `catch` pořadí doložek důležité, protože `catch` doložky jsou zkoumány v pořadí. Zachyťte konkrétnější výjimky před méně konkrétními výjimkami. Kompilátor vytvoří chybu, pokud objednáte bloky catch tak, aby nikdy nebylo dosaženo pozdějšího bloku.

Použití `catch` argumentů je jedním ze způsobů filtrování výjimek, které chcete zpracovat.  Můžete také použít filtr výjimek, který dále zkoumá výjimku a rozhodne, zda ji zpracovat.  Pokud filtr výjimek vrátí hodnotu false, pokračuje hledání obslužné rutiny.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Filtry výjimek jsou vhodnější k zachycení a opětovnému vyvolání (vysvětleno níže), protože filtry ponechávají zásobník bez poškození.  Pokud novější obslužná rutina vypíše zásobníku, můžete zobrazit, kde výjimka původně pochází, nikoli jen na posledním místě, které bylo znovu vyvoláno.  Běžně se používají výrazy filtru výjimek protokolování.  Můžete vytvořit filtr, který vždy vrátí false, který také výstupy do protokolu, můžete protokolovat výjimky, jak jdou, aniž by bylo třeba je zpracovat a znovu vyvolat.

Příkaz [throw](throw.md) lze použít `catch` v bloku znovu vyvolat výjimku, `catch` která je zachycena příkazem. Následující příklad extrahuje zdrojové informace z výjimky <xref:System.IO.IOException> a potom vyvolá výjimku nadřazené metody.

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

Můžete zachytit jednu výjimku a vyvolat jinou výjimku. Když toto, zadejte výjimku, která byla zachycena jako vnitřní výjimku, jak je znázorněno v následujícím příkladu.

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
> Je také možné použít filtr výjimek získat podobný výsledek často čistší způsobem (stejně jako neúpravy zásobníku, jak je vysvětleno výše v tomto dokumentu). Následující příklad má podobné chování pro volající jako předchozí příklad. Funkce vyvolá `InvalidCastException` zpět volajícímu, `e.Data` když `null`je .
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

Zevnitř `try` bloku inicializovat pouze proměnné, které jsou deklarovány v něm. V opačném případě může dojít k výjimce před dokončením provádění bloku. Například v následujícím příkladu kódu `n` je proměnná `try` inicializována uvnitř bloku. Pokus o použití této `try` proměnné mimo `Write(n)` blok v příkazu vygeneruje chybu kompilátoru.

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

Další informace o úlovku naleznete v [tématu try-catch-finally](try-catch-finally.md).

## <a name="exceptions-in-async-methods"></a>Výjimky v asynchronních metodách

Asynchronní metoda je [označena asynchronním](async.md) modifikátorem a obvykle obsahuje jeden nebo více výrazů nebo příkazů await. Výraz await použije operátor [await](../operators/await.md) <xref:System.Threading.Tasks.Task> na <xref:System.Threading.Tasks.Task%601>operátor a nebo .

Když ovládací prvek `await` dosáhne v asynchronní metodě, průběh metody je pozastaven, dokud nebude dokončena očekávaná úloha. Po dokončení úlohy může spuštění pokračovat v metodě. Další informace naleznete [v tématu Asynchronní programování s asynchronní a await](../../programming-guide/concepts/async/index.md) a [control flow v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Dokončená úloha, na kterou `await` je použita může být v chybovém stavu z důvodu neošetřené výjimky v metodě, která vrátí úkol. Čekání na úkol vyvolá výjimku. Úloha může také skončit ve stavu zrušena, pokud je zrušen asynchronní proces, který vrátí. Čekání na zrušený úkol `OperationCanceledException`vyvolá . Další informace o zrušení asynchronního procesu naleznete v [tématu Jemné doladění asynchronní aplikace](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Chcete-li zachytit výjimku, počkejte na úkol v `try` bloku `catch` a zachyťte výjimku v přidruženém bloku. Příklad naleznete v části [Příklad metody Async.](#async-method-example)

Úloha může být v chybovém stavu, protože došlo k více výjimkám v aočekávaná asynchronní metoda. Úkol může být například výsledkem volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Když čekáte na takový úkol, je zachycena pouze jedna z výjimek a nemůžete předpovědět, která výjimka bude zachycena. Příklad naleznete v části [Task.WhenAll example.](#taskwhenall-example)

## <a name="example"></a>Příklad

V následujícím příkladu `try` blok obsahuje volání `ProcessString` metody, která může způsobit výjimku. Klauzule `catch` obsahuje obslužnou rutinu výjimky, která pouze zobrazí zprávu na obrazovce. Při `throw` volání příkazu `MyMethod`zevnitř systém vyhledá `catch` příkaz a `Exception caught`zobrazí zprávu .

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>Příklad dvou bloků úlovků

V následujícím příkladu jsou použity dva bloky catch a nejkonkrétnější výjimka, která je na prvním místě, je zachycena.

Chcete-li zachytit nejméně konkrétní výjimku, `ProcessString` můžete nahradit throw `throw new Exception()`prohlášení v s následujícím příkazem: .

Pokud v příkladu umístíte nejprve nejméně specifický blok catch, zobrazí se následující chybová zpráva: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Příklad asynchronní metody

Následující příklad ilustruje zpracování výjimek pro asynchronní metody. Chcete-li zachytit výjimku, kterou vyvolá `await` asynchronní `try` úloha, umístěte výraz `catch` do bloku a zachyťte výjimku v bloku.

Odkomentujte `throw new Exception` řádek v příkladu, abyste demonstrovali zpracování výjimek. `IsFaulted` Vlastnost úkolu je nastavena `True`na , `Exception.InnerException` vlastnost úkolu je nastavena na výjimku `catch` a výjimka je zachycena v bloku.

Odkomentujte `throw new OperationCanceledException` řádek a předveďte, co se stane, když zrušíte asynchronní proces. `IsCanceled` Vlastnost úkolu je nastavena `true`na , a výjimka je zachycena `catch` v bloku. Za určitých podmínek, které se v tomto `IsFaulted` příkladu `true` nevztahují, je vlastnost úkolu nastavena na položku a `IsCanceled` je nastavena na . `false`

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Task.WhenPříklad

Následující příklad znázorňuje zpracování výjimek, kde více úkolů může mít za následek více výjimek. Blok `try` čeká na úkol, který je vrácen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>voláním . Úkol je dokončen po dokončení tří úkolů, na které je použita WhenAll.

Každý ze tří úkolů způsobí výjimku. Blok `catch` iterates prostřednictvím výjimky, které `Exception.InnerExceptions` se nacházejí ve vlastnosti <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>úkolu, který byl vrácen .

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [try statement](~/_csharplang/spec/statements.md#the-try-statement) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
