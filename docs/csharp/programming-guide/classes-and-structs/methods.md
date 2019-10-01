---
title: Metody – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 318f51afefd780ed7be0ab8c2a72acb5fcf9db15
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699967"
---
# <a name="methods-c-programming-guide"></a>Metody (Průvodce programováním v C#)

Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že budou příkazy provedeny voláním metody a zadáním požadovaných argumentů metody. V C#je každá spuštěná instrukce provedena v kontextu metody. Metoda `Main` je vstupním bodem pro každou C# aplikaci a je volána modulem CLR (Common Language Runtime) při spuštění programu.

> [!NOTE]
> Tento článek popisuje pojmenované metody. Informace o anonymních funkcích naleznete v tématu [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).

## <a name="method-signatures"></a>Signatury metod

Metody jsou deklarovány ve [třídě](../../language-reference/keywords/class.md) nebo [struktuře](../../language-reference/keywords/struct.md) zadáním úrovně přístupu, například `public` nebo `private`, volitelné modifikátory, jako je například `abstract` nebo `sealed`, návratová hodnota, název metody a všechny parametry metody. Tyto části jsou společně signaturou metody.

> [!NOTE]
> Návratový typ metody není součástí signatury metody pro účely přetěžování metody. Je však součástí signatury metody při určování kompatibility mezi delegátem a metodou, na kterou odkazuje.

Parametry metody jsou uzavřeny v závorkách a jsou odděleny čárkami. Prázdné kulaté závorky označují, že metoda nepožaduje žádné parametry. Tato třída obsahuje čtyři metody:

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a>Přístup k metodě

Volání metody v objektu se podobá přístupu k poli. Za název objektu přidejte tečku, název metody a závorky. Argumenty jsou uvedeny v závorkách a jsou odděleny čárkami. Metody třídy `Motorcycle` lze proto volat jako v následujícím příkladu:

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a>Parametry metody vs. argumenty

Definice metody určuje názvy a typy parametrů, které jsou požadovány. Když volání kódu volá metodu, poskytuje konkrétní hodnoty nazvané argumenty pro každý parametr. Argumenty musí být kompatibilní s typem parametru, ale název argumentu (pokud existuje) použitý v volajícím kódu nemusí být stejný jako parametr s názvem definovaným v metodě. Příklad:

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a>Předávání odkazem vs. předání podle hodnoty

Ve výchozím nastavení, když je typ hodnoty předán metodě, je předána kopie namísto samotného objektu. Proto změny argumentu nemají žádný vliv na původní kopii v volání metody. Pomocí klíčového slova ref můžete předat typ hodnoty odkazem. Další informace naleznete v tématu [předávání parametrů typu hodnoty](./passing-value-type-parameters.md). Seznam předdefinovaných typů hodnot naleznete v tématu [Tabulka typů hodnot](../../language-reference/keywords/value-types-table.md).

Je-li objekt typu odkazu předán metodě, odkaz na objekt je předán. To znamená, že metoda nepřijímá samotný objekt, ale argument, který označuje umístění objektu. Pokud změníte člena objektu pomocí tohoto odkazu, změna se projeví v argumentu volající metody, a to i v případě, že předáte objekt podle hodnoty.

Typ odkazu vytvoříte pomocí klíčového slova `class`, jak ukazuje následující příklad:

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

Nyní Pokud předáte objekt, který je založen na tomto typu pro metodu, odkaz na objekt je předán. Následující příklad předá objekt typu `SampleRefType` do metody `ModifyObject`:

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

Příklad v podstatě totéž jako předchozí příklad v tom, že předává argument podle hodnoty metodě. Ale vzhledem k tomu, že se používá typ odkazu, je výsledek jiný. Úprava, která je provedena v `ModifyObject` do pole `value` parametru, `obj`, také změní pole `value` argumentu, `rt` v metodě `TestRefType`. Metoda `TestRefType` zobrazí jako výstup 33.

Další informace o tom, jak předat typy odkazu odkazem a podle hodnoty, naleznete v tématu [předávání parametrů typu odkazu](./passing-reference-type-parameters.md) a [odkazových typů](../../language-reference/keywords/reference-types.md).

## <a name="return-values"></a>Vrácené hodnoty

Metody mohou vracet hodnotu volajícímu. Pokud návratový typ, typ uvedený před názvem metody, není `void`, metoda může vracet hodnotu pomocí klíčového slova `return`. Příkaz s klíčovým slovem `return` následovaný hodnotou, která odpovídá typu vrácené hodnoty, vrátí tuto hodnotu volajícímu metody.

Hodnota může být vrácena volajícímu podle hodnoty nebo, počínaje C# 7,0, [odkazem](ref-returns.md). Hodnoty se vrátí volajícímu pomocí odkazu, pokud se v signatuře metody používá klíčové slovo `ref` a následuje každé klíčové slovo-1 `return`. Například následující signatura metody a příkaz return označují, že metoda vrací názvy proměnných `estDistance` odkazem na volajícího.

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

Klíčové slovo `return` také zastaví provádění metody. Pokud je návratový typ `void`, je příkaz `return` bez hodnoty stále užitečný k zastavení provádění metody. Bez klíčového slova `return` se Metoda zastaví, když dosáhne konce bloku kódu. Metody s návratovým typem, který není typu void, jsou vyžadovány k použití klíčového slova `return` pro vrácení hodnoty. Tyto dvě metody například používají klíčové slovo `return` pro vrácení celých čísel:

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

Chcete-li použít hodnotu vrácenou metodou, volající metoda může použít samotné volání metody kdekoli kdekoliv, kde bude stačit hodnota stejného typu. Vrácenou hodnotu můžete také přiřadit proměnné. Například následující dva příklady kódu mají stejný cíl:

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

Použití místní proměnné, v tomto případě `result` pro uložení hodnoty je volitelné. Může to usnadnit čitelnost kódu nebo může být nutné, pokud potřebujete uložit původní hodnotu argumentu pro celý rozsah metody.

Chcete-li použít hodnotu vrácenou odkazem z metody, je nutné deklarovat [místní proměnnou ref](ref-returns.md#ref-locals) , pokud máte v úmyslu změnit její hodnotu. Například pokud metoda `Planet.GetEstimatedDistance` vrátí hodnotu <xref:System.Double> odkazem, můžete ji definovat jako místní proměnnou ref s kódem podobným následujícímu:

```csharp
ref int distance = plant
```

Vrácení multidimenzionálního pole z metody `M`, které upraví obsah pole, není nutné, pokud volání funkce předává pole do `M`.  Výsledné pole můžete vracet z `M` pro dobrý styl nebo funkční tok hodnot, ale není nutné, protože C# předává všechny odkazové typy podle hodnoty a hodnota odkazu na pole je ukazatel na pole. V metodě `M` jsou všechny změny v obsahu pole pozorovatelované jakýmkoli kódem, který má odkaz na pole, jak je znázorněno v následujícím příkladu:

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

Další informace naleznete v tématu [return](../../language-reference/keywords/return.md).

## <a name="async-methods"></a>Asynchronní metody

Pomocí asynchronní funkce můžete vyvolat asynchronní metody bez použití explicitních zpětných volání nebo ruční rozdělení kódu napříč více metodami nebo lambda výrazy.

Pokud označíte metodu pomocí modifikátoru [Async](../../language-reference/keywords/async.md) , můžete použít operátor [await](../../language-reference/operators/await.md) v metodě. Když ovládací prvek dosáhne výrazu await v asynchronní metodě, ovládací prvek se vrátí volajícímu a průběh v metodě je pozastaven, dokud není dokončen očekávaný úkol. Po dokončení úlohy může provádění pokračovat v metodě.

> [!NOTE]
> Asynchronní metoda se vrátí volajícímu, když dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo získá na konec asynchronní metody, podle toho, co nastane dříve.

Asynchronní metoda může mít návratový typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> nebo void. Typ vrácené hodnoty void slouží hlavně k definování obslužných rutin událostí, kde je požadován návratový typ void. Asynchronní metoda, která vrací typ void, nemůže být očekávána a volající metody vracející typ void nemůže zachytit výjimky, které metoda vyvolá.

V následujícím příkladu je `DelayAsync` asynchronní metodou, která má návratový typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má příkaz `return`, který vrací celé číslo. Proto deklarace metody `DelayAsync` musí mít návratový typ `Task<int>`. Vzhledem k tomu, že návratový typ je `Task<int>`, vyhodnocení výrazu `await` v `DoSomethingAsync` vytvoří celé číslo, jak ukazuje následující příkaz: `int result = await delayTask`.

Metoda `startButton_Click` je příkladem asynchronní metody, která má návratový typ void. Vzhledem k tomu, že `DoSomethingAsync` je asynchronní metoda, musí být úloha volání `DoSomethingAsync` očekávána, jak ukazuje následující příkaz: `await DoSomethingAsync();`. Metoda `startButton_Click` musí být definována s modifikátorem `async`, protože metoda má výraz `await`.

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

Asynchronní metoda nemůže deklarovat všechny parametry [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) , ale může volat metody, které mají tyto parametry.

Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await](../concepts/async/index.md), [řízení toku v asynchronních programech](../concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../concepts/async/async-return-types.md).

## <a name="expression-body-definitions"></a>Definice textu výrazu

Je běžné mít definice metod, které se jednoduše vrátí s výsledkem výrazu nebo které mají jediný příkaz jako tělo metody. Pro definování takových metod pomocí `=>` je k dispozici zástupce syntaxe:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Pokud metoda vrátí `void` nebo je asynchronní metodou, pak tělo metody musí být výraz příkazu (totéž jako u výrazů lambda). U vlastností a indexerů musí být jen pro čtení a nepoužíváte klíčové slovo `get` přístupového objektu.

## <a name="iterators"></a>Iterátory

Iterátor provádí vlastní iteraci v kolekci, jako je například seznam nebo pole. Iterátor používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého elementu v jednom okamžiku. Při dosažení příkazu [yield return](../../language-reference/keywords/yield.md) se aktuální umístění v kódu pamatuje. Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.

Můžete zavolat iterátor z klientského kódu pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) .

Návratový typ iterátoru může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601>.

Další informace najdete v tématu [iterátory](../concepts/iterators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Statické třídy a jejich členové](static-classes-and-static-class-members.md)
- [Dědičnost](inheritance.md)
- [Abstraktní a uzavřené třídy a jejich členové](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [return](../../language-reference/keywords/return.md)
- [out](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [Předávání parametrů](passing-parameters.md)
