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
# <a name="building-expression-trees"></a><span data-ttu-id="86ec0-103">Vytváření stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="86ec0-103">Building Expression Trees</span></span>

[<span data-ttu-id="86ec0-104">Předchozí -- Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="86ec0-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="86ec0-105">Všechny stromy výrazů, které jste dosud viděli, byly vytvořeny kompilátorem Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="86ec0-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="86ec0-106">Jediné, co jste museli udělat, bylo vytvořit výraz lambda, `Expression<Func<T>>` který byl přiřazen proměnné zadané jako nebo nějaký podobný typ.</span><span class="sxs-lookup"><span data-stu-id="86ec0-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="86ec0-107">To není jediný způsob, jak vytvořit strom výrazů.</span><span class="sxs-lookup"><span data-stu-id="86ec0-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="86ec0-108">Pro mnoho scénářů můžete zjistit, že je třeba vytvořit výraz v paměti za běhu.</span><span class="sxs-lookup"><span data-stu-id="86ec0-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="86ec0-109">Vytváření stromů výrazů je komplikováno skutečností, že tyto stromy výrazů jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="86ec0-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="86ec0-110">Být neměnný znamená, že musíte postavit strom od listů až ke kořeni.</span><span class="sxs-lookup"><span data-stu-id="86ec0-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="86ec0-111">Api, která budete používat k vytváření stromů výrazů, odrážejí tuto skutečnost: Metody, které použijete k sestavení uzlu, berou všechny jeho podřízené položky jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="86ec0-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="86ec0-112">Pojďme si projít několik příkladů, které vám ukáží techniky.</span><span class="sxs-lookup"><span data-stu-id="86ec0-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="86ec0-113">Vytváření uzlů</span><span class="sxs-lookup"><span data-stu-id="86ec0-113">Creating Nodes</span></span>

<span data-ttu-id="86ec0-114">Začněme poměrně jednoduše znovu.</span><span class="sxs-lookup"><span data-stu-id="86ec0-114">Let's start relatively simply again.</span></span> <span data-ttu-id="86ec0-115">Budeme používat výraz sčítání jsem pracoval s v těchto částech:</span><span class="sxs-lookup"><span data-stu-id="86ec0-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="86ec0-116">Chcete-li vytvořit tento strom výrazu, musíte vytvořit uzly listu.</span><span class="sxs-lookup"><span data-stu-id="86ec0-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="86ec0-117">Uzly listů jsou konstanty, takže `Expression.Constant` můžete použít metodu k vytvoření uzlů:</span><span class="sxs-lookup"><span data-stu-id="86ec0-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="86ec0-118">Dále vytvoříte výraz sčítání:</span><span class="sxs-lookup"><span data-stu-id="86ec0-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="86ec0-119">Jakmile máte výraz sčítání, můžete vytvořit výraz lambda:</span><span class="sxs-lookup"><span data-stu-id="86ec0-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="86ec0-120">Toto je velmi jednoduchý lambda výraz, protože neobsahuje žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="86ec0-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="86ec0-121">Dále v této části uvidíte, jak mapovat argumenty na parametry a vytvářet složitější výrazy.</span><span class="sxs-lookup"><span data-stu-id="86ec0-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="86ec0-122">Pro výrazy, které jsou stejně jednoduché jako tento, můžete kombinovat všechna volání do jednoho příkazu:</span><span class="sxs-lookup"><span data-stu-id="86ec0-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="86ec0-123">Budování stromu</span><span class="sxs-lookup"><span data-stu-id="86ec0-123">Building a Tree</span></span>

<span data-ttu-id="86ec0-124">To jsou základy vytváření stromu výrazů v paměti.</span><span class="sxs-lookup"><span data-stu-id="86ec0-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="86ec0-125">Složitější stromy obecně znamenají více typů uzlů a více uzlů ve stromu.</span><span class="sxs-lookup"><span data-stu-id="86ec0-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="86ec0-126">Pojďme projít ještě jeden příklad a ukázat další dva typy uzlů, které budete obvykle stavět při vytváření stromů výrazů: uzly argumentů a uzly volání metody.</span><span class="sxs-lookup"><span data-stu-id="86ec0-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="86ec0-127">Vytvořme strom výrazů pro vytvoření tohoto výrazu:</span><span class="sxs-lookup"><span data-stu-id="86ec0-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="86ec0-128">Začnete vytvořením výrazů parametrů `x` `y`pro a:</span><span class="sxs-lookup"><span data-stu-id="86ec0-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="86ec0-129">Vytvoření výrazů násobení a sčítání se řídí vzorem, který jste již viděli:</span><span class="sxs-lookup"><span data-stu-id="86ec0-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="86ec0-130">Dále je třeba vytvořit výraz volání metody `Math.Sqrt`pro volání .</span><span class="sxs-lookup"><span data-stu-id="86ec0-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="86ec0-131">A nakonec vložíte volání metody do výrazu lambda a ujistěte se, že definujete argumenty výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="86ec0-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="86ec0-132">V tomto složitějším příkladu se zobrazí několik dalších technik, které budete často potřebovat k vytvoření stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="86ec0-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="86ec0-133">Nejprve je třeba vytvořit objekty, které představují parametry nebo místní proměnné před jejich použitím.</span><span class="sxs-lookup"><span data-stu-id="86ec0-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="86ec0-134">Jakmile tyto objekty vytvoříte, můžete je použít ve stromu výrazů, kdekoli potřebujete.</span><span class="sxs-lookup"><span data-stu-id="86ec0-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="86ec0-135">Za druhé je třeba použít podmnožinu reflexe `MethodInfo` API k vytvoření objektu tak, že můžete vytvořit strom výrazpro přístup k této metodě.</span><span class="sxs-lookup"><span data-stu-id="86ec0-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="86ec0-136">Musíte se omezit na podmnožinu rozhraní API reflexe, které jsou k dispozici na platformě .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86ec0-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="86ec0-137">Opět platí, že tyto techniky se rozšíří na jiné stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="86ec0-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="86ec0-138">Stavební kód do hloubky</span><span class="sxs-lookup"><span data-stu-id="86ec0-138">Building Code In Depth</span></span>

<span data-ttu-id="86ec0-139">Nejste omezeni v tom, co můžete vytvořit pomocí těchto api.</span><span class="sxs-lookup"><span data-stu-id="86ec0-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="86ec0-140">Složitější strom výrazů, který chcete vytvořit, je však obtížnější kód spravovat a číst.</span><span class="sxs-lookup"><span data-stu-id="86ec0-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="86ec0-141">Pojďme vytvořit strom výrazů, který je ekvivalentem tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="86ec0-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="86ec0-142">Všimněte si výše, že jsem nevytvořil strom výrazů, ale jednoduše delegát.</span><span class="sxs-lookup"><span data-stu-id="86ec0-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="86ec0-143">Pomocí `Expression` třídy nelze vytvořit příkaz lambdas.</span><span class="sxs-lookup"><span data-stu-id="86ec0-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="86ec0-144">Zde je kód, který je nutný k vytvoření stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="86ec0-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="86ec0-145">Je to složité tím, že neexistuje rozhraní API `while` pro vytvoření smyčky, místo toho je třeba vytvořit smyčku, která obsahuje podmíněný test a cíl popisku, který se z smyčky vymyká.</span><span class="sxs-lookup"><span data-stu-id="86ec0-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

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

<span data-ttu-id="86ec0-146">Kód pro vytvoření stromu výrazů pro faktoriální funkci je o něco delší, komplikovanější a je prošpikovaný popisky a příkazy break a dalšími prvky, kterým bychom se chtěli vyhnout v našich každodenních úkolech kódování.</span><span class="sxs-lookup"><span data-stu-id="86ec0-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="86ec0-147">V této části jsem také aktualizoval kód návštěvníka, aby navštívil každý uzel v tomto stromu výrazů a napsal informace o uzlech, které jsou vytvořeny v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="86ec0-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="86ec0-148">[Ukázkový kód](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) můžete zobrazit nebo stáhnout v úložišti GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="86ec0-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="86ec0-149">Experimentujte sami sestavením a spuštěním vzorků.</span><span class="sxs-lookup"><span data-stu-id="86ec0-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="86ec0-150">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="86ec0-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="86ec0-151">Zkoumání api</span><span class="sxs-lookup"><span data-stu-id="86ec0-151">Examining the APIs</span></span>

<span data-ttu-id="86ec0-152">Rozhraní API stromu výrazů jsou některé z obtížnější navigaci v .NET Core, ale to je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="86ec0-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="86ec0-153">Jejich účelem je poměrně složitý podnik: psaní kódu, který generuje kód za běhu.</span><span class="sxs-lookup"><span data-stu-id="86ec0-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="86ec0-154">Jsou nutně složité poskytnout rovnováhu mezi podporou všech řídicích struktur, které jsou k dispozici v jazyce C# a udržování plochy rozhraní API tak malé, jak je rozumné.</span><span class="sxs-lookup"><span data-stu-id="86ec0-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="86ec0-155">Toto vyvážení znamená, že mnoho řídicích struktur jsou reprezentovány ne jejich C# konstrukce, ale konstrukce, které představují základní logiku, kterou kompilátor generuje z těchto vyšší úrovně konstrukce.</span><span class="sxs-lookup"><span data-stu-id="86ec0-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="86ec0-156">Také v tomto okamžiku existují výrazy Jazyka C#, `Expression` které nelze sestavit přímo pomocí metod třídy.</span><span class="sxs-lookup"><span data-stu-id="86ec0-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="86ec0-157">Obecně se jedná o nejnovější operátory a výrazy přidané v C# 5 a C# 6.</span><span class="sxs-lookup"><span data-stu-id="86ec0-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="86ec0-158">(Například `async` výrazy nelze sestavit a `?.` nový operátor nelze přímo vytvořit.)</span><span class="sxs-lookup"><span data-stu-id="86ec0-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="86ec0-159">Další -- Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="86ec0-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
