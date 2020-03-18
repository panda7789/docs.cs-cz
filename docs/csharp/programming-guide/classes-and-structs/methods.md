---
title: Metody – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 114fa2973c50be9a4199db9729e3cd9ea6122866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626526"
---
# <a name="methods-c-programming-guide"></a>Metody (Průvodce programováním v C#)

Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že příkazy, které mají být provedeny voláním metody a zadáním všechny argumenty požadované metody. V C# každá provedená instrukce se provádí v kontextu metody. Metoda `Main` je vstupníbod pro každou aplikaci Jazyka C# a je volána za běhu common jazyka (CLR) při spuštění programu.

> [!NOTE]
> Tento článek popisuje pojmenované metody. Informace o anonymních funkcích naleznete [v tématu Anonymní funkce](../statements-expressions-operators/anonymous-functions.md).

## <a name="method-signatures"></a>Podpisy metod

Metody jsou deklarovány ve [třídě](../../language-reference/keywords/class.md), [struktuře](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../interfaces/index.md) zadáním úrovně přístupu, jako `public` jsou nebo `private`, volitelné modifikátory, jako `abstract` jsou nebo `sealed`, vrácená hodnota, název metody a všechny parametry metody. Tyto části dohromady jsou podpisem metody.

> [!NOTE]
> Návratový typ metody není součástí podpisu metody pro účely přetížení metody. Je však součástí podpisu metody při určování kompatibility mezi delegátem a metodou, na kterou odkazuje.

Parametry metody jsou uzavřeny v závorce a jsou odděleny čárkami. Prázdné závorky označují, že metoda nevyžaduje žádné parametry. Tato třída obsahuje čtyři metody:

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a>Přístup k metodě

Volání metody na objekt je jako přístup k poli. Za název objektu přidejte tečku, název metody a závorky. Argumenty jsou uvedeny v závorce a jsou odděleny čárkami. Metody třídy `Motorcycle` proto lze volat jako v následujícím příkladu:

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a>Parametry metody vs. argumenty

Definice metody určuje názvy a typy všech požadovaných parametrů. Při volání kódu volá metodu, poskytuje konkrétní hodnoty nazývané argumenty pro každý parametr. Argumenty musí být kompatibilní s typem parametru, ale název argumentu (pokud existuje) použitý v volajícím kódu nemusí být stejný jako parametr pojmenovaný definovaný v metodě. Například:

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a>Předání odkazem vs. předávání hodnotou

Ve výchozím nastavení, když je instance [typu hodnoty](../../language-reference/builtin-types/value-types.md) předána metodě, její kopie je předána namísto samotné instance. Proto změny argumentu nemají žádný vliv na původní instance v volající metody. Chcete-li předat instanci typu `ref` hodnoty odkazem, použijte klíčové slovo. Další informace naleznete [v tématu Předávání parametrů typu hodnoty](./passing-value-type-parameters.md).

Pokud je objekt typu odkazu předán metodě, je předán odkaz na objekt. To znamená, že metoda neobdrží samotný objekt, ale argument, který označuje umístění objektu. Pokud změníte člen objektu pomocí tohoto odkazu, změna se projeví v argumentu v volající metodě, i když objekt předáte hodnotou.

Typ odkazu vytvoříte pomocí `class` klíčového slova, jak ukazuje následující příklad:

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

Nyní pokud předáte objekt, který je založen na tomto typu metodě, je předán odkaz na objekt. Následující příklad předá objekt `SampleRefType` typu `ModifyObject`metodě :

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

Příklad dělá v podstatě totéž jako předchozí příklad v tom, že předá argument podle hodnoty metodě. Ale protože se používá typ odkazu, výsledek je jiný. Změna provedená v `ModifyObject` `value` poli parametru , `obj`také změní `value` pole argumentu `rt`, `TestRefType` v metodě. Metoda `TestRefType` zobrazí 33 jako výstup.

Další informace o předávání typů odkazů odkazem a hodnotou naleznete [v tématu Předávání parametrů typu odkazu](./passing-reference-type-parameters.md) a typů [odkazů](../../language-reference/keywords/reference-types.md).

## <a name="return-values"></a>Vrácené hodnoty

Metody můžete vrátit hodnotu volajícímu. Pokud návratový typ, typ uvedený před názvem `void`metody, není , metoda `return` může vrátit hodnotu pomocí klíčového slova. Příkaz s `return` klíčovým slovem následovaný hodnotou, která odpovídá návratový typ vrátí tuto hodnotu volajícímu metody.

Hodnota může být vrácena volajícímu podle hodnoty nebo, počínaje C# 7.0, [odkazem](ref-returns.md). Hodnoty jsou vráceny volajícímu `ref` odkazem, pokud je klíčové slovo `return` použito v podpisu metody a následuje každé klíčové slovo. Například následující metoda podpis a příkaz return označují, `estDistance` že metoda vrátí názvy proměnných odkazem na volajícího.

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

Klíčové `return` slovo také zastaví provádění metody. Pokud je `void`návratový `return` typ , příkaz bez hodnoty je stále užitečné zastavit provádění metody. Bez `return` klíčového slova se metoda zastaví při dosažení konce bloku kódu. Metody s nevoid návratový typ jsou `return` nutné použít klíčové slovo vrátit hodnotu. Například tyto dvě metody `return` používají klíčové slovo k vrácení celá čísla:

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

Chcete-li použít hodnotu vrácenou z metody, může metoda volání použít metodu, která se nazývá kdekoli, že by stačila hodnota stejného typu. Návratovou hodnotu můžete také přiřadit proměnné. Například následující dva příklady kódu dosáhnout stejného cíle:

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

Použití místní proměnné, v `result`tomto případě , k uložení hodnoty je volitelné. Může pomoci čitelnost kódu nebo může být nezbytné, pokud potřebujete uložit původní hodnotu argumentu pro celý rozsah metody.

Chcete-li použít hodnotu vrácenou odkazem z metody, musíte deklarovat místní proměnnou [ref,](ref-returns.md#ref-locals) pokud máte v úmyslu změnit její hodnotu. Pokud například `Planet.GetEstimatedDistance` metoda vrátí <xref:System.Double> hodnotu odkazem, můžete ji definovat jako místní proměnnou ref s následujícím kódem:

```csharp
ref int distance = plant
```

Vrácení vícerozměrné pole z metody `M`, která upravuje obsah pole není nutné, pokud volající funkce `M`předána pole do .  Můžete vrátit výsledné pole `M` z pro dobrý styl nebo funkční tok hodnot, ale není nutné, protože C# předá všechny typy odkazů podle hodnoty a hodnota odkazu pole je ukazatel na pole. V metodě `M`jsou všechny změny obsahu pole pozorovatelné libovolným kódem, který má odkaz na pole, jak je znázorněno v následujícím příkladu:

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

Pomocí funkce async můžete vyvolat asynchronní metody bez použití explicitních zpětných volání nebo ručnírozdělení kódu mezi více metod nebo výrazy lambda.

Pokud označíte metodu s [asynchronním](../../language-reference/keywords/async.md) modifikátorem, můžete použít operátor [await](../../language-reference/operators/await.md) v metodě. Když ovládací prvek dosáhne výrazu await v asynchronní metodě, ovládací prvek se vrátí volajícímu a průběh metody je pozastaven, dokud nebude dokončena očekávaná úloha. Po dokončení úlohy může spuštění pokračovat v metodě.

> [!NOTE]
> Asynchronní metoda se vrátí volajícímu, když buď narazí na první očekávaný objekt, který ještě není dokončen, nebo se dostane na konec asynchronní metody, podle toho, co nastane dříve.

Asynchronní metoda může mít <xref:System.Threading.Tasks.Task%601>návratový typ , <xref:System.Threading.Tasks.Task>nebo void. Typ vrácení void se používá především k definování obslužné rutiny událostí, kde je vyžadován prázdný návratový typ. Asynchronní metoda, která vrátí void nelze čekat a volající metody vrácení void nemůže zachytit výjimky, které metoda vyvolá.

V následujícím příkladu je asynchronní metoda, `DelayAsync` <xref:System.Threading.Tasks.Task%601>která má návratový typ . `DelayAsync`má `return` příkaz, který vrací celé číslo. Proto musí mít `DelayAsync` deklarace metody `Task<int>`návratový typ . Vzhledem k `Task<int>`tomu, že `await` návratový `DoSomethingAsync` typ je , vyhodnocení výrazu v `int result = await delayTask`vytváří celé číslo jako následující příkaz ukazuje: .

Metoda `startButton_Click` je příkladem asynchronní metody, která má návratový typ void. Protože `DoSomethingAsync` je asynchronní metoda, `DoSomethingAsync` úkol pro volání musí být očekávány, `await DoSomethingAsync();`jak ukazuje následující příkaz: . Metoda `startButton_Click` musí být definována modifikátorem, `async` protože metoda má `await` výraz.

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

Asynchronní metoda nemůže deklarovat žádné parametry [ref](../../language-reference/keywords/ref.md) nebo [out,](../../language-reference/keywords/out-parameter-modifier.md) ale může volat metody, které mají takové parametry.

Další informace o asynchronních metodách naleznete [v tématu Asynchronní programování s asynchronní a await](../concepts/async/index.md), [Řízení toku v asynchronních programech](../concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../concepts/async/async-return-types.md).

## <a name="expression-body-definitions"></a>Definice těla výrazu

Je běžné mít definice metod, které jednoduše vrátit okamžitě s výsledkem výrazu nebo které mají jeden příkaz jako tělo metody. Existuje zástupce syntaxe pro definování `=>`těchto metod pomocí :

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Pokud metoda `void` vrátí nebo je asynchronní metoda, pak tělo metody musí být výraz příkazu (stejné jako u lambdas). Pro vlastnosti a indexery musí být jen pro `get` čtení a nepoužíváte klíčové slovo přistupujícího objektu.

## <a name="iterators"></a>Iterátory

Iterátor provádí vlastní iteraci přes kolekci, jako je například seznam nebo pole. Iterátor používá yield [return](../../language-reference/keywords/yield.md) prohlášení vrátit každý prvek jeden po druhém. Když je dosaženo výnos [return](../../language-reference/keywords/yield.md) prohlášení, aktuální umístění v kódu je zapamatována. Spuštění je restartován z tohoto umístění při restartování iterátoru při příštím volání.

Volání iterátoru z kódu klienta pomocí [foreach](../../language-reference/keywords/foreach-in.md) prohlášení.

Návratový typ iterátoru může <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>být <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>, , nebo .

Další informace naleznete v tématu [Iterators](../concepts/iterators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Statické třídy a jejich členové](static-classes-and-static-class-members.md)
- [Dědičnost](inheritance.md)
- [Abstraktní a uzavřené třídy a jejich členové](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [return](../../language-reference/keywords/return.md)
- [ven](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [Předávání parametrů](passing-parameters.md)
