---
title: Překlad stromů výrazů
description: Zjistěte, jak chcete navštívit každý uzel ve stromu výrazů při sestavování upravenou kopii tohoto stromu výrazu.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 6fe35983119bba443ed9132ff0c52361e1f07da8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200532"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="58da3-103">Překlad stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="58da3-103">Translating Expression Trees</span></span>

[<span data-ttu-id="58da3-104">Předchozí – Vytváření výrazů</span><span class="sxs-lookup"><span data-stu-id="58da3-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="58da3-105">V této závěrečné sekci dozvíte, jak chcete navštívit každý uzel ve stromu výrazů při sestavování upravenou kopii tohoto stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="58da3-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="58da3-106">Jedná se o techniky, které budete používat v dva důležité scénáře.</span><span class="sxs-lookup"><span data-stu-id="58da3-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="58da3-107">Prvním je pochopit algoritmy vyjádřená strom výrazu tak, aby jej lze přeložit do jiného prostředí.</span><span class="sxs-lookup"><span data-stu-id="58da3-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="58da3-108">Druhým je, když chcete změnit algoritmus, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="58da3-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="58da3-109">To může být přidání protokolování, zachytí volání metod a sledovat jejich, nebo pro jiné účely.</span><span class="sxs-lookup"><span data-stu-id="58da3-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="58da3-110">Překlad je návštěva</span><span class="sxs-lookup"><span data-stu-id="58da3-110">Translating is Visiting</span></span>

<span data-ttu-id="58da3-111">Kód sestavení pro převod strom výrazu je rozšířením co jste viděli již k navštívení všechny uzly ve stromu.</span><span class="sxs-lookup"><span data-stu-id="58da3-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="58da3-112">Když jste přeložit strom výrazu, najdete všechny uzly a při jejich návštěvě, vytváření nového stromu.</span><span class="sxs-lookup"><span data-stu-id="58da3-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="58da3-113">Nové stromové struktury mohou obsahovat odkazy na původní uzly nebo nové uzly, které jste umístili ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="58da3-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="58da3-114">Podívejme se to v praxi navštívit strom výrazů a vytvořením nové větve s některé uzly nahrazení.</span><span class="sxs-lookup"><span data-stu-id="58da3-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="58da3-115">V tomto příkladu podíváme nahradit libovolná konstanta s konstantou, která je větší, desetkrát.</span><span class="sxs-lookup"><span data-stu-id="58da3-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="58da3-116">V opačném případě Ponecháme stromu výrazů beze změn.</span><span class="sxs-lookup"><span data-stu-id="58da3-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="58da3-117">Namísto hodnotou konstanty pro čtení a jeho nahrazení atributem nové konstantou, uděláme toto nahrazení nahrazením konstantního uzlu nový uzel, který provede násobení.</span><span class="sxs-lookup"><span data-stu-id="58da3-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="58da3-118">Jakmile najdete konstantního uzlu, můžete zde vytvářet nový uzel násobení, jehož potomci se původní konstantní a konstanty `10`:</span><span class="sxs-lookup"><span data-stu-id="58da3-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="58da3-119">Nahrazením původní uzel dosadit, je vytvořen nový stromu, který obsahuje úpravy.</span><span class="sxs-lookup"><span data-stu-id="58da3-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="58da3-120">Abychom mohli ověřit, který kompilaci a spouštění stromu nahrazené.</span><span class="sxs-lookup"><span data-stu-id="58da3-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="58da3-121">Vytvoření nové větve je kombinací navštívit uzlů ve stromu existující a vytváření nových uzlů a jejich vložení do stromu.</span><span class="sxs-lookup"><span data-stu-id="58da3-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="58da3-122">Tento příklad ukazuje důležitost stromů výrazů jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="58da3-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="58da3-123">Všimněte si, že nové větve vytvořené výše obsahuje kombinaci nově vytvořené uzly a uzly ze stávající strom.</span><span class="sxs-lookup"><span data-stu-id="58da3-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="58da3-124">Který je bezpečné, protože uzly ve stromu existující nelze upravovat.</span><span class="sxs-lookup"><span data-stu-id="58da3-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="58da3-125">To může způsobit velké paměti efektivitu.</span><span class="sxs-lookup"><span data-stu-id="58da3-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="58da3-126">Stejné uzly je možné v rámci stromu, nebo více stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="58da3-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="58da3-127">Protože uzly nelze upravovat, může být stejném uzlu znovu použít vždy, když své potřeby.</span><span class="sxs-lookup"><span data-stu-id="58da3-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="58da3-128">Procházení a provádění doplněk</span><span class="sxs-lookup"><span data-stu-id="58da3-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="58da3-129">Můžeme to ověřit tak vytváření druhé návštěvníka, který vás provede přidáním uzlů stromu a vypočítá výsledek.</span><span class="sxs-lookup"><span data-stu-id="58da3-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="58da3-130">Můžete to provést tak, že několik úprav návštěvník, který jste zatím viděli.</span><span class="sxs-lookup"><span data-stu-id="58da3-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="58da3-131">V této nové verzi návštěvníka vrátí částečného součtu operace přidání do této chvíle.</span><span class="sxs-lookup"><span data-stu-id="58da3-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="58da3-132">Pro konstantní výraz, který je jednoduše hodnotu konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="58da3-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="58da3-133">Pro přidání výrazu výsledkem je součet operandů levé a pravé, jakmile byla z těchto stromů provázány.</span><span class="sxs-lookup"><span data-stu-id="58da3-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="58da3-134">Je hodně Zde uveďte kód, ale popsané koncepty se velmi přístupné.</span><span class="sxs-lookup"><span data-stu-id="58da3-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="58da3-135">Tento kód navštíví podřízené objekty první hledání hloubku.</span><span class="sxs-lookup"><span data-stu-id="58da3-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="58da3-136">Pokud se setká konstantního uzlu, návštěvníka hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="58da3-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="58da3-137">Poté, co návštěvníka navštíví i podřízené položky, tyto podřízené objekty se vypočítat součet vypočítat pro dílčí stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="58da3-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="58da3-138">Přidání uzlu můžete nyní výpočetní jeho součet.</span><span class="sxs-lookup"><span data-stu-id="58da3-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="58da3-139">Jakmile navštívili všech uzlů ve stromu výrazu součet bude vypočítání.</span><span class="sxs-lookup"><span data-stu-id="58da3-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="58da3-140">Sledování spuštění spuštěním ukázky v ladicím programu a trasování provádění.</span><span class="sxs-lookup"><span data-stu-id="58da3-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="58da3-141">Pojďme usnadňují sledování, jak se analyzují uzly a jak se počítají součet tak, že travsersing stromu.</span><span class="sxs-lookup"><span data-stu-id="58da3-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="58da3-142">Tady je aktualizovanou verzi agregační metoda, která obsahuje hodně trasovací informace:</span><span class="sxs-lookup"><span data-stu-id="58da3-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="58da3-143">Spuštění ve stejném výrazu poskytuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="58da3-143">Running it on the same expression yields the following output:</span></span>

```
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

<span data-ttu-id="58da3-144">Trasování výstupu a můžete pokračovat ve výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="58da3-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="58da3-145">Je třeba možnost pracovat na více systémů jak kód navštíví každý uzel a kód vypočítá součet prochází stromu a zjistí součet.</span><span class="sxs-lookup"><span data-stu-id="58da3-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="58da3-146">Teď se podívejme se na různé spuštěný proces, pomocí výrazu Dal `sum1`:</span><span class="sxs-lookup"><span data-stu-id="58da3-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="58da3-147">Zde se nachází výstup z zkoumání tento výraz:</span><span class="sxs-lookup"><span data-stu-id="58da3-147">Here's the output from examining this expression:</span></span>

```
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

<span data-ttu-id="58da3-148">I když je poslední odpovědí je stejný, přechod zálohovaných stromové struktury se úplně.</span><span class="sxs-lookup"><span data-stu-id="58da3-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="58da3-149">Uzly se přesunul v jiném pořadí, protože stromu byl zkonstruován pomocí různých operací, ke kterým dochází poprvé.</span><span class="sxs-lookup"><span data-stu-id="58da3-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="58da3-150">Další informace</span><span class="sxs-lookup"><span data-stu-id="58da3-150">Learning More</span></span>

<span data-ttu-id="58da3-151">Tento příklad ukazuje malou část kódu, který by sestavení k procházení a interpretovat algoritmy reprezentována strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="58da3-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="58da3-152">Úplné informace veškeré práce potřebné k vytvoření knihovny obecné účely, který překládá stromů výrazů do jiného jazyka, přečtěte si prosím [tuto řadu](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) podle Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="58da3-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="58da3-153">To obsahuje skvělé podrobnosti o tom, jak přeložit některý kód, který může pro vás ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="58da3-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="58da3-154">Doufám, že už teď víte, výkon služby stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="58da3-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="58da3-155">Můžete prozkoumat sadu kódu, proveďte požadované změny by rádi, že kód a provést změny verze.</span><span class="sxs-lookup"><span data-stu-id="58da3-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="58da3-156">Protože jsou neměnné stromů výrazů, můžete vytvořit nové stromové struktury pomocí komponenty větvích.</span><span class="sxs-lookup"><span data-stu-id="58da3-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="58da3-157">Tím se minimalizují množství paměti, které jsou potřebné k vytvoření stromů výrazu upravené.</span><span class="sxs-lookup"><span data-stu-id="58da3-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="58da3-158">Další--Sečetl</span><span class="sxs-lookup"><span data-stu-id="58da3-158">Next -- Summing up</span></span>](expression-trees-summary.md)
