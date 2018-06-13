---
title: Překladu stromů výrazů
description: Naučte se navštívit každý uzel ve stromu výrazů při sestavování upravené kopie tento strom výrazu.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 9483cbe75b4bf5a38dd791633c852eb0b8473944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217113"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="eae1b-103">Překladu stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="eae1b-103">Translating Expression Trees</span></span>

[<span data-ttu-id="eae1b-104">Předchozí – Vytváření výrazů</span><span class="sxs-lookup"><span data-stu-id="eae1b-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="eae1b-105">V této části konečné naučíte navštívit každý uzel ve stromu výrazů při sestavování upravené kopie tento strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="eae1b-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="eae1b-106">Jedná se o techniky, které budete používat ve dvou scénářích důležité.</span><span class="sxs-lookup"><span data-stu-id="eae1b-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="eae1b-107">Prvním je pochopit algoritmy vyjádřená strom výrazu, aby ji lze přeložit do jiného prostředí.</span><span class="sxs-lookup"><span data-stu-id="eae1b-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="eae1b-108">Druhá je, když chcete změnit algoritmus, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="eae1b-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="eae1b-109">To může být přidat protokolování, zachytí volání metod a sledovat, nebo pro jiné účely.</span><span class="sxs-lookup"><span data-stu-id="eae1b-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="eae1b-110">Překladu je návštěvou</span><span class="sxs-lookup"><span data-stu-id="eae1b-110">Translating is Visiting</span></span>

<span data-ttu-id="eae1b-111">Kód sestavení přeložit strom výrazu je rozšířením co jste viděli již k navštívení všechny uzly ve stromu.</span><span class="sxs-lookup"><span data-stu-id="eae1b-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="eae1b-112">Když je přeložit strom výrazu, navštivte všechny uzly a při návštěvě je, vytvářet novou větev.</span><span class="sxs-lookup"><span data-stu-id="eae1b-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="eae1b-113">Novou větev může obsahovat odkazy na původní uzlů nebo nové uzly, které jste umístili ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="eae1b-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="eae1b-114">Podíváme se to v praxi návštěvou strom výrazu a vytvoření nového stromu s některé uzly nahrazení.</span><span class="sxs-lookup"><span data-stu-id="eae1b-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="eae1b-115">V tomto příkladu budeme nahraďte všechny konstanta konstanta, která je větší desetkrát.</span><span class="sxs-lookup"><span data-stu-id="eae1b-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="eae1b-116">V opačném necháme strom výrazu beze změn.</span><span class="sxs-lookup"><span data-stu-id="eae1b-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="eae1b-117">Namísto čtení hodnoty konstanty a nahraďte ji nové konstanta, uděláme toto nahrazení nahrazením konstantního uzlu nový uzel, který provádí násobení.</span><span class="sxs-lookup"><span data-stu-id="eae1b-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="eae1b-118">Zde, jakmile zjistíte konstantního uzlu, vytvořit nový uzel násobení jehož podřízené objekty jsou původní konstanta a konstantu `10`:</span><span class="sxs-lookup"><span data-stu-id="eae1b-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="eae1b-119">Nahrazením původní uzel dosadit, je vytvořen novou větev obsahující naše úpravy.</span><span class="sxs-lookup"><span data-stu-id="eae1b-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="eae1b-120">Abychom mohli ověřit, která kompilování a provádění stromu nahrazené.</span><span class="sxs-lookup"><span data-stu-id="eae1b-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="eae1b-121">Vytvoření nové větve je kombinací návštěvou uzly ve stromu existující a vytváření nových uzlů a jejich vložení do stromu.</span><span class="sxs-lookup"><span data-stu-id="eae1b-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="eae1b-122">Tento příklad ukazuje význam stromů výrazů se nedá změnit.</span><span class="sxs-lookup"><span data-stu-id="eae1b-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="eae1b-123">Všimněte si, že novou větev vytvořili výše obsahuje směs nově vytvořený uzlů a uzly z na stávající strom.</span><span class="sxs-lookup"><span data-stu-id="eae1b-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="eae1b-124">Který je bezpečné, protože uzly ve stromu existující nemůže být upraven.</span><span class="sxs-lookup"><span data-stu-id="eae1b-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="eae1b-125">To může způsobit velké paměti efektivitu.</span><span class="sxs-lookup"><span data-stu-id="eae1b-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="eae1b-126">Stejným uzlům lze použít v rámci stromu, nebo více stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="eae1b-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="eae1b-127">Vzhledem k tomu, že uzly nemůže být upraven, může být stejném uzlu znovu použít vždy, když jeho potřebné.</span><span class="sxs-lookup"><span data-stu-id="eae1b-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="eae1b-128">Procházení a provádění doplněk</span><span class="sxs-lookup"><span data-stu-id="eae1b-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="eae1b-129">Umožňuje ověřit vytváření druhé návštěvníka, který provede stromu přidání uzlů a vypočítá výsledek.</span><span class="sxs-lookup"><span data-stu-id="eae1b-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="eae1b-130">To provedete tak, že několik změny vistor, který jste se seznámili s dosavadní práce.</span><span class="sxs-lookup"><span data-stu-id="eae1b-130">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="eae1b-131">V této nové verzi návštěvníka vrátí součet částečné operace přidání až tento bod.</span><span class="sxs-lookup"><span data-stu-id="eae1b-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="eae1b-132">Pro konstantní výraz, který je jednoduše hodnota konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="eae1b-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="eae1b-133">Pro přidání výrazu výsledkem je součet operandy levé a pravé po stromů mít byl vyčerpán.</span><span class="sxs-lookup"><span data-stu-id="eae1b-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="eae1b-134">Je celkem kousek sem kód, ale koncepty jsou velmi přístupný.</span><span class="sxs-lookup"><span data-stu-id="eae1b-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="eae1b-135">Tento kód navštíví podřízené objekty do hloubky první hledání.</span><span class="sxs-lookup"><span data-stu-id="eae1b-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="eae1b-136">Pokud se setká s konstantního uzlu, návštěvníka vrací hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="eae1b-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="eae1b-137">Poté, co návštěvníka navštíví i podřízené objekty, tyto děti se počítá součet vypočítanou pro dílčí stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="eae1b-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="eae1b-138">Přidání uzlu můžete nyní výpočetní jeho součet.</span><span class="sxs-lookup"><span data-stu-id="eae1b-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="eae1b-139">Jakmile navštívili všechny uzly ve stromu výraz součet bude vypočítání.</span><span class="sxs-lookup"><span data-stu-id="eae1b-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="eae1b-140">Můžete sledovat spuštění spuštěním ukázky v ladicím programu a trasování provádění.</span><span class="sxs-lookup"><span data-stu-id="eae1b-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="eae1b-141">Pojďme usnadňují trasovat, jak se analyzují uzly a jak jsou součet vypočítána pomocí travsersing stromu.</span><span class="sxs-lookup"><span data-stu-id="eae1b-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="eae1b-142">Zde je aktualizovaná verze agregační metody, která zahrnuje s bit informace trasování:</span><span class="sxs-lookup"><span data-stu-id="eae1b-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="eae1b-143">Spuštění ve stejném výrazu vypočítá následující výstup:</span><span class="sxs-lookup"><span data-stu-id="eae1b-143">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="eae1b-144">Výstup trasování a podle nich zorientujete ve výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="eae1b-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="eae1b-145">Nyní byste měli mít vycházejí jak kód navštíví každý uzel a vypočítá součet jak prochází stromu a vyhledá součet.</span><span class="sxs-lookup"><span data-stu-id="eae1b-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="eae1b-146">Nyní se podívejme na spuštění různých pomocí výrazu poskytují `sum1`:</span><span class="sxs-lookup"><span data-stu-id="eae1b-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="eae1b-147">Toto je výstup z zkoumání výrazu:</span><span class="sxs-lookup"><span data-stu-id="eae1b-147">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="eae1b-148">Při poslední odpověď je stejný, je úplně jiné traversal stromu.</span><span class="sxs-lookup"><span data-stu-id="eae1b-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="eae1b-149">Uzly jsou cesty v jiném pořadí, protože stromu byl zkonstruován pomocí různých operací, které provádí nejdřív.</span><span class="sxs-lookup"><span data-stu-id="eae1b-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="eae1b-150">Více učení</span><span class="sxs-lookup"><span data-stu-id="eae1b-150">Learning More</span></span>

<span data-ttu-id="eae1b-151">Tento příklad ukazuje malou část kódu, který by sestavení k procházení a interpretovat algoritmy reprezentována strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="eae1b-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="eae1b-152">Úplné informace práce potřebné k vytvoření knihovnu obecné účely, který překládá stromů výrazů v jiném jazyce, přečtěte si prosím [této série](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) podle Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="eae1b-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="eae1b-153">Přejde do skvělé podrobnosti o tom, jak převede kód, které je možné nalézt v strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="eae1b-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="eae1b-154">Snad že nyní jste viděli true sílu stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="eae1b-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="eae1b-155">Můžete zkontrolovat sadu kódu, proveďte požadované změny by chtěli tento kód a spouštět změněné verze.</span><span class="sxs-lookup"><span data-stu-id="eae1b-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="eae1b-156">Protože jsou neměnné stromů výrazů, můžete vytvořit nové stromy pomocí součásti existující stromy.</span><span class="sxs-lookup"><span data-stu-id="eae1b-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="eae1b-157">To minimalizuje množství paměti nutné k vytváření stromů výrazů upravené.</span><span class="sxs-lookup"><span data-stu-id="eae1b-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="eae1b-158">Další – Součet</span><span class="sxs-lookup"><span data-stu-id="eae1b-158">Next -- Summing up</span></span>](expression-trees-summary.md)
