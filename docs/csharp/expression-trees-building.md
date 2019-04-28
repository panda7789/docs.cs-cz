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
# <a name="building-expression-trees"></a><span data-ttu-id="4bbb4-103">Vytváření stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="4bbb4-103">Building Expression Trees</span></span>

[<span data-ttu-id="4bbb4-104">Předchozí – Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="4bbb4-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="4bbb4-105">Stromy výrazů jste zatím viděli se vytvořila C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="4bbb4-106">Vše museli dělat bylo vytvořit výraz lambda, který byl přiřazen proměnné typu `Expression<Func<T>>` nebo podobný typ.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="4bbb4-107">To není jediný způsob, jak vytvořit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="4bbb4-108">Pro mnoho scénářů možná zjistíte, že budete muset sestavit výraz v paměti za běhu.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="4bbb4-109">Vytváření stromů výrazů je složité fakt, že tyto stromů výrazů jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="4bbb4-110">Je neměnný znamená, že je nutné vytvořit z listy až po kořen stromu.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="4bbb4-111">Rozhraní API, které budete používat k vytváření stromů výrazů, aby odrážela tuto skutečnost: Jako argumenty metod, které použijete k vytvoření uzlu přijímat všechny jeho podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="4bbb4-112">Projděme si několik příkladů, chcete-li zobrazit technik.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="4bbb4-113">Vytvoření uzlů</span><span class="sxs-lookup"><span data-stu-id="4bbb4-113">Creating Nodes</span></span>

<span data-ttu-id="4bbb4-114">Začněme relativně jednoduše znovu.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-114">Let's start relatively simply again.</span></span> <span data-ttu-id="4bbb4-115">Přidání výrazu, které Pracuji s použijeme v těchto částech:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="4bbb4-116">K vytvoření tohoto stromu výrazu, je nutné vytvořit uzly listů.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="4bbb4-117">Listové uzly jsou konstanty, takže můžete používat `Expression.Constant` metodu pro vytvoření uzly:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="4bbb4-118">V dalším kroku sestavíte Přidání výrazu:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="4bbb4-119">Jakmile máte Přidání výrazu, můžete vytvořit lambda výrazu:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="4bbb4-120">To je velmi jednoduchý lambda výraz, protože neobsahuje žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="4bbb4-121">Později v této části, zobrazí se vám mapování argumentů do parametrů a složitější výrazy.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="4bbb4-122">Pro výrazy, které jsou stejně jednoduché jako to předchozí může kombinovat všechna volání do jednoho příkazu:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="4bbb4-123">Vytvoření větve</span><span class="sxs-lookup"><span data-stu-id="4bbb4-123">Building a Tree</span></span>

<span data-ttu-id="4bbb4-124">Který se se základy vytváření stromu výrazů v paměti.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="4bbb4-125">Složitější stromů obecně znamená další typy uzlů a více uzlů ve stromu.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="4bbb4-126">Umožňuje spustit prostřednictvím jednoho další příklad a zobrazit dva další typy uzlů, které se obvykle sestaví při vytváření stromů výrazů: argument uzly a uzly volání metody.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="4bbb4-127">Vytvořme strom výrazu. Chcete-li vytvořit tento výraz:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="4bbb4-128">Začnete vytvořením výrazech pro parametry pro `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="4bbb4-129">Vytváření výrazů násobení a přidání následuje vzor, který jste už viděli:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="4bbb4-130">Dále je třeba vytvořit výraz volání metody pro volání `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="4bbb4-131">A konečně, umístěte volání metody na výraz lambda, ujistěte se, že k definování argumenty výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="4bbb4-132">V tomto příkladu složitější uvidíte několik další techniky, které se často potřebujete k vytvoření stromů výrazu.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="4bbb4-133">Nejprve musíte vytvořit objekty, které představují parametry nebo lokální proměnné, před jejich použitím.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="4bbb4-134">Po vytvoření těchto objektů, můžete ho použít ve vaší strom výrazu, bez ohledu na to budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="4bbb4-135">Za druhé, budete muset použít podmnožinu rozhraní API reflexe k vytvoření `MethodInfo` objektu tak, že vytvoříte strom výrazů pro přístup k této metodě.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="4bbb4-136">Je třeba sami omezit na podmnožinu rozhraní API reflexe, které jsou k dispozici na platformě .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="4bbb4-137">Tyto postupy znovu, rozšíří na další stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="4bbb4-138">Vytváření kódu do hloubky</span><span class="sxs-lookup"><span data-stu-id="4bbb4-138">Building Code In Depth</span></span>

<span data-ttu-id="4bbb4-139">Nejsou omezeni v co lze sestavit pomocí těchto rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="4bbb4-140">Nicméně Čím více složité strom výrazu, který chcete sestavit, tím obtížnější je kód, spravovat a ke čtení.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="4bbb4-141">Vytvořme strom výrazů, který je ekvivalentem tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="4bbb4-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="4bbb4-142">Všimněte si, že výše uvedené, že mám nesestavili strom výrazu, ale jednoduše delegáta.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="4bbb4-143">Použití `Expression` třída, nelze sestavit příkazové lambdy.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="4bbb4-144">Tady je kód, který je nutné k vytvoření stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="4bbb4-145">Je složité fakt, že není rozhraní API pro vytváření `while` smyčky, místo toho budete muset sestavit smyčku, která obsahuje podmíněný test a cíl popisek, který má přerušit ze smyčky.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

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

<span data-ttu-id="4bbb4-146">Kód k vytvoření stromu výrazu pro funkci faktoriálu je poměrně o něco delší složitější, a je riddled s popisky a příkazy break a další prvky, které jsme chtěli vyhnout v naší běžné úlohy kódování.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="4bbb4-147">Pro tento oddíl jsem také jsme aktualizovali kód návštěvníka navštívit každý uzel ve stromu tohoto výrazu a vypsat informace o uzlech, které jsou vytvořeny v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="4bbb4-148">Je možné [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) v úložišti dotnet/docs GitHub.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="4bbb4-149">Vyzkoušejte si to sami sestavováním a spouštěním ukázek.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="4bbb4-150">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="4bbb4-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="4bbb4-151">Zkoumání rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4bbb4-151">Examining the APIs</span></span>

<span data-ttu-id="4bbb4-152">Strom výrazu rozhraní API jsou některé z obtížnější pro navigaci v .NET Core, ale to je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="4bbb4-153">Jejich účelem je spíše složitý proces: psaní kódu, který generuje kód za běhu.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="4bbb4-154">Jsou nutně složité zajistit rovnováhu mezi podpora k dispozici v řídicích struktur C# jazyka a udržování rozumné plochy rozhraní API jako malé.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="4bbb4-155">Této rovnováhy znamená, že mnoho řídících struktur jsou reprezentovány není podle jejich C# vytvoří, ale vytvoří pomocí konstrukce, které představují základní logiku, která generuje kompilátor z těchto vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="4bbb4-156">V tuto chvíli k dispozici je také C# výrazy, které se nedají vytvářet přímo pomocí `Expression` metody třídy.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="4bbb4-157">Obecně platí, bude se jednat o nejnovější operátory a výrazy přidá C# 5 a C# 6.</span><span class="sxs-lookup"><span data-stu-id="4bbb4-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="4bbb4-158">(Například `async` výrazů nemůže být vytvořena a nové `?.` operátor nelze vytvořit přímo.)</span><span class="sxs-lookup"><span data-stu-id="4bbb4-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="4bbb4-159">Další – Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="4bbb4-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
