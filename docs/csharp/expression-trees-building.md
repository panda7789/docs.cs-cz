---
title: Vytváření stromů výrazů
description: Další informace o technikách pro vytváření stromů výrazů.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7751af17aafa8e2d1a14125da43352108b1c1f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646594"
---
# <a name="building-expression-trees"></a>Vytváření stromů výrazů

[Předchozí – Interpretace výrazů](expression-trees-interpreting.md)

Stromy výrazů jste zatím viděli se vytvořila C# kompilátoru. Vše museli dělat bylo vytvořit výraz lambda, který byl přiřazen proměnné typu `Expression<Func<T>>` nebo podobný typ. To není jediný způsob, jak vytvořit strom výrazu. Pro mnoho scénářů možná zjistíte, že budete muset sestavit výraz v paměti za běhu. 

Vytváření stromů výrazů je složité fakt, že tyto stromů výrazů jsou neměnné. Je neměnný znamená, že je nutné vytvořit z listy až po kořen stromu. Rozhraní API, které budete používat k vytváření stromů výrazů, aby odrážela tuto skutečnost: Jako argumenty metod, které použijete k vytvoření uzlu přijímat všechny jeho podřízené objekty. Projděme si několik příkladů, chcete-li zobrazit technik.

## <a name="creating-nodes"></a>Vytvoření uzlů

Začněme relativně jednoduše znovu. Přidání výrazu, které Pracuji s použijeme v těchto částech:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

K vytvoření tohoto stromu výrazu, je nutné vytvořit uzly listů.
Listové uzly jsou konstanty, takže můžete používat `Expression.Constant` metodu pro vytvoření uzly:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

V dalším kroku sestavíte Přidání výrazu:

```csharp
var addition = Expression.Add(one, two);
```

Jakmile máte Přidání výrazu, můžete vytvořit lambda výrazu:

```csharp
var lambda = Expression.Lambda(addition);
```

To je velmi jednoduchý lambda výraz, protože neobsahuje žádné argumenty.
Později v této části, zobrazí se vám mapování argumentů do parametrů a složitější výrazy.

Pro výrazy, které jsou stejně jednoduché jako to předchozí může kombinovat všechna volání do jednoho příkazu:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Vytvoření větve

Který se se základy vytváření stromu výrazů v paměti. Složitější stromů obecně znamená další typy uzlů a více uzlů ve stromu. Umožňuje spustit prostřednictvím jednoho další příklad a zobrazit dva další typy uzlů, které se obvykle sestaví při vytváření stromů výrazů: argument uzly a uzly volání metody.

Vytvořme strom výrazu. Chcete-li vytvořit tento výraz:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Začnete vytvořením výrazech pro parametry pro `x` a `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Vytváření výrazů násobení a přidání následuje vzor, který jste už viděli:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Dále je třeba vytvořit výraz volání metody pro volání `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

A konečně, umístěte volání metody na výraz lambda, ujistěte se, že k definování argumenty výrazu lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

V tomto příkladu složitější uvidíte několik další techniky, které se často potřebujete k vytvoření stromů výrazu.

Nejprve musíte vytvořit objekty, které představují parametry nebo lokální proměnné, před jejich použitím. Po vytvoření těchto objektů, můžete ho použít ve vaší strom výrazu, bez ohledu na to budete potřebovat.

Za druhé, budete muset použít podmnožinu rozhraní API reflexe k vytvoření `MethodInfo` objektu tak, že vytvoříte strom výrazů pro přístup k této metodě. Je třeba sami omezit na podmnožinu rozhraní API reflexe, které jsou k dispozici na platformě .NET Core. Tyto postupy znovu, rozšíří na další stromy výrazů.

## <a name="building-code-in-depth"></a>Vytváření kódu do hloubky

Nejsou omezeni v co lze sestavit pomocí těchto rozhraní API. Nicméně Čím více složité strom výrazu, který chcete sestavit, tím obtížnější je kód, spravovat a ke čtení. 

Vytvořme strom výrazů, který je ekvivalentem tohoto kódu:

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

Všimněte si, že výše uvedené, že mám nesestavili strom výrazu, ale jednoduše delegáta. Použití `Expression` třída, nelze sestavit příkazové lambdy. Tady je kód, který je nutné k vytvoření stejné funkce. Je složité fakt, že není rozhraní API pro vytváření `while` smyčky, místo toho budete muset sestavit smyčku, která obsahuje podmíněný test a cíl popisek, který má přerušit ze smyčky. 

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

Kód k vytvoření stromu výrazu pro funkci faktoriálu je poměrně o něco delší složitější, a je riddled s popisky a příkazy break a další prvky, které jsme chtěli vyhnout v naší běžné úlohy kódování. 

Pro tento oddíl jsem také jsme aktualizovali kód návštěvníka navštívit každý uzel ve stromu tohoto výrazu a vypsat informace o uzlech, které jsou vytvořeny v této ukázce. Je možné [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) v úložišti dotnet/docs GitHub. Vyzkoušejte si to sami sestavováním a spouštěním ukázek. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Zkoumání rozhraní API

Strom výrazu rozhraní API jsou některé z obtížnější pro navigaci v .NET Core, ale to je v pořádku. Jejich účelem je spíše složitý proces: psaní kódu, který generuje kód za běhu. Jsou nutně složité zajistit rovnováhu mezi podpora k dispozici v řídicích struktur C# jazyka a udržování rozumné plochy rozhraní API jako malé. Této rovnováhy znamená, že mnoho řídících struktur jsou reprezentovány není podle jejich C# vytvoří, ale vytvoří pomocí konstrukce, které představují základní logiku, která generuje kompilátor z těchto vyšší úrovně. 

V tuto chvíli k dispozici je také C# výrazy, které se nedají vytvářet přímo pomocí `Expression` metody třídy. Obecně platí, bude se jednat o nejnovější operátory a výrazy přidá C# 5 a C# 6. (Například `async` výrazů nemůže být vytvořena a nové `?.` operátor nelze vytvořit přímo.)

[Další – Překlad výrazů](expression-trees-translating.md)
