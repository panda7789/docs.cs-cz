---
title: Vytváření stromů výrazů
description: Další informace o technikách pro vytváření stromů výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146044"
---
# <a name="building-expression-trees"></a>Vytváření stromů výrazů

[Předchozí -- Interpretace výrazů](expression-trees-interpreting.md)

Všechny stromy výrazů, které jste dosud viděli, byly vytvořeny kompilátorem Jazyka C#. Jediné, co jste museli udělat, bylo vytvořit výraz lambda, `Expression<Func<T>>` který byl přiřazen proměnné zadané jako nebo nějaký podobný typ. To není jediný způsob, jak vytvořit strom výrazů. Pro mnoho scénářů můžete zjistit, že je třeba vytvořit výraz v paměti za běhu.

Vytváření stromů výrazů je komplikováno skutečností, že tyto stromy výrazů jsou neměnné. Být neměnný znamená, že musíte postavit strom od listů až ke kořeni. Api, která budete používat k vytváření stromů výrazů, odrážejí tuto skutečnost: Metody, které použijete k sestavení uzlu, berou všechny jeho podřízené položky jako argumenty. Pojďme si projít několik příkladů, které vám ukáží techniky.

## <a name="creating-nodes"></a>Vytváření uzlů

Začněme poměrně jednoduše znovu. Budeme používat výraz sčítání jsem pracoval s v těchto částech:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Chcete-li vytvořit tento strom výrazu, musíte vytvořit uzly listu.
Uzly listů jsou konstanty, takže `Expression.Constant` můžete použít metodu k vytvoření uzlů:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Dále vytvoříte výraz sčítání:

```csharp
var addition = Expression.Add(one, two);
```

Jakmile máte výraz sčítání, můžete vytvořit výraz lambda:

```csharp
var lambda = Expression.Lambda(addition);
```

Toto je velmi jednoduchý lambda výraz, protože neobsahuje žádné argumenty.
Dále v této části uvidíte, jak mapovat argumenty na parametry a vytvářet složitější výrazy.

Pro výrazy, které jsou stejně jednoduché jako tento, můžete kombinovat všechna volání do jednoho příkazu:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Budování stromu

To jsou základy vytváření stromu výrazů v paměti. Složitější stromy obecně znamenají více typů uzlů a více uzlů ve stromu. Pojďme projít ještě jeden příklad a ukázat další dva typy uzlů, které budete obvykle stavět při vytváření stromů výrazů: uzly argumentů a uzly volání metody.

Vytvořme strom výrazů pro vytvoření tohoto výrazu:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

Začnete vytvořením výrazů parametrů `x` `y`pro a:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Vytvoření výrazů násobení a sčítání se řídí vzorem, který jste již viděli:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Dále je třeba vytvořit výraz volání metody `Math.Sqrt`pro volání .

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

A nakonec vložíte volání metody do výrazu lambda a ujistěte se, že definujete argumenty výrazu lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

V tomto složitějším příkladu se zobrazí několik dalších technik, které budete často potřebovat k vytvoření stromů výrazů.

Nejprve je třeba vytvořit objekty, které představují parametry nebo místní proměnné před jejich použitím. Jakmile tyto objekty vytvoříte, můžete je použít ve stromu výrazů, kdekoli potřebujete.

Za druhé je třeba použít podmnožinu reflexe `MethodInfo` API k vytvoření objektu tak, že můžete vytvořit strom výrazpro přístup k této metodě. Musíte se omezit na podmnožinu rozhraní API reflexe, které jsou k dispozici na platformě .NET Core. Opět platí, že tyto techniky se rozšíří na jiné stromy výrazů.

## <a name="building-code-in-depth"></a>Stavební kód do hloubky

Nejste omezeni v tom, co můžete vytvořit pomocí těchto api. Složitější strom výrazů, který chcete vytvořit, je však obtížnější kód spravovat a číst.

Pojďme vytvořit strom výrazů, který je ekvivalentem tohoto kódu:

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

Všimněte si výše, že jsem nevytvořil strom výrazů, ale jednoduše delegát. Pomocí `Expression` třídy nelze vytvořit příkaz lambdas. Zde je kód, který je nutný k vytvoření stejné funkce. Je to složité tím, že neexistuje rozhraní API `while` pro vytvoření smyčky, místo toho je třeba vytvořit smyčku, která obsahuje podmíněný test a cíl popisku, který se z smyčky vymyká.

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

Kód pro vytvoření stromu výrazů pro faktoriální funkci je o něco delší, komplikovanější a je prošpikovaný popisky a příkazy break a dalšími prvky, kterým bychom se chtěli vyhnout v našich každodenních úkolech kódování.

V této části jsem také aktualizoval kód návštěvníka, aby navštívil každý uzel v tomto stromu výrazů a napsal informace o uzlech, které jsou vytvořeny v této ukázce. [Ukázkový kód](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) můžete zobrazit nebo stáhnout v úložišti GitHub dotnet/docs. Experimentujte sami sestavením a spuštěním vzorků. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Zkoumání api

Rozhraní API stromu výrazů jsou některé z obtížnější navigaci v .NET Core, ale to je v pořádku. Jejich účelem je poměrně složitý podnik: psaní kódu, který generuje kód za běhu. Jsou nutně složité poskytnout rovnováhu mezi podporou všech řídicích struktur, které jsou k dispozici v jazyce C# a udržování plochy rozhraní API tak malé, jak je rozumné. Toto vyvážení znamená, že mnoho řídicích struktur jsou reprezentovány ne jejich C# konstrukce, ale konstrukce, které představují základní logiku, kterou kompilátor generuje z těchto vyšší úrovně konstrukce.

Také v tomto okamžiku existují výrazy Jazyka C#, `Expression` které nelze sestavit přímo pomocí metod třídy. Obecně se jedná o nejnovější operátory a výrazy přidané v C# 5 a C# 6. (Například `async` výrazy nelze sestavit a `?.` nový operátor nelze přímo vytvořit.)

[Další -- Překlad výrazů](expression-trees-translating.md)
