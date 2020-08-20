---
title: Sestavování stromů výrazů
description: Přečtěte si o technikách vytváření stromů výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c153ca2c75738571c81057364390f489d2decb05
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656147"
---
# <a name="building-expression-trees"></a><span data-ttu-id="bb2ce-103">Sestavování stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="bb2ce-103">Building Expression Trees</span></span>

[<span data-ttu-id="bb2ce-104">Předchozí--interpretující výrazy</span><span class="sxs-lookup"><span data-stu-id="bb2ce-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="bb2ce-105">Všechny stromy výrazů, které jste viděli zatím, byly vytvořeny kompilátorem jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="bb2ce-106">Vše, co jste museli udělat, byl vytvořit lambda výraz, který byl přiřazen proměnné typu jako `Expression<Func<T>>` nebo podobný podobnému typu.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="bb2ce-107">To není jediný způsob, jak vytvořit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="bb2ce-108">V mnoha scénářích se můžete setkat s tím, že je potřeba vytvořit výraz v paměti za běhu.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="bb2ce-109">Sestavování stromů výrazů je komplikované skutečností, že tyto stromy výrazů jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="bb2ce-110">Neměnné znamená, že je nutné vytvořit strom ze všech listů až po kořen.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="bb2ce-111">Rozhraní API, která použijete k sestavení stromů výrazů, odráží tuto skutečnost: metody, které použijete k sestavení uzlu, přebírají všechny své podřízené položky jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="bb2ce-112">Podívejme se na několik příkladů a ukážeme vám techniky.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="bb2ce-113">Vytváření uzlů</span><span class="sxs-lookup"><span data-stu-id="bb2ce-113">Creating Nodes</span></span>

<span data-ttu-id="bb2ce-114">Pojďme začít poměrně znovu.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-114">Let's start relatively simply again.</span></span> <span data-ttu-id="bb2ce-115">Použijeme výraz sčítání, se kterým pracujete v těchto částech:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="bb2ce-116">Chcete-li vytvořit tento strom výrazů, je nutné vytvořit listové uzly.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="bb2ce-117">Uzly listu jsou konstanty, takže můžete použít `Expression.Constant` metodu k vytvoření uzlů:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="bb2ce-118">Dále vytvoříte výraz sčítání:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="bb2ce-119">Jakmile máte výraz sčítání, můžete vytvořit výraz lambda:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="bb2ce-120">Toto je velmi jednoduchý výraz lambda, protože neobsahuje žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="bb2ce-121">Později v této části se dozvíte, jak namapovat argumenty na parametry a sestavovat složitější výrazy.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="bb2ce-122">Pro výrazy, které jsou stejně jednoduché jako tyto, můžete zkombinovat všechna volání do jednoho příkazu:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="bb2ce-123">Sestavování stromu</span><span class="sxs-lookup"><span data-stu-id="bb2ce-123">Building a Tree</span></span>

<span data-ttu-id="bb2ce-124">To je základy vytváření stromu výrazů v paměti.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="bb2ce-125">Složitější stromy obecně znamenají více typů uzlů a další uzly ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="bb2ce-126">Pojďme spustit více než jeden příklad a zobrazit dva další typy uzlů, které obvykle sestavíte při vytváření stromů výrazů: uzly argumentů a uzly volání metody.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="bb2ce-127">Pojďme sestavit strom výrazu pro vytvoření tohoto výrazu:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="bb2ce-128">Začnete vytvořením výrazů parametrů pro `x` a `y` :</span><span class="sxs-lookup"><span data-stu-id="bb2ce-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="bb2ce-129">Vytváření výrazů násobení a sčítání se řídí vzorem, který jste už viděli:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="bb2ce-130">Dále musíte vytvořit výraz volání metody pro volání `Math.Sqrt` .</span><span class="sxs-lookup"><span data-stu-id="bb2ce-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="bb2ce-131">A nakonec vložte volání metody do výrazu lambda a nezapomeňte definovat argumenty pro výraz lambda:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="bb2ce-132">V tomto složitějším příkladu vidíte několik dalších technik, které často budete potřebovat k vytváření stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="bb2ce-133">Nejprve musíte vytvořit objekty, které reprezentují parametry nebo lokální proměnné, než je použijete.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="bb2ce-134">Jakmile tyto objekty vytvoříte, můžete je ve stromové struktuře výrazu použít všude, kde potřebujete.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="bb2ce-135">Za druhé, je nutné použít podmnožinu rozhraní API reflexe k vytvoření `MethodInfo` objektu, abyste mohli vytvořit strom výrazu pro přístup k této metodě.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="bb2ce-136">Musíte se omezit na podmnožinu rozhraní API pro reflexi, která jsou k dispozici na platformě .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="bb2ce-137">Tyto techniky se znovu rozšíří do dalších stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="bb2ce-138">Sestavování kódu v Hloubkě</span><span class="sxs-lookup"><span data-stu-id="bb2ce-138">Building Code In Depth</span></span>

<span data-ttu-id="bb2ce-139">Nejste omezeni tím, co můžete pomocí těchto rozhraní API sestavit.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="bb2ce-140">Avšak Složitější strom výrazů, který chcete sestavit, je obtížnější kód spravovat a číst.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="bb2ce-141">Pojďme sestavit strom výrazu, který je ekvivalentem tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="bb2ce-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="bb2ce-142">Všimněte si, že se strom výrazů nesestavil, ale stačí ho jednoduše delegovat.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="bb2ce-143">Pomocí `Expression` třídy nelze sestavit výrazy lambda příkazů.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="bb2ce-144">Zde je kód, který je vyžadován pro sestavení stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="bb2ce-145">Je to komplikované, že není k dispozici rozhraní API k vytvoření `while` smyčky, místo toho je nutné vytvořit smyčku, která obsahuje podmíněný test, a cíl popisku k přerušení smyčky.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

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

<span data-ttu-id="bb2ce-146">Kód pro sestavování stromu výrazů pro funkci faktoriál je poměrně složitý a složitější a je riddled pomocí popisků a příkazů Break a dalších prvků, které bychom se chtěli vyhnout při každodenních úlohách kódování.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="bb2ce-147">V této části jsem také aktualizovali kód návštěvníka k návštěvě všech uzlů v tomto stromu výrazů a zapisuje informace o uzlech, které jsou vytvořeny v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="bb2ce-148">[Vzorový kód můžete zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) v úložišti GitHub/docs.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="bb2ce-149">Experimentujte sami vytvořením a spuštěním ukázek.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="bb2ce-150">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="bb2ce-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="bb2ce-151">Zkoumání rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bb2ce-151">Examining the APIs</span></span>

<span data-ttu-id="bb2ce-152">Rozhraní API stromu výrazů jsou trochu obtížnější navigovat v .NET Core, ale to je dobré.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="bb2ce-153">Jejich účelem je spíše složitý závazek: psaní kódu, který generuje kód za běhu.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="bb2ce-154">Jsou nutně komplikované, aby poskytovaly rovnováhu mezi podporou všech řídicích struktur dostupných v jazyce C# a udržení oblasti povrchu rozhraní API co nejmenších.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="bb2ce-155">Toto vyvážení znamená, že mnoho řídicích struktur je reprezentovaných konstrukcemi jazyka C#, ale konstrukcemi, které představují základní logiku, kterou kompilátor generuje z těchto konstrukcí vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="bb2ce-156">V tuto chvíli také existují výrazy jazyka C#, které nelze sestavit přímo pomocí `Expression` metod třídy.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="bb2ce-157">Obecně platí, že se jedná o nejnovější operátory a výrazy přidané v jazyce C# 5 a C# 6.</span><span class="sxs-lookup"><span data-stu-id="bb2ce-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="bb2ce-158">(Například `async` výrazy nelze sestavit a `?.` operátor New nelze vytvořit přímo.)</span><span class="sxs-lookup"><span data-stu-id="bb2ce-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="bb2ce-159">Další--překládání výrazů</span><span class="sxs-lookup"><span data-stu-id="bb2ce-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
