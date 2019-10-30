---
title: Typy architektur podporující stromy výrazů
description: Seznamte se s typy architektury, které podporují stromy výrazů, vytváření stromů výrazů a techniky pro práci s rozhraními API stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 157e97594f27345ac96fe91f7dd6f29907c2c7ac
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037622"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="bcfd4-103">Typy architektur podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="bcfd4-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="bcfd4-104">Vysvětlení stromů předchozí--výraz</span><span class="sxs-lookup"><span data-stu-id="bcfd4-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="bcfd4-105">V rozhraní .NET Core Framework je rozsáhlý seznam tříd, které pracují se stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="bcfd4-106">Úplný seznam najdete na stránce <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="bcfd4-107">Místo toho, aby procházely prostřednictvím úplného seznamu, porozuměli tomu, jak byly navrženy třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="bcfd4-108">V návrhu jazyka je výraz tělo kódu, který vyhodnocuje a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="bcfd4-109">Výrazy můžou být velmi jednoduché: konstantní výraz `1` vrací konstantní hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="bcfd4-110">Můžou být složitější: výraz `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` vrátí jeden kořen pro kvadratickou rovnici (v případě, kdy rovnice obsahuje řešení).</span><span class="sxs-lookup"><span data-stu-id="bcfd4-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="bcfd4-111">Vše začíná řetězcem System. Linq. Expression.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="bcfd4-112">Jednou ze složitých prací se stromy výrazů je, že mnoho různých druhů výrazů je platných na mnoha místech v programech.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="bcfd4-113">Vezměte v úvahu výraz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-113">Consider an assignment expression.</span></span> <span data-ttu-id="bcfd4-114">Pravá strana přiřazení může být konstantní hodnota, proměnná, výraz volání metody nebo jiné.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="bcfd4-115">Tato flexibilita jazyka znamená, že se můžete setkat s mnoha různými typy výrazů kdekoli v uzlech stromu při procházení stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="bcfd4-116">Proto když můžete pracovat s typem základního výrazu, je to nejjednodušší způsob, jak pracovat.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="bcfd4-117">Někdy ale potřebujete znát ještě více.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="bcfd4-118">Třída Base Expression obsahuje vlastnost `NodeType` pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="bcfd4-119">Vrátí `ExpressionType`, který je výčtem možných typů výrazů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="bcfd4-120">Jakmile znáte typ uzlu, můžete ho přetypovat na tento typ a provádět konkrétní akce, které budou znát typ uzlu výrazu.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="bcfd4-121">Můžete hledat určité typy uzlů a pak pracovat s konkrétními vlastnostmi tohoto typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="bcfd4-122">Například tento kód vytiskne název proměnné pro výraz přístupu proměnné.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="bcfd4-123">Použil jsem postup kontroly typu uzlu, následné přetypování do výrazu přístupu k proměnné a následné kontrole vlastností konkrétního typu výrazu:</span><span class="sxs-lookup"><span data-stu-id="bcfd4-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="bcfd4-124">Vytváření stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="bcfd4-124">Creating Expression Trees</span></span>

<span data-ttu-id="bcfd4-125">Třída `System.Linq.Expression` také obsahuje mnoho statických metod pro vytváření výrazů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="bcfd4-126">Tyto metody vytvoří uzel výrazu pomocí argumentů dodaných pro své podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="bcfd4-127">Tímto způsobem sestavíte výraz z jeho listových uzlů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="bcfd4-128">Například tento kód vytvoří výraz Add:</span><span class="sxs-lookup"><span data-stu-id="bcfd4-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="bcfd4-129">Můžete si prohlédnout z tohoto jednoduchého příkladu, který je součástí vytváření a práce se stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="bcfd4-130">Tato složitá složitost je nutná k zajištění schopností bohatých slovníků poskytovaných C# jazykem.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="bcfd4-131">Navigace v rozhraních API</span><span class="sxs-lookup"><span data-stu-id="bcfd4-131">Navigating the APIs</span></span>
<span data-ttu-id="bcfd4-132">Existují typy uzlů výrazů, které jsou namapovány na skoro všechny prvky syntaxe C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="bcfd4-133">Každý typ má konkrétní metody pro tento typ elementu jazyka.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="bcfd4-134">Je to hodně, co je potřeba v hlavě uchovávat najednou.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="bcfd4-135">Místo toho, abyste se pokusili nepamatují vše, jsou zde postupy, které mám použít pro práci s stromy výrazů:</span><span class="sxs-lookup"><span data-stu-id="bcfd4-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="bcfd4-136">Podívejte se na členy výčtu `ExpressionType` a určete možné uzly, které byste měli prošetřit.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="bcfd4-137">To skutečně pomáhá při procházení a pochopení stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="bcfd4-138">Pokud chcete vytvořit výraz, podívejte se na statické členy třídy `Expression`.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="bcfd4-139">Tyto metody mohou sestavit libovolný typ výrazu ze sady svých podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="bcfd4-140">Podívejte se na třídu `ExpressionVisitor` a vytvořte upravený strom výrazů.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="bcfd4-141">Další informace najdete v každé z těchto tří oblastí.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="bcfd4-142">Invariably zjistíte, co potřebujete, když začnete s jedním z těchto tří kroků.</span><span class="sxs-lookup"><span data-stu-id="bcfd4-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="bcfd4-143">Další – spouštění stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="bcfd4-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
