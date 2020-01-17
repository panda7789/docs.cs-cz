---
title: Překládání stromů výrazů
description: Naučte se navštívit jednotlivé uzly ve stromové struktuře výrazů a přitom sestavovat upravenou kopii tohoto stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: f60c447d5c89aa83f85073e642e621608131ed8d
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115772"
---
# <a name="translate-expression-trees"></a><span data-ttu-id="252bd-103">Přeložit stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="252bd-103">Translate expression trees</span></span>

[<span data-ttu-id="252bd-104">Předchozí výrazy sestavení</span><span class="sxs-lookup"><span data-stu-id="252bd-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="252bd-105">V této poslední části se dozvíte, jak při sestavování upravené kopie stromu výrazu navštívit jednotlivé uzly ve stromové struktuře výrazů.</span><span class="sxs-lookup"><span data-stu-id="252bd-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="252bd-106">Jedná se o techniky, které použijete ve dvou důležitých scénářích.</span><span class="sxs-lookup"><span data-stu-id="252bd-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="252bd-107">První je pochopit algoritmy vyjádřené stromem výrazu, aby bylo možné je přeložit do jiného prostředí.</span><span class="sxs-lookup"><span data-stu-id="252bd-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="252bd-108">Druhá je, když chcete změnit algoritmus, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="252bd-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="252bd-109">To může být přidání protokolování, zachytávání volání metod a jejich sledování nebo jiné účely.</span><span class="sxs-lookup"><span data-stu-id="252bd-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="252bd-110">Probíhá překládání.</span><span class="sxs-lookup"><span data-stu-id="252bd-110">Translating is Visiting</span></span>

<span data-ttu-id="252bd-111">Kód, který sestavíte k překladu stromu výrazů, je rozšířením toho, co jste už viděli pro návštěvě všech uzlů ve stromu.</span><span class="sxs-lookup"><span data-stu-id="252bd-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="252bd-112">Při převodu stromu výrazu navštívíte všechny uzly a při jejich návštěvě sestavíte nový strom.</span><span class="sxs-lookup"><span data-stu-id="252bd-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="252bd-113">Nový strom může obsahovat odkazy na původní uzly nebo nové uzly, které jste umístili do stromu.</span><span class="sxs-lookup"><span data-stu-id="252bd-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="252bd-114">Pojďme to vidět v akci návštěvou stromu výrazů a vytvořením nového stromu s některými náhradními uzly.</span><span class="sxs-lookup"><span data-stu-id="252bd-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="252bd-115">V tomto příkladu nahradíme všechny konstanty konstantou, která je desetkrát větší.</span><span class="sxs-lookup"><span data-stu-id="252bd-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="252bd-116">V opačném případě ponecháme strom výrazu beze změny.</span><span class="sxs-lookup"><span data-stu-id="252bd-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="252bd-117">Místo přečtení hodnoty konstanty a její nahrazení novou konstantou provedeme tuto náhradu nahrazením konstantního uzlu novým uzlem, který provede násobení.</span><span class="sxs-lookup"><span data-stu-id="252bd-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="252bd-118">Zde je po nalezení konstantního uzlu vytvořen nový uzel násobení, jehož podřízené položky jsou původní konstantou, a konstanta `10`:</span><span class="sxs-lookup"><span data-stu-id="252bd-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="252bd-119">Nahrazením původního uzlu nahraďte nový strom, který obsahuje naše úpravy.</span><span class="sxs-lookup"><span data-stu-id="252bd-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="252bd-120">Můžeme ověřit, že kompilování a provádění nahrazeného stromu.</span><span class="sxs-lookup"><span data-stu-id="252bd-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="252bd-121">Sestavování nového stromu je kombinace návštěvy uzlů v existujícím stromu a vytvoření nových uzlů a jejich vložení do stromu.</span><span class="sxs-lookup"><span data-stu-id="252bd-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="252bd-122">Tento příklad ukazuje důležitost stromů výrazů, které jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="252bd-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="252bd-123">Všimněte si, že nový strom vytvořený výše obsahuje kombinaci nově vytvořených uzlů a uzlů z existujícího stromu.</span><span class="sxs-lookup"><span data-stu-id="252bd-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="252bd-124">To je bezpečné, protože uzly ve stávajícím stromu nelze upravovat.</span><span class="sxs-lookup"><span data-stu-id="252bd-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="252bd-125">To může mít za následek výrazné zvýšení efektivity paměti.</span><span class="sxs-lookup"><span data-stu-id="252bd-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="252bd-126">Stejné uzly lze použít v celém stromu nebo v několika stromech výrazů.</span><span class="sxs-lookup"><span data-stu-id="252bd-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="252bd-127">Vzhledem k tomu, že uzly nelze upravovat, lze stejný uzel znovu použít vždy, když je potřeba.</span><span class="sxs-lookup"><span data-stu-id="252bd-127">Since nodes can't be modified, the same node can be reused whenever it's needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="252bd-128">Procházení a provádění přidání</span><span class="sxs-lookup"><span data-stu-id="252bd-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="252bd-129">Pojďme to ověřit vytvořením druhého návštěvníka, který projde stromem přidaných uzlů a vypočítá výsledek.</span><span class="sxs-lookup"><span data-stu-id="252bd-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="252bd-130">Můžete to udělat tak, že provedete několik úprav návštěvníka, který jste doposud viděli.</span><span class="sxs-lookup"><span data-stu-id="252bd-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="252bd-131">V této nové verzi návštěvník vrátí částečný součet operace sčítání do tohoto bodu.</span><span class="sxs-lookup"><span data-stu-id="252bd-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="252bd-132">Pro konstantní výraz, který je jednoduše hodnotou konstantního výrazu.</span><span class="sxs-lookup"><span data-stu-id="252bd-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="252bd-133">Pro výraz sčítání je výsledkem součet levého a pravého operandu, jakmile byly tyto stromy přecházet.</span><span class="sxs-lookup"><span data-stu-id="252bd-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="252bd-134">Tady je trochu kód, ale koncepty jsou velmi dostupné.</span><span class="sxs-lookup"><span data-stu-id="252bd-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="252bd-135">Tento kód po prvním hledání navštíví podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="252bd-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="252bd-136">Když narazí na konstantní uzel, návštěvník vrátí hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="252bd-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="252bd-137">Po navštívení návštěvníka budou tyto podřízené položky vypočítány součtem vypočítaným pro daný podstrom.</span><span class="sxs-lookup"><span data-stu-id="252bd-137">After the visitor has visited both children, those children will have computed the sum computed for that subtree.</span></span> <span data-ttu-id="252bd-138">Uzel sčítání teď může vypočítat jeho součet.</span><span class="sxs-lookup"><span data-stu-id="252bd-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="252bd-139">Po navštívení všech uzlů ve stromu výrazů bude součet vypočítán.</span><span class="sxs-lookup"><span data-stu-id="252bd-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="252bd-140">Spuštění můžete trasovat spuštěním ukázky v ladicím programu a trasováním provádění.</span><span class="sxs-lookup"><span data-stu-id="252bd-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="252bd-141">Podívejme se, jak sledovat, jak se uzly analyzují, a jak se součet vypočítává pomocí procházení stromu.</span><span class="sxs-lookup"><span data-stu-id="252bd-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="252bd-142">Zde je aktualizovaná verze agregované metody, která obsahuje poměrně bitovou část trasovacích informací:</span><span class="sxs-lookup"><span data-stu-id="252bd-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="252bd-143">Spuštění na stejném výrazu vrací následující výstup:</span><span class="sxs-lookup"><span data-stu-id="252bd-143">Running it on the same expression yields the following output:</span></span>

```output
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="252bd-144">Sledujte výstup a sledujte v kódu výše.</span><span class="sxs-lookup"><span data-stu-id="252bd-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="252bd-145">Měli byste být schopni pracovat s tím, jak kód navštíví každý uzel, a vypočítat součet při jeho průchodu stromovou strukturou a vyhledá součet.</span><span class="sxs-lookup"><span data-stu-id="252bd-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="252bd-146">Nyní se podívejme na jiný běh s výrazem zadaným `sum1`:</span><span class="sxs-lookup"><span data-stu-id="252bd-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="252bd-147">Zde je výstup prozkoumání tohoto výrazu:</span><span class="sxs-lookup"><span data-stu-id="252bd-147">Here's the output from examining this expression:</span></span>

```output
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="252bd-148">I když je konečná odpověď stejná, je procházení stromové struktury zcela jiné.</span><span class="sxs-lookup"><span data-stu-id="252bd-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="252bd-149">Uzly se cestují v jiném pořadí, protože strom byl vytvořen s různými operacemi, které nastaly jako první.</span><span class="sxs-lookup"><span data-stu-id="252bd-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="252bd-150">Další informace</span><span class="sxs-lookup"><span data-stu-id="252bd-150">Learning More</span></span>

<span data-ttu-id="252bd-151">Tato ukázka ukazuje malou podmnožinu kódu, který byste vytvořili pro procházení a interpretaci algoritmů, které jsou zastoupeny stromem výrazů.</span><span class="sxs-lookup"><span data-stu-id="252bd-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="252bd-152">Kompletní diskuzi o všech potřebách potřebných k sestavení knihovny pro obecné účely, která překládá stromy výrazů do jiného jazyka, si prosím přečtěte v [této řadě](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) podkladem Warren.</span><span class="sxs-lookup"><span data-stu-id="252bd-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="252bd-153">To je velmi podrobné informace o tom, jak přeložit libovolný kód, který můžete najít ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="252bd-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="252bd-154">Doufám, že teď jste viděli skutečnou sílu stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="252bd-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="252bd-155">Můžete zkontrolovat sadu kódu, provést všechny změny, které byste chtěli v kódu, a provést změněnou verzi.</span><span class="sxs-lookup"><span data-stu-id="252bd-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="252bd-156">Vzhledem k tomu, že stromy výrazů jsou neměnné, můžete vytvořit nové stromy pomocí komponent existujících stromů.</span><span class="sxs-lookup"><span data-stu-id="252bd-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="252bd-157">Tím se minimalizuje množství paměti potřebné k vytvoření upravených stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="252bd-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="252bd-158">Další – součet</span><span class="sxs-lookup"><span data-stu-id="252bd-158">Next -- Summing up</span></span>](expression-trees-summary.md)
