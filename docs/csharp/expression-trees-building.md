---
title: Sestavování stromů výrazů
description: Přečtěte si o technikách vytváření stromů výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 45628b00633c8d6ff51dbd5f5dbdda7ca25dd7c4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037097"
---
# <a name="building-expression-trees"></a>Sestavování stromů výrazů

[Předchozí--interpretující výrazy](expression-trees-interpreting.md)

Všechny stromy výrazů, které jste viděli, zatím byly vytvořeny C# kompilátorem. Vše, co jste museli udělat, byl vytvořit lambda výraz, který byl přiřazen proměnné typu jako `Expression<Func<T>>` nebo podobným typem. To není jediný způsob, jak vytvořit strom výrazu. V mnoha scénářích se můžete setkat s tím, že je potřeba vytvořit výraz v paměti za běhu. 

Sestavování stromů výrazů je komplikované skutečností, že tyto stromy výrazů jsou neměnné. Neměnné znamená, že je nutné vytvořit strom ze všech listů až po kořen. Rozhraní API, která použijete k sestavení stromů výrazů, odráží tuto skutečnost: metody, které použijete k sestavení uzlu, přebírají všechny své podřízené položky jako argumenty. Podívejme se na několik příkladů a ukážeme vám techniky.

## <a name="creating-nodes"></a>Vytváření uzlů

Pojďme začít poměrně znovu. Použijeme výraz sčítání, se kterým pracujete v těchto částech:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Chcete-li vytvořit tento strom výrazů, je nutné vytvořit listové uzly.
Uzly listu jsou konstanty, takže můžete pomocí metody `Expression.Constant` vytvořit uzly:

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

Toto je velmi jednoduchý výraz lambda, protože neobsahuje žádné argumenty.
Později v této části se dozvíte, jak namapovat argumenty na parametry a sestavovat složitější výrazy.

Pro výrazy, které jsou stejně jednoduché jako tyto, můžete zkombinovat všechna volání do jednoho příkazu:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Sestavování stromu

To je základy vytváření stromu výrazů v paměti. Složitější stromy obecně znamenají více typů uzlů a další uzly ve stromové struktuře. Pojďme spustit více než jeden příklad a zobrazit dva další typy uzlů, které obvykle sestavíte při vytváření stromů výrazů: uzly argumentů a uzly volání metody.

Pojďme sestavit strom výrazu pro vytvoření tohoto výrazu:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Začnete vytvořením výrazů parametrů pro `x` a `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Vytváření výrazů násobení a sčítání se řídí vzorem, který jste už viděli:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Dále je nutné vytvořit výraz volání metody pro volání `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

A nakonec vložte volání metody do výrazu lambda a nezapomeňte definovat argumenty pro výraz lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

V tomto složitějším příkladu vidíte několik dalších technik, které často budete potřebovat k vytváření stromů výrazů.

Nejprve musíte vytvořit objekty, které reprezentují parametry nebo lokální proměnné, než je použijete. Jakmile tyto objekty vytvoříte, můžete je ve stromové struktuře výrazu použít všude, kde potřebujete.

Za druhé, je nutné použít podmnožinu rozhraní API pro reflexi a vytvořit objekt `MethodInfo`, abyste mohli vytvořit strom výrazů pro přístup k této metodě. Musíte se omezit na podmnožinu rozhraní API pro reflexi, která jsou k dispozici na platformě .NET Core. Tyto techniky se znovu rozšíří do dalších stromů výrazů.

## <a name="building-code-in-depth"></a>Sestavování kódu v Hloubkě

Nejste omezeni tím, co můžete pomocí těchto rozhraní API sestavit. Avšak Složitější strom výrazů, který chcete sestavit, je obtížnější kód spravovat a číst. 

Pojďme sestavit strom výrazu, který je ekvivalentem tohoto kódu:

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

Všimněte si, že se strom výrazů nesestavil, ale stačí ho jednoduše delegovat. Pomocí třídy `Expression` nelze sestavit výrazy lambda příkazů. Zde je kód, který je vyžadován pro sestavení stejné funkce. Je to komplikované, že není k dispozici rozhraní API pro sestavení smyčky `while`, místo toho je nutné vytvořit smyčku, která obsahuje podmíněný test, a cíl popisku k přerušení smyčky. 

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

Kód pro sestavování stromu výrazů pro funkci faktoriál je poměrně složitý a složitější a je riddled pomocí popisků a příkazů Break a dalších prvků, které bychom se chtěli vyhnout při každodenních úlohách kódování. 

V této části jsem také aktualizovali kód návštěvníka k návštěvě všech uzlů v tomto stromu výrazů a zapisuje informace o uzlech, které jsou vytvořeny v této ukázce. [Vzorový kód můžete zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) v úložišti GitHub/docs. Experimentujte sami vytvořením a spuštěním ukázek. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Zkoumání rozhraní API

Rozhraní API stromu výrazů jsou trochu obtížnější navigovat v .NET Core, ale to je dobré. Jejich účelem je spíše složitý závazek: psaní kódu, který generuje kód za běhu. Jsou nutně komplikované, aby poskytovaly rovnováhu mezi podporou všech řídicích struktur dostupných v C# jazyce a udržení oblasti povrchu rozhraní API tak, jak je co nejmenší. Tento zůstatek znamená, že mnoho řídicích struktur je zastoupena C# bez jejich konstrukcí, ale konstrukce, které představují základní logiku, kterou kompilátor generuje z těchto konstrukcí vyšší úrovně. 

V tuto chvíli existují C# výrazy, které nemohou být sestaveny přímo pomocí metod`Expression`třídy. Obecně platí, že se jedná o nejnovější operátory a výrazy přidané v C# 5 a C# 6. (Například `async` výrazy nelze sestavit a Nový operátor `?.` nelze vytvořit přímo.)

[Další--překládání výrazů](expression-trees-translating.md)
