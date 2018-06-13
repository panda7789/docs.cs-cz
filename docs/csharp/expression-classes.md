---
title: Framework typy podpůrné stromů výrazů
description: Informace o typech framework podpora stromů výrazů vytváření stromů výrazů a postupy pro práci se strom výrazu rozhraní API.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 3110f2a9534085aba95fcb5c8e76f66229e79f86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214942"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="4a323-103">Framework typy podpůrné stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="4a323-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="4a323-104">Předchozí – Vysvětlení stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="4a323-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="4a323-105">Existuje velký seznam tříd v rozhraní .NET Core, které pracují s stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="4a323-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="4a323-106">Zobrazí úplný seznam [zde](/dotnet/core/api/System.Linq.Expressions).</span><span class="sxs-lookup"><span data-stu-id="4a323-106">You can see the full list [here](/dotnet/core/api/System.Linq.Expressions).</span></span>
<span data-ttu-id="4a323-107">Místo spuštění prostřednictvím úplný seznam, probereme, jak byly navrženy třídy rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="4a323-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="4a323-108">V návrhu jazyka je výraz text kódu, který se vyhodnotí a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4a323-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="4a323-109">Může být velmi jednoduché výrazy: konstantní výraz `1` vrátí na konstantní hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="4a323-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="4a323-110">Mohou být složitější: výraz `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` vrátí jeden kořenový pro Kvadratická rovnice (v případě, kde má rovnice řešení).</span><span class="sxs-lookup"><span data-stu-id="4a323-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="4a323-111">Všechny začíná System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="4a323-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="4a323-112">Jedním z složitosti práce stromů výrazů je, že různé druhy výrazů jsou platné na mnoha místech programy.</span><span class="sxs-lookup"><span data-stu-id="4a323-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="4a323-113">Vezměte v úvahu výraz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4a323-113">Consider an assignment expression.</span></span> <span data-ttu-id="4a323-114">Pravé straně přiřazení může být konstantní hodnota, proměnné, výraz volání metody nebo jiné.</span><span class="sxs-lookup"><span data-stu-id="4a323-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="4a323-115">Tento jazyk flexibilitě mnoho typů jiný výraz kdekoli v uzlu stromu může dojít, když procházejí strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="4a323-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="4a323-116">Proto když můžete pracovat s typem základní výraz, který je nejjednodušší způsob, jak pracovat.</span><span class="sxs-lookup"><span data-stu-id="4a323-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="4a323-117">Ale někdy potřebujete další informace.</span><span class="sxs-lookup"><span data-stu-id="4a323-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="4a323-118">Obsahuje základní třídy výraz `NodeType` vlastnost pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="4a323-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="4a323-119">Vrátí `ExpressionType` tedy výčet typů možné výraz.</span><span class="sxs-lookup"><span data-stu-id="4a323-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="4a323-120">Jakmile znáte typ uzlu, můžete ho převést na tento typ a provedení určitých akcí s jistotou typ uzlu výrazu.</span><span class="sxs-lookup"><span data-stu-id="4a323-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="4a323-121">Můžete vyhledat určité typy uzlů a pak pracovat s konkrétní vlastnosti tohoto typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="4a323-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="4a323-122">Tento kód bude například vytisknout název proměnné pro výraz proměnné přístup.</span><span class="sxs-lookup"><span data-stu-id="4a323-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="4a323-123">Jste postupovali podle postup kontrolou typu uzlu, pak přetypování výrazu proměnné přístup a pak zkontroluje vlastnosti konkrétní výraz typu:</span><span class="sxs-lookup"><span data-stu-id="4a323-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="4a323-124">Vytváření stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="4a323-124">Creating Expression Trees</span></span>

<span data-ttu-id="4a323-125">`System.Linq.Expression` Třída také obsahuje mnoho statické metody pro vytváření výrazů.</span><span class="sxs-lookup"><span data-stu-id="4a323-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="4a323-126">Tyto metody vytvoření do uzlu výraz pomocí zadané argumenty pro své podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="4a323-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="4a323-127">Tímto způsobem můžete vytvořit výraz z jeho uzlů listu.</span><span class="sxs-lookup"><span data-stu-id="4a323-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="4a323-128">Např. Tento kód vytvoří výraz přidat:</span><span class="sxs-lookup"><span data-stu-id="4a323-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="4a323-129">Je vidět na tomto jednoduchém příkladu mnoho typů jsou součástí vytváření a práci s stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="4a323-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="4a323-130">Aby složitost je potřeba zadat možnosti bohaté termínů poskytované jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4a323-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="4a323-131">Navigace rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4a323-131">Navigating the APIs</span></span>
<span data-ttu-id="4a323-132">Existují uzlu typy výrazů, které jsou mapovány na téměř všechny prvky syntaxe jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4a323-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="4a323-133">Každý typ má konkrétní metody pro tento typ elementu jazyk.</span><span class="sxs-lookup"><span data-stu-id="4a323-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="4a323-134">Je mnoho zajišťující ve vaší head najednou.</span><span class="sxs-lookup"><span data-stu-id="4a323-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="4a323-135">Místo pokusí pamatovat vše, zde jsou technik, které používám k práci s stromů výrazů:</span><span class="sxs-lookup"><span data-stu-id="4a323-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="4a323-136">Podívejte se na členy `ExpressionType` výčtu k určení možných uzlů by měl zkoumání.</span><span class="sxs-lookup"><span data-stu-id="4a323-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="4a323-137">To opravdu pomáhá při chcete procházení a porozumění strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="4a323-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="4a323-138">Podívejte se na statické členy `Expression` třída výraz.</span><span class="sxs-lookup"><span data-stu-id="4a323-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="4a323-139">Tyto metody můžete vytvořit libovolný typ výrazu ze sady jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="4a323-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="4a323-140">Podívejte se na `ExpressionVisitor` třída Sestavit strom upravené výrazu.</span><span class="sxs-lookup"><span data-stu-id="4a323-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="4a323-141">Najdete tu informace, jako je podívejte se na každý z těchto tří oblastí.</span><span class="sxs-lookup"><span data-stu-id="4a323-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="4a323-142">Vždy zjistíte, co potřebujete, když začínáte s jedním z těchto tří kroků.</span><span class="sxs-lookup"><span data-stu-id="4a323-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="4a323-143">Další – Provádění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="4a323-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 
