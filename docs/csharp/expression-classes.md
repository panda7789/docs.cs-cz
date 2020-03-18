---
title: Typy architektur podporující stromy výrazů
description: Další informace o typech architektury podporujících stromy výrazů, vytváření stromů výrazů a technikách pro práci s rozhraními API stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 8483c46dde3ea97138e55ab84a5924a3d2578730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146083"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="6aa6f-103">Typy architektur podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="6aa6f-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="6aa6f-104">Předchozí -- Vysvětlení stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="6aa6f-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="6aa6f-105">Existuje velký seznam tříd v rozhraní .NET Core framework, které pracují se stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="6aa6f-106">Celý seznam naleznete na <xref:System.Linq.Expressions>adrese .</span><span class="sxs-lookup"><span data-stu-id="6aa6f-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="6aa6f-107">Spíše než spustit úplný seznam, pojďme pochopit, jak byly navrženy framework třídy.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="6aa6f-108">V návrhu jazyka výraz je tělo kódu, který vyhodnocuje a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="6aa6f-109">Výrazy mohou být velmi jednoduché: konstantní výraz `1` vrátí konstantní hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="6aa6f-110">Mohou být složitější: Výraz `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` vrátí jeden kořen pro kvadratickou rovnici (v případě, kdy rovnice má řešení).</span><span class="sxs-lookup"><span data-stu-id="6aa6f-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="6aa6f-111">Vše začíná System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="6aa6f-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="6aa6f-112">Jednou ze složitostí práce se stromy výrazů je, že mnoho různých druhů výrazů je platných na mnoha místech v programech.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="6aa6f-113">Zvažte výraz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-113">Consider an assignment expression.</span></span> <span data-ttu-id="6aa6f-114">Pravá strana přiřazení může být konstantní hodnota, proměnná, výraz volání metody nebo jiné.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="6aa6f-115">Tato flexibilita jazyka znamená, že můžete setkat s mnoha různými typy výrazů kdekoli v uzlech stromu při procházení stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="6aa6f-116">Proto při práci s typem základního výrazu, to je nejjednodušší způsob práce.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="6aa6f-117">Někdy však potřebujete vědět více.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="6aa6f-118">Základní třída Expression `NodeType` obsahuje vlastnost pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="6aa6f-119">Vrátí což `ExpressionType` je výčet možných typů výrazů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="6aa6f-120">Jakmile znáte typ uzlu, můžete jej přetypovat na tento typ a provést určité akce s vědomím typu uzlu výrazu.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="6aa6f-121">Můžete vyhledat určité typy uzlů a potom pracovat s konkrétními vlastnostmi tohoto druhu výrazu.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="6aa6f-122">Tento kód například vytiskne název proměnné pro výraz přístupu proměnné.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="6aa6f-123">Sledoval jsem praxi kontroly typu uzlu, potom přetypování na výraz přístupu proměnné a následné kontrole vlastností konkrétního typu výrazu:</span><span class="sxs-lookup"><span data-stu-id="6aa6f-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="6aa6f-124">Vytváření stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="6aa6f-124">Creating Expression Trees</span></span>

<span data-ttu-id="6aa6f-125">Třída `System.Linq.Expression` také obsahuje mnoho statických metod pro vytvoření výrazů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="6aa6f-126">Tyto metody vytvořit uzel výrazu pomocí argumentů zadaných pro jeho podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="6aa6f-127">Tímto způsobem vytvoříte výraz z jeho listových uzlů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="6aa6f-128">Například tento kód vytvoří výraz Add:</span><span class="sxs-lookup"><span data-stu-id="6aa6f-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="6aa6f-129">Z tohoto jednoduchého příkladu můžete vidět, že mnoho typů se podílí na vytváření a práci se stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="6aa6f-130">Tato složitost je nezbytné poskytnout možnosti bohaté slovní zásoby poskytované jazykem C#.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="6aa6f-131">Navigace v prostředí API</span><span class="sxs-lookup"><span data-stu-id="6aa6f-131">Navigating the APIs</span></span>
<span data-ttu-id="6aa6f-132">Existují typy uzlů výraz, které mapují téměř všechny prvky syntaxe jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="6aa6f-133">Každý typ má specifické metody pro tento typ prvku jazyka.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="6aa6f-134">Je toho hodně, co si najednou necháváš v hlavě.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="6aa6f-135">Spíše než se snažit zapamatovat všechno, zde jsou techniky, které používám pro práci se stromy výrazů:</span><span class="sxs-lookup"><span data-stu-id="6aa6f-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="6aa6f-136">Podívejte se na `ExpressionType` členy výčtu k určení možných uzlů, které byste měli zkoumat.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="6aa6f-137">To opravdu pomáhá, když chcete procházet a pochopit strom výrazů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="6aa6f-138">Podívejte se na statické `Expression` členy třídy k vytvoření výrazu.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="6aa6f-139">Tyto metody můžete vytvořit libovolný typ výrazu ze sady jeho podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="6aa6f-140">Podívejte se `ExpressionVisitor` na třídu k vytvoření stromu upraveného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="6aa6f-141">Najdete více, jak se podíváte na každou z těchto tří oblastí.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="6aa6f-142">Vždy najdete to, co potřebujete, když začnete s jedním z těchto tří kroků.</span><span class="sxs-lookup"><span data-stu-id="6aa6f-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>

 [<span data-ttu-id="6aa6f-143">Další -- Provádění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="6aa6f-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
