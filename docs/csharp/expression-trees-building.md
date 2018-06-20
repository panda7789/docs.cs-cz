---
title: Vytváření stromů výrazů
description: Další informace o technikách pro vytváření stromů výrazů.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7751af17aafa8e2d1a14125da43352108b1c1f95
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207186"
---
# <a name="building-expression-trees"></a><span data-ttu-id="92ff5-103">Vytváření stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="92ff5-103">Building Expression Trees</span></span>

[<span data-ttu-id="92ff5-104">Předchozí – Interpretace výrazy</span><span class="sxs-lookup"><span data-stu-id="92ff5-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="92ff5-105">Všechny stromů výrazů, které jste se seznámili s, pokud byla vytvořena kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="92ff5-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="92ff5-106">Všechny jste museli provést byl vytvoření výrazu lambda, kterému byla přiřazena k proměnné typu `Expression<Func<T>>` nebo podobné typ.</span><span class="sxs-lookup"><span data-stu-id="92ff5-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="92ff5-107">Která není jedinou možností, jak vytvořit strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="92ff5-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="92ff5-108">Pro mnoho scénářů s můžete zjistit, které potřebujete k vytvoření výrazu v paměti za běhu.</span><span class="sxs-lookup"><span data-stu-id="92ff5-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="92ff5-109">Vytváření stromů výrazů ztěžuje skutečnost, že jsou tyto stromů výrazů neměnné.</span><span class="sxs-lookup"><span data-stu-id="92ff5-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="92ff5-110">Probíhá neměnné znamená, že musíte sestavit z nechá až kořenu stromu.</span><span class="sxs-lookup"><span data-stu-id="92ff5-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="92ff5-111">Rozhraní API, které použijete k sestavení stromů výrazů odrážela tuto skutečnost: metody, které použijete k vytvoření uzlu trvat všechny její podřízené položky jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="92ff5-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="92ff5-112">Projděme několik příkladů tak, aby zobrazovalo technik.</span><span class="sxs-lookup"><span data-stu-id="92ff5-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="92ff5-113">Vytvoření uzlů</span><span class="sxs-lookup"><span data-stu-id="92ff5-113">Creating Nodes</span></span>

<span data-ttu-id="92ff5-114">Začněme relativně jednoduše znovu.</span><span class="sxs-lookup"><span data-stu-id="92ff5-114">Let's start relatively simply again.</span></span> <span data-ttu-id="92ff5-115">Použijeme přidání výraz, který I jste pracovali v těchto částech:</span><span class="sxs-lookup"><span data-stu-id="92ff5-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="92ff5-116">Chcete-li vytvořit tento strom výrazu, je nutné vytvořit uzlů listu.</span><span class="sxs-lookup"><span data-stu-id="92ff5-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="92ff5-117">Uzlů listu jsou konstanty, abyste mohli používat `Expression.Constant` metodu pro vytvoření uzly:</span><span class="sxs-lookup"><span data-stu-id="92ff5-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="92ff5-118">Dále budete sestavení výrazu přidání:</span><span class="sxs-lookup"><span data-stu-id="92ff5-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="92ff5-119">Jakmile máte Přidání výrazu, můžete vytvořit výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="92ff5-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="92ff5-120">Toto je výrazu lambda velmi jednoduchý, protože neobsahuje žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="92ff5-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="92ff5-121">Později v této části se zobrazí postup namapovat argumenty parametrů a složitější výrazy se vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="92ff5-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="92ff5-122">Pro výrazy, které jsou stejně jednoduché jako to předchozí můžou kombinovat všechna volání do jednoho příkazu:</span><span class="sxs-lookup"><span data-stu-id="92ff5-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="92ff5-123">Vytváření stromu</span><span class="sxs-lookup"><span data-stu-id="92ff5-123">Building a Tree</span></span>

<span data-ttu-id="92ff5-124">To je základní informace o vytváření strom výrazu v paměti.</span><span class="sxs-lookup"><span data-stu-id="92ff5-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="92ff5-125">Složitější stromy obvykle znamená další typy uzlů a další uzly ve stromu.</span><span class="sxs-lookup"><span data-stu-id="92ff5-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="92ff5-126">Umožňuje spustit prostřednictvím jednoho další příklad a zobrazit dva další typy uzlů, které obvykle vytvoříte při vytváření stromů výrazů: argument uzlů a uzly volání metody.</span><span class="sxs-lookup"><span data-stu-id="92ff5-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="92ff5-127">Vytvořme strom výrazu se nezdařilo vytvořit tento výraz:</span><span class="sxs-lookup"><span data-stu-id="92ff5-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="92ff5-128">Budete začněte vytvořením výrazech parametrů pro `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="92ff5-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="92ff5-129">Vzor, který jste už viděli vytváření výrazy násobení a přidání takto:</span><span class="sxs-lookup"><span data-stu-id="92ff5-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="92ff5-130">Dále musíte vytvořit výraz volání metody pro volání `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="92ff5-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="92ff5-131">A nakonec uvést volání metody do výrazu lambda, nezapomeňte zadat argumenty výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="92ff5-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="92ff5-132">V tomto příkladu složitější zobrazí několik další techniky, které často bude potřeba vytvořit stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="92ff5-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="92ff5-133">Nejprve musíte vytvořit objekty, které představují parametry nebo lokální proměnné dříve, než je použijete.</span><span class="sxs-lookup"><span data-stu-id="92ff5-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="92ff5-134">Po vytvoření těchto objektů, můžete je používat v vaší strom výrazu, vždy, když potřebujete.</span><span class="sxs-lookup"><span data-stu-id="92ff5-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="92ff5-135">Druhý, budete muset použít podmnožinu rozhraní API reflexe k vytvoření `MethodInfo` objektu tak, že můžete vytvořit strom výrazu pro přístup k dané metody.</span><span class="sxs-lookup"><span data-stu-id="92ff5-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="92ff5-136">Je nutné sami omezit na podmnožinu rozhraní API reflexe, které jsou k dispozici na platformě .NET Core.</span><span class="sxs-lookup"><span data-stu-id="92ff5-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="92ff5-137">Tyto postupy se znovu rozšířit jiných stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="92ff5-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="92ff5-138">Vytváření kódu v hloubka</span><span class="sxs-lookup"><span data-stu-id="92ff5-138">Building Code In Depth</span></span>

<span data-ttu-id="92ff5-139">Nejsou omezené v si můžete vytvořit pomocí těchto rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="92ff5-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="92ff5-140">Čím více však komplikovanější strom výrazu, který chcete vytvořit, tím složitější kód je spravovat a číst.</span><span class="sxs-lookup"><span data-stu-id="92ff5-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="92ff5-141">Vytvořme strom výrazu, který je ekvivalentem tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="92ff5-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="92ff5-142">Všimněte si výše, I není sestavení strom výrazu, ale jednoduše delegát.</span><span class="sxs-lookup"><span data-stu-id="92ff5-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="92ff5-143">Pomocí `Expression` třídy, nemůže vytvořit lambda.</span><span class="sxs-lookup"><span data-stu-id="92ff5-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="92ff5-144">Zde je kód, který je potřeba vytvořit stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="92ff5-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="92ff5-145">Ztěžuje fakt, že není k dispozici rozhraní API pro sestavení `while` smyčky, místo toho potřebujete k vytváření smyčku, který obsahuje testu podmíněného a cíl popisek pro přerušení mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="92ff5-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

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

<span data-ttu-id="92ff5-146">Kód k vytvoření strom výrazu pro funkci faktoriálu je poměrně trochu delší složitěji, a je riddled s popisky a zalomení příkazy a další prvky, kterou jsme chtěli vyhnout v našem každý den kódování úlohy.</span><span class="sxs-lookup"><span data-stu-id="92ff5-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="92ff5-147">Pro tento oddíl I taky aktualizovali kód návštěvníka navštívit každý uzel v tomto výrazu stromu a zapsat informace o uzly, které jsou vytvořené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="92ff5-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="92ff5-148">Můžete [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) v úložišti GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="92ff5-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="92ff5-149">Vytváření a spuštěním ukázky experimentovat sami.</span><span class="sxs-lookup"><span data-stu-id="92ff5-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="92ff5-150">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="92ff5-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="92ff5-151">Zkoumání rozhraní API</span><span class="sxs-lookup"><span data-stu-id="92ff5-151">Examining the APIs</span></span>

<span data-ttu-id="92ff5-152">Strom výrazu rozhraní API jsou některé obtížnější přejděte v .NET Core, ale není to.</span><span class="sxs-lookup"><span data-stu-id="92ff5-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="92ff5-153">Jejich účelem je spíš složitý proces: psaní kódu, který generuje kód za běhu.</span><span class="sxs-lookup"><span data-stu-id="92ff5-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="92ff5-154">Jsou to nutně složitá zajistit rovnováhu mezi podpora všechny řídicí struktury dostupné v jazyce C# a udržování co přiměřené možnosti útoku na rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="92ff5-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="92ff5-155">Toto vyrovnávání znamená, že mnoho řídicí struktury jsou reprezentované není podle jejich konstrukce jazyka C#, nikoli podle konceptů, které představují základní logiku, která kompilátor generuje na základě těchto konstrukce vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="92ff5-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="92ff5-156">V tuto chvíli k dispozici je také výrazy jazyka C#, které nelze sestavit přímo pomocí `Expression` metody třídy.</span><span class="sxs-lookup"><span data-stu-id="92ff5-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="92ff5-157">Obecně platí tyto bude nejnovější operátory a výrazy přidali v C# 5 a 6 C#.</span><span class="sxs-lookup"><span data-stu-id="92ff5-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="92ff5-158">(Například `async` výrazy nelze vytvořili a nové `?.` operátor nelze vytvořit přímo.)</span><span class="sxs-lookup"><span data-stu-id="92ff5-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="92ff5-159">Další – Překladu výrazy</span><span class="sxs-lookup"><span data-stu-id="92ff5-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
