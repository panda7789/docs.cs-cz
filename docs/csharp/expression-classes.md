---
title: Typy architektur podporující stromy výrazů
description: Další informace o rozhraní framework typy podporující stromy výrazů, vytváření stromů výrazů a techniky pro práci s strom výrazu rozhraní API.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 687b521c52c1ca380a12e18469b5f66000049d3c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934789"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="d601c-103">Typy architektur podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="d601c-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="d601c-104">Předchozí – Vysvětlení stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="d601c-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="d601c-105">Existuje dlouhý seznam tříd v rozhraní .NET Core, které pracují s stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="d601c-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="d601c-106">Podívejte se na seznam v <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="d601c-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="d601c-107">Nespouštějte ho pomocí úplného seznamu, nyní se pokusíme pochopit, jak byly navrženy tříd rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="d601c-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="d601c-108">V návrhu jazyka je výraz tělo kód, který se vyhodnotí a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d601c-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="d601c-109">Výrazy mohou být velmi jednoduchý: konstantní výraz `1` vrací konstantní hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="d601c-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="d601c-110">Mohou být složitější: výraz `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` vrátí jeden kořenový adresář pro kvadratické rovnice (v případě, kdy má rovnice řešení).</span><span class="sxs-lookup"><span data-stu-id="d601c-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="d601c-111">Všechno začíná System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="d601c-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="d601c-112">Jedním ze složitých úkolů při práci s stromů výrazů je, že jsou různé druhy výrazů platný na mnoha místech v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="d601c-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="d601c-113">Vezměte v úvahu výraz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d601c-113">Consider an assignment expression.</span></span> <span data-ttu-id="d601c-114">Pravá strana přiřazení může být konstantní hodnotu, proměnné, výraz volání metody nebo jiné.</span><span class="sxs-lookup"><span data-stu-id="d601c-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="d601c-115">Flexibilita z jazyka znamená, že mnoho typů jiný výraz kdekoli v uzly stromu mohou nastat, když procházejí strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="d601c-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="d601c-116">Proto můžete pracovat s typem základní výraz, který při nejjednodušší způsob, jak pracovat.</span><span class="sxs-lookup"><span data-stu-id="d601c-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="d601c-117">Ale někdy potřebujete další informace.</span><span class="sxs-lookup"><span data-stu-id="d601c-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="d601c-118">Obsahuje základní třídy výraz `NodeType` vlastnost pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="d601c-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="d601c-119">Vrátí `ExpressionType` což je výčet typy výrazů je to možné.</span><span class="sxs-lookup"><span data-stu-id="d601c-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="d601c-120">Jakmile budete znát typ uzlu, můžete přetypovat na daný typ a provádět konkrétní akce znalost typ uzlu výrazu.</span><span class="sxs-lookup"><span data-stu-id="d601c-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="d601c-121">Můžete vyhledat určité typy uzlů a poté pracovat s určitými vlastnostmi tohoto typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="d601c-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="d601c-122">Tento kód například vytiskne název proměnné pro přístup k proměnným výraz.</span><span class="sxs-lookup"><span data-stu-id="d601c-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="d601c-123">Jste postupovali podle postupů kontrola typu uzlu, pak přetypování výrazu přístup k proměnným a následnou kontrolou vlastnosti typu určité výraz:</span><span class="sxs-lookup"><span data-stu-id="d601c-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="d601c-124">Vytváření stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="d601c-124">Creating Expression Trees</span></span>

<span data-ttu-id="d601c-125">`System.Linq.Expression` Třída také obsahuje mnoho statické metody pro vytváření výrazů.</span><span class="sxs-lookup"><span data-stu-id="d601c-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="d601c-126">Tyto metody vytvoří uzlu výraz pomocí zadané pro podřízené argumenty.</span><span class="sxs-lookup"><span data-stu-id="d601c-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="d601c-127">Tímto způsobem můžete vytvořit výraz z jeho uzly typu list.</span><span class="sxs-lookup"><span data-stu-id="d601c-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="d601c-128">Například tento kód vytvoří přidat výraz:</span><span class="sxs-lookup"><span data-stu-id="d601c-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="d601c-129">Zobrazí se v tomto jednoduchém příkladu mnoho typů jsou součástí vytváření a práci s stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="d601c-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="d601c-130">Složitost je potřeba zadat možnosti bohaté slovníku k dispozici v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="d601c-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="d601c-131">Procházení rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d601c-131">Navigating the APIs</span></span>
<span data-ttu-id="d601c-132">Existují výraz typy uzlů, které mapují na téměř všechny prvky syntaxe jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="d601c-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="d601c-133">Každý typ má specifické metody pro daný typ prvku jazyka.</span><span class="sxs-lookup"><span data-stu-id="d601c-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="d601c-134">Je mnoho dalších zachovat v hlavě najednou.</span><span class="sxs-lookup"><span data-stu-id="d601c-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="d601c-135">Namísto pokusu o všechno, co učit nazpaměť, tady jsou techniky využité pro práci s stromů výrazů:</span><span class="sxs-lookup"><span data-stu-id="d601c-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="d601c-136">Podívejte se na členy `ExpressionType` výčtu k určení možných uzly by měl zkoumání.</span><span class="sxs-lookup"><span data-stu-id="d601c-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="d601c-137">To opravdu pomáhá při procházení a porozumění strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="d601c-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="d601c-138">Podívejte se na statické členy třídy `Expression` třída výraz.</span><span class="sxs-lookup"><span data-stu-id="d601c-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="d601c-139">Tyto metody můžete vytvořit jakýkoli typ výrazu ze sady jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="d601c-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="d601c-140">Podívejte se na `ExpressionVisitor` třídy k sestavení stromu upravené výrazem.</span><span class="sxs-lookup"><span data-stu-id="d601c-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="d601c-141">Najdete tu informace, jako je podívejte se na každý z těchto tří oblastí.</span><span class="sxs-lookup"><span data-stu-id="d601c-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="d601c-142">Vždy zjistíte, co potřebujete, když začínáte s jeden z těchto tří kroků.</span><span class="sxs-lookup"><span data-stu-id="d601c-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="d601c-143">Další – Provádění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="d601c-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 
