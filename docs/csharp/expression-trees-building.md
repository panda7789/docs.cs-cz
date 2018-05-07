---
title: Vytváření stromů výrazů
description: Další informace o technikách pro vytváření stromů výrazů.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 52e03bd1ea2635d75da6d70af6918b33b64622b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="building-expression-trees"></a>Vytváření stromů výrazů

[Předchozí – Interpretace výrazy](expression-trees-interpreting.md)

Všechny stromů výrazů, které jste se seznámili s, pokud byla vytvořena kompilátor jazyka C#. Všechny jste museli provést byl vytvoření výrazu lambda, kterému byla přiřazena k proměnné typu `Expression<Func<T>>` nebo podobné typ. Která není jedinou možností, jak vytvořit strom výrazu se nezdařilo. Pro mnoho scénářů s můžete zjistit, které potřebujete k vytvoření výrazu v paměti za běhu. 

Vytváření stromů výrazů ztěžuje skutečnost, že jsou tyto stromů výrazů neměnné. Probíhá neměnné znamená, že musíte sestavit z nechá až kořenu stromu. Rozhraní API, které použijete k sestavení stromů výrazů odrážela tuto skutečnost: metody, které použijete k vytvoření uzlu trvat všechny její podřízené položky jako argumenty. Projděme několik příkladů tak, aby zobrazovalo technik.

## <a name="creating-nodes"></a>Vytvoření uzlů

Začněme relativně jednoduše znovu. Použijeme přidání výraz, který I jste pracovali v těchto částech:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Chcete-li vytvořit tento strom výrazu, je nutné vytvořit uzlů listu.
Uzlů listu jsou konstanty, abyste mohli používat `Expression.Constant` metodu pro vytvoření uzly:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Dále budete sestavení výrazu přidání:

```csharp
var addition = Expression.Add(one, two);
```

Jakmile máte Přidání výrazu, můžete vytvořit výrazu lambda:

```csharp
var lamdba = Expression.Lambda(addition);
```

Toto je velmi jednoduchý LambdaExpression, protože neobsahuje žádné argumenty.
Později v této části se zobrazí postup namapovat argumenty parametrů a složitější výrazy se vytvářejí.

Pro výrazy, které jsou stejně jednoduché jako to předchozí můžou kombinovat všechna volání do jednoho příkazu:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Vytváření stromu

To je základní informace o vytváření strom výrazu v paměti. Složitější stromy obvykle znamená další typy uzlů a další uzly ve stromu. Umožňuje spustit prostřednictvím jednoho další příklad a zobrazit dva další typy uzlů, které obvykle vytvoříte při vytváření stromů výrazů: argument uzlů a uzly volání metody.

Vytvořme strom výrazu se nezdařilo vytvořit tento výraz:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Budete začněte vytvořením výrazech parametrů pro `x` a `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Vzor, který jste už viděli vytváření výrazy násobení a přidání takto:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Dále musíte vytvořit výraz volání metody pro volání `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

A nakonec uvést volání metody do výrazu lambda, nezapomeňte zadat argumenty výrazu lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

V tomto příkladu složitější zobrazí několik další techniky, které často bude potřeba vytvořit stromů výrazů.

Nejprve musíte vytvořit objekty, které představují parametry nebo lokální proměnné dříve, než je použijete. Po vytvoření těchto objektů, můžete je používat v vaší strom výrazu, vždy, když potřebujete.

Druhý, budete muset použít podmnožinu rozhraní API reflexe k vytvoření `MethodInfo` objektu tak, že můžete vytvořit strom výrazu pro přístup k dané metody. Je nutné sami omezit na podmnožinu rozhraní API reflexe, které jsou k dispozici na platformě .NET Core. Tyto postupy se znovu rozšířit jiných stromů výrazů.

## <a name="building-code-in-depth"></a>Vytváření kódu v hloubka

Nejsou omezené v si můžete vytvořit pomocí těchto rozhraní API. Čím více však komplikovanější strom výrazu, který chcete vytvořit, tím složitější kód je spravovat a číst. 

Vytvořme strom výrazu, který je ekvivalentem tohoto kódu:

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

Všimněte si výše, I není sestavení strom výrazu, ale jednoduše delegát. Pomocí `Expression` třídy, nemůže vytvořit lambda. Zde je kód, který je potřeba vytvořit stejné funkce. Ztěžuje fakt, že není k dispozici rozhraní API pro sestavení `while` smyčky, místo toho potřebujete k vytváření smyčku, který obsahuje testu podmíněného a cíl popisek pro přerušení mimo smyčku. 

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

Kód k vytvoření strom výrazu pro funkci faktoriálu je poměrně trochu delší složitěji, a je riddled s popisky a zalomení příkazy a další prvky, kterou jsme chtěli vyhnout v našem každý den kódování úlohy. 

Pro tento oddíl I taky aktualizovali kód návštěvníka navštívit každý uzel v tomto výrazu stromu a zapsat informace o uzly, které jsou vytvořené v této ukázce. Můžete [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) v úložišti GitHub dotnet/docs. Vytváření a spuštěním ukázky experimentovat sami. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Zkoumání rozhraní API

Strom výrazu rozhraní API jsou některé obtížnější přejděte v .NET Core, ale není to. Jejich účelem je spíš složitý proces: psaní kódu, který generuje kód za běhu. Jsou to nutně složitá zajistit rovnováhu mezi podpora všechny řídicí struktury dostupné v jazyce C# a udržování co přiměřené možnosti útoku na rozhraní API. Toto vyrovnávání znamená, že mnoho řídicí struktury jsou reprezentované není podle jejich konstrukce jazyka C#, nikoli podle konceptů, které představují základní logiku, která kompilátor generuje na základě těchto konstrukce vyšší úrovně. 

V tuto chvíli k dispozici je také výrazy jazyka C#, které nelze sestavit přímo pomocí `Expression` metody třídy. Obecně platí tyto bude nejnovější operátory a výrazy přidali v C# 5 a 6 C#. (Například `async` výrazy nelze vytvořili a nové `?.` operátor nelze vytvořit přímo.)

[Další – Překladu výrazy](expression-trees-translating.md)
