---
title: "Překladu stromů výrazů"
description: "Naučte se navštívit každý uzel ve stromu výrazů při sestavování upravené kopie tento strom výrazu."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 602a17591d27ebfd098516453b9028bca37ad5e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="translating-expression-trees"></a><span data-ttu-id="3087d-104">Překladu stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="3087d-104">Translating Expression Trees</span></span>

[<span data-ttu-id="3087d-105">Předchozí – Vytváření výrazů</span><span class="sxs-lookup"><span data-stu-id="3087d-105">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="3087d-106">V této části konečné naučíte navštívit každý uzel ve stromu výrazů při sestavování upravené kopie tento strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3087d-106">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="3087d-107">Jedná se o techniky, které budete používat ve dvou scénářích důležité.</span><span class="sxs-lookup"><span data-stu-id="3087d-107">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="3087d-108">Prvním je pochopit algoritmy vyjádřená strom výrazu, aby ji lze přeložit do jiného prostředí.</span><span class="sxs-lookup"><span data-stu-id="3087d-108">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="3087d-109">Druhá je, když chcete změnit algoritmus, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="3087d-109">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="3087d-110">To může být přidat protokolování, zachytí volání metod a sledovat, nebo pro jiné účely.</span><span class="sxs-lookup"><span data-stu-id="3087d-110">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="3087d-111">Překladu je návštěvou</span><span class="sxs-lookup"><span data-stu-id="3087d-111">Translating is Visiting</span></span>

<span data-ttu-id="3087d-112">Kód sestavení přeložit strom výrazu je rozšířením co jste viděli již k navštívení všechny uzly ve stromu.</span><span class="sxs-lookup"><span data-stu-id="3087d-112">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="3087d-113">Když je přeložit strom výrazu, navštivte všechny uzly a při návštěvě je, vytvářet novou větev.</span><span class="sxs-lookup"><span data-stu-id="3087d-113">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="3087d-114">Novou větev může obsahovat odkazy na původní uzlů nebo nové uzly, které jste umístili ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="3087d-114">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="3087d-115">Podíváme se to v praxi návštěvou strom výrazu a vytvoření nového stromu s některé uzly nahrazení.</span><span class="sxs-lookup"><span data-stu-id="3087d-115">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="3087d-116">V tomto příkladu budeme nahraďte všechny konstanta konstanta, která je větší desetkrát.</span><span class="sxs-lookup"><span data-stu-id="3087d-116">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="3087d-117">V opačném necháme strom výrazu beze změn.</span><span class="sxs-lookup"><span data-stu-id="3087d-117">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="3087d-118">Namísto čtení hodnoty konstanty a nahraďte ji nové konstanta, uděláme toto nahrazení nahrazením konstantního uzlu nový uzel, který provádí násobení.</span><span class="sxs-lookup"><span data-stu-id="3087d-118">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="3087d-119">Zde, jakmile zjistíte konstantního uzlu, vytvořit nový uzel násobení jehož podřízené objekty jsou původní konstanta a konstantu `10`:</span><span class="sxs-lookup"><span data-stu-id="3087d-119">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="3087d-120">Nahrazením původní uzel dosadit, je vytvořen novou větev obsahující naše úpravy.</span><span class="sxs-lookup"><span data-stu-id="3087d-120">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="3087d-121">Abychom mohli ověřit, která kompilování a provádění stromu nahrazené.</span><span class="sxs-lookup"><span data-stu-id="3087d-121">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="3087d-122">Vytvoření nové větve je kombinací návštěvou uzly ve stromu existující a vytváření nových uzlů a jejich vložení do stromu.</span><span class="sxs-lookup"><span data-stu-id="3087d-122">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="3087d-123">Tento příklad ukazuje význam stromů výrazů se nedá změnit.</span><span class="sxs-lookup"><span data-stu-id="3087d-123">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="3087d-124">Všimněte si, že novou větev vytvořili výše obsahuje směs nově vytvořený uzlů a uzly z na stávající strom.</span><span class="sxs-lookup"><span data-stu-id="3087d-124">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="3087d-125">Který je bezpečné, protože uzly ve stromu existující nemůže být upraven.</span><span class="sxs-lookup"><span data-stu-id="3087d-125">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="3087d-126">To může způsobit velké paměti efektivitu.</span><span class="sxs-lookup"><span data-stu-id="3087d-126">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="3087d-127">Stejným uzlům lze použít v rámci stromu, nebo více stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="3087d-127">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="3087d-128">Vzhledem k tomu, že uzly nemůže být upraven, může být stejném uzlu znovu použít vždy, když jeho potřebné.</span><span class="sxs-lookup"><span data-stu-id="3087d-128">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="3087d-129">Procházení a provádění doplněk</span><span class="sxs-lookup"><span data-stu-id="3087d-129">Traversing and Executing an Addition</span></span>

<span data-ttu-id="3087d-130">Umožňuje ověřit vytváření druhé návštěvníka, který provede stromu přidání uzlů a vypočítá výsledek.</span><span class="sxs-lookup"><span data-stu-id="3087d-130">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="3087d-131">To provedete tak, že několik změny vistor, který jste se seznámili s dosavadní práce.</span><span class="sxs-lookup"><span data-stu-id="3087d-131">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="3087d-132">V této nové verzi návštěvníka vrátí součet částečné operace přidání až tento bod.</span><span class="sxs-lookup"><span data-stu-id="3087d-132">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="3087d-133">Pro konstantní výraz, který je jednoduše hodnota konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="3087d-133">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="3087d-134">Pro přidání výrazu výsledkem je součet operandy levé a pravé po stromů mít byl vyčerpán.</span><span class="sxs-lookup"><span data-stu-id="3087d-134">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="3087d-135">Je celkem kousek sem kód, ale koncepty jsou velmi přístupný.</span><span class="sxs-lookup"><span data-stu-id="3087d-135">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="3087d-136">Tento kód navštíví podřízené objekty do hloubky první hledání.</span><span class="sxs-lookup"><span data-stu-id="3087d-136">This code visits children in a depth first search.</span></span> <span data-ttu-id="3087d-137">Pokud se setká s konstantního uzlu, návštěvníka vrací hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="3087d-137">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="3087d-138">Poté, co návštěvníka navštíví i podřízené objekty, tyto děti se počítá součet vypočítanou pro dílčí stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="3087d-138">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="3087d-139">Přidání uzlu můžete nyní výpočetní jeho součet.</span><span class="sxs-lookup"><span data-stu-id="3087d-139">The addition node can now compute its sum.</span></span>
<span data-ttu-id="3087d-140">Jakmile navštívili všechny uzly ve stromu výraz součet bude vypočítání.</span><span class="sxs-lookup"><span data-stu-id="3087d-140">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="3087d-141">Můžete sledovat spuštění spuštěním ukázky v ladicím programu a trasování provádění.</span><span class="sxs-lookup"><span data-stu-id="3087d-141">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="3087d-142">Pojďme usnadňují trasovat, jak se analyzují uzly a jak jsou součet vypočítána pomocí travsersing stromu.</span><span class="sxs-lookup"><span data-stu-id="3087d-142">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="3087d-143">Zde je aktualizovaná verze agregační metody, která zahrnuje s bit informace trasování:</span><span class="sxs-lookup"><span data-stu-id="3087d-143">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="3087d-144">Spuštění ve stejném výrazu vypočítá následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3087d-144">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="3087d-145">Výstup trasování a podle nich zorientujete ve výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="3087d-145">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="3087d-146">Nyní byste měli mít vycházejí jak kód navštíví každý uzel a vypočítá součet jak prochází stromu a vyhledá součet.</span><span class="sxs-lookup"><span data-stu-id="3087d-146">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="3087d-147">Nyní se podívejme na spuštění různých pomocí výrazu poskytují `sum1`:</span><span class="sxs-lookup"><span data-stu-id="3087d-147">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="3087d-148">Toto je výstup z zkoumání výrazu:</span><span class="sxs-lookup"><span data-stu-id="3087d-148">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="3087d-149">Při poslední odpověď je stejný, je úplně jiné traversal stromu.</span><span class="sxs-lookup"><span data-stu-id="3087d-149">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="3087d-150">Uzly jsou cesty v jiném pořadí, protože stromu byl zkonstruován pomocí různých operací, které provádí nejdřív.</span><span class="sxs-lookup"><span data-stu-id="3087d-150">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="3087d-151">Více učení</span><span class="sxs-lookup"><span data-stu-id="3087d-151">Learning More</span></span>

<span data-ttu-id="3087d-152">Tento příklad ukazuje malou část kódu, který by sestavení k procházení a interpretovat algoritmy reprezentována strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3087d-152">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="3087d-153">Úplné informace práce potřebné k vytvoření knihovnu obecné účely, který překládá stromů výrazů v jiném jazyce, přečtěte si prosím [této série](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) podle Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="3087d-153">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="3087d-154">Přejde do skvělé podrobnosti o tom, jak převede kód, které je možné nalézt v strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3087d-154">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="3087d-155">Snad že nyní jste viděli true sílu stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3087d-155">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="3087d-156">Můžete zkontrolovat sadu kódu, proveďte požadované změny by chtěli tento kód a spouštět změněné verze.</span><span class="sxs-lookup"><span data-stu-id="3087d-156">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="3087d-157">Protože jsou neměnné stromů výrazů, můžete vytvořit nové stromy pomocí součásti existující stromy.</span><span class="sxs-lookup"><span data-stu-id="3087d-157">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="3087d-158">To minimalizuje množství paměti nutné k vytváření stromů výrazů upravené.</span><span class="sxs-lookup"><span data-stu-id="3087d-158">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="3087d-159">Další – Součet</span><span class="sxs-lookup"><span data-stu-id="3087d-159">Next -- Summing up</span></span>](expression-trees-summary.md)
