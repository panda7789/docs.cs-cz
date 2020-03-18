---
title: Překlad stromů výrazů
description: Zjistěte, jak navštívit každý uzel ve stromu výrazů při vytváření upravené kopie tohoto stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: f60c447d5c89aa83f85073e642e621608131ed8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76115772"
---
# <a name="translate-expression-trees"></a><span data-ttu-id="7dcc5-103">Přeložit stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="7dcc5-103">Translate expression trees</span></span>

[<span data-ttu-id="7dcc5-104">Předchozí -- Výrazy budovy</span><span class="sxs-lookup"><span data-stu-id="7dcc5-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="7dcc5-105">V této poslední části se dozvíte, jak navštívit každý uzel ve stromu výrazů při vytváření upravené kopie tohoto stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="7dcc5-106">Jedná se o techniky, které budete používat ve dvou důležitých scénářích.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="7dcc5-107">Prvním z toho je pochopit algoritmy vyjádřené stromem výrazů tak, aby mohl být přeložen do jiného prostředí.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="7dcc5-108">Druhý je, když chcete změnit algoritmus, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="7dcc5-109">To může být přidat protokolování, volání metody zachycení a sledovat je nebo jiné účely.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="7dcc5-110">Překládání je na návštěvě</span><span class="sxs-lookup"><span data-stu-id="7dcc5-110">Translating is Visiting</span></span>

<span data-ttu-id="7dcc5-111">Kód, který vytvoříte k překladu stromu výrazů, je rozšířením toho, co jste již viděli k návštěvě všech uzlů ve stromu.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="7dcc5-112">Při překladu stromu výrazů navštívíte všechny uzly a při jejich návštěvě vytvoříte nový strom.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="7dcc5-113">Nový strom může obsahovat odkazy na původní uzly nebo nové uzly, které jste umístili do stromu.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="7dcc5-114">Podívejme se na to v akci návštěvou stromu výrazů a vytvořením nového stromu s některými náhradními uzly.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="7dcc5-115">V tomto příkladu nahradíme libovolnou konstantu konstantou, která je desetkrát větší.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="7dcc5-116">Jinak necháme strom výrazu neporušený.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="7dcc5-117">Spíše než čtení hodnoty konstanty a nahrazení nové konstanty, provedeme toto nahrazení nahrazením konstantní uzel s novým uzlovým, který provádí násobení.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="7dcc5-118">Zde, jakmile najdete konstantní uzel, vytvoříte nový uzel násobení, jehož podřízené `10`jsou původní konstanta a konstanta :</span><span class="sxs-lookup"><span data-stu-id="7dcc5-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="7dcc5-119">Nahrazením původního uzlu náhražkou se vytvoří nový strom, který obsahuje naše modifikace.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="7dcc5-120">Můžeme ověřit, že kompilací a provedením nahrazený strom.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="7dcc5-121">Vytvoření nového stromu je kombinací návštěvy uzlů v existujícím stromu a vytvoření nových uzlů a jejich vložení do stromu.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="7dcc5-122">Tento příklad ukazuje důležitost výrazstromy jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="7dcc5-123">Všimněte si, že nový strom vytvořený výše obsahuje směs nově vytvořených uzlů a uzlů z existujícího stromu.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="7dcc5-124">To je bezpečné, protože uzly v existujícím stromu nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="7dcc5-125">To může mít za následek významné účinnosti paměti.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="7dcc5-126">Stejné uzly lze použít v celém stromu nebo ve více stromech výrazů.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="7dcc5-127">Vzhledem k tomu, že uzly nelze změnit, stejný uzel lze znovu použít vždy, když je to potřeba.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-127">Since nodes can't be modified, the same node can be reused whenever it's needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="7dcc5-128">Procházení a provádění sčítání</span><span class="sxs-lookup"><span data-stu-id="7dcc5-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="7dcc5-129">Ověřme to vytvořením druhého návštěvníka, který projde stromem uzlů sčítání a vypočítá výsledek.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="7dcc5-130">Můžete to udělat tím, že pár úprav návštěvníka, které jste viděli tak daleko.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="7dcc5-131">V této nové verzi návštěvník vrátí částečný součet operace sčítání až do tohoto bodu.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="7dcc5-132">Pro konstantní výraz, který je jednoduše hodnota konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="7dcc5-133">Pro výraz sčítání je výsledkem součet levého a pravého operandu, jakmile jsou tyto stromy projety.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="7dcc5-134">Je tu docela dost kódu, ale pojmy jsou velmi přístupný.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="7dcc5-135">Tento kód navštíví děti v hloubce první vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="7dcc5-136">Když narazí na konstantní uzel, návštěvník vrátí hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="7dcc5-137">Poté, co návštěvník navštíví obě děti, tyto děti vypočítají součet vypočítaný pro tento podstrom.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-137">After the visitor has visited both children, those children will have computed the sum computed for that subtree.</span></span> <span data-ttu-id="7dcc5-138">Uzel sčítání nyní můžete vypočítat jeho součet.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="7dcc5-139">Po navštívení všech uzlů ve stromu výrazů bude součet vypočítán.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="7dcc5-140">Spuštění můžete sledovat spuštěním ukázky v ladicím programu a sledováním spuštění.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="7dcc5-141">Usnadněme sledování toho, jak jsou analyzovány uzly a jak se vypočítá součet procházením stromu.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="7dcc5-142">Zde je aktualizovaná verze metody Aggregate, která obsahuje poměrně dost informací o trasování:</span><span class="sxs-lookup"><span data-stu-id="7dcc5-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="7dcc5-143">Spuštění ve stejném výrazu dává následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7dcc5-143">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="7dcc5-144">Sledujte výstup a postupujte podle výše uvedeného kódu.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="7dcc5-145">Měli byste být schopni zjistit, jak kód navštíví každý uzel a vypočítá součet, jak prochází stromem a najde součet.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="7dcc5-146">Nyní se podívejme na jiný běh, s `sum1`výrazem daný :</span><span class="sxs-lookup"><span data-stu-id="7dcc5-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="7dcc5-147">Zde je výstup z zkoumání tohoto výrazu:</span><span class="sxs-lookup"><span data-stu-id="7dcc5-147">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="7dcc5-148">Zatímco konečná odpověď je stejná, strom traversal je zcela odlišný.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="7dcc5-149">Uzly jsou prohledány v jiném pořadí, protože strom byl vytvořen s různými operacemi, které se vyskytly jako první.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="7dcc5-150">Další informace</span><span class="sxs-lookup"><span data-stu-id="7dcc5-150">Learning More</span></span>

<span data-ttu-id="7dcc5-151">Tato ukázka ukazuje malou podmnožinu kódu, který byste vytvořili k procházení a interpretaci algoritmů reprezentovaných stromem výrazů.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="7dcc5-152">Pro úplnou diskusi o všech pracích potřebných k vybudování univerzální knihovny, která překládá výraz stromy do jiného jazyka, přečtěte si [prosím tuto sérii](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="7dcc5-153">To jde do velkých podrobností o tom, jak přeložit některý z kódu, který můžete najít ve stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="7dcc5-154">Doufám, že jste teď viděli skutečnou sílu výrazových stromů.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="7dcc5-155">Můžete zkontrolovat sadu kódu, provést změny, které chcete k tomuto kódu, a spustit změněnou verzi.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="7dcc5-156">Vzhledem k tomu, že stromy výrazů jsou neměnné, můžete vytvořit nové stromy pomocí součástí existujících stromů.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="7dcc5-157">Tím se minimalizuje množství paměti potřebné k vytvoření změněných stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="7dcc5-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="7dcc5-158">Další - Shrnutí</span><span class="sxs-lookup"><span data-stu-id="7dcc5-158">Next -- Summing up</span></span>](expression-trees-summary.md)
