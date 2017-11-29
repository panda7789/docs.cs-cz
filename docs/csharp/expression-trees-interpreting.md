---
title: "Interpretace výrazy"
description: "Zjistěte, jak napsat kód pro zjištění strukturu strom výrazu se nezdařilo."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: e7c5f7404546c6f3812fc5cc3d0320c77816634d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interpreting-expressions"></a><span data-ttu-id="131dd-104">Interpretace výrazy</span><span class="sxs-lookup"><span data-stu-id="131dd-104">Interpreting Expressions</span></span>

[<span data-ttu-id="131dd-105">Předchozí – Provádění výrazy</span><span class="sxs-lookup"><span data-stu-id="131dd-105">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="131dd-106">Teď můžete napsat kód, který zkontrolujte strukturu *strom výrazu*.</span><span class="sxs-lookup"><span data-stu-id="131dd-106">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="131dd-107">Každý uzel ve stromu výrazů bude objekt třídy, který je odvozený od `Expression`.</span><span class="sxs-lookup"><span data-stu-id="131dd-107">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="131dd-108">Tento návrh díky návštěvou všechny uzly v operaci relativně splněny následující rekurzivní strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="131dd-108">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="131dd-109">Obecné strategie je spuštění na kořenový uzel a zjistit, jaký druh uzlu je.</span><span class="sxs-lookup"><span data-stu-id="131dd-109">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="131dd-110">Pokud má typ uzlu podřízené objekty, navštivte rekurzivně podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="131dd-110">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="131dd-111">V každém uzlu podřízené, opakujte tento postup použít v kořenovém uzlu: určit typ a pokud má typ podřízené objekty, navštivte všechny podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="131dd-111">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="131dd-112">Zkoumání výraz s žádné podřízené objekty</span><span class="sxs-lookup"><span data-stu-id="131dd-112">Examining an Expression with No Children</span></span>
<span data-ttu-id="131dd-113">Začněme tím, kteří navštěvují každý uzel ve stromu velmi jednoduchý výraz.</span><span class="sxs-lookup"><span data-stu-id="131dd-113">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="131dd-114">Tady je kód, který vytvoří konstantní výraz a poté zkoumá jeho vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="131dd-114">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="131dd-115">To bude tisknout následující:</span><span class="sxs-lookup"><span data-stu-id="131dd-115">This will print the following:</span></span>

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="131dd-116">Teď můžete napsat kód, který by Zkontrolujte tento výraz a zapsat některé důležité vlastnosti o něm.</span><span class="sxs-lookup"><span data-stu-id="131dd-116">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="131dd-117">Tady je tento kód:</span><span class="sxs-lookup"><span data-stu-id="131dd-117">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="131dd-118">Zkoumání jednoduchý výraz přidání</span><span class="sxs-lookup"><span data-stu-id="131dd-118">Examining a simple Addition Expression</span></span>

<span data-ttu-id="131dd-119">Začněme s ukázkou přidání z Úvod do této části.</span><span class="sxs-lookup"><span data-stu-id="131dd-119">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="131dd-120">Nepoužívám `var` deklarovat tento strom výrazu, protože není možné, protože je implicitně typované na pravé straně přiřazení.</span><span class="sxs-lookup"><span data-stu-id="131dd-120">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="131dd-121">Pro lepší vysvětlení hlubšímu, přečtěte si [zde](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="131dd-121">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="131dd-122">Je kořenový uzel `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="131dd-122">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="131dd-123">Chcete-li získat kód zajímavé na pravé straně z `=>` operátor, budete muset najít podřízených objektů `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="131dd-123">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="131dd-124">Jsme to udělat pomocí všechny výrazy v této části.</span><span class="sxs-lookup"><span data-stu-id="131dd-124">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="131dd-125">Nadřazený uzel Pomozte nám najít návratový typ `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="131dd-125">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="131dd-126">Zkontrolujte každý uzel v tomto výrazu, jsme budete potřebovat k rekurzivnímu najdete na počet uzlů.</span><span class="sxs-lookup"><span data-stu-id="131dd-126">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="131dd-127">Zde je jednoduchý první implementace:</span><span class="sxs-lookup"><span data-stu-id="131dd-127">Here's a simple first implementation:</span></span>

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

<span data-ttu-id="131dd-128">Tato ukázka se vytiskne následující výstup:</span><span class="sxs-lookup"><span data-stu-id="131dd-128">This sample prints the following output:</span></span>

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

<span data-ttu-id="131dd-129">Můžete si všimnout spoustu opakování v ukázce kódu, výše.</span><span class="sxs-lookup"><span data-stu-id="131dd-129">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="131dd-130">Umožňuje vyčistit a vytvořit více obecné výraz uzlu návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="131dd-130">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="131dd-131">Která se bude vyžadovat nám zápis rekurzivní algoritmus.</span><span class="sxs-lookup"><span data-stu-id="131dd-131">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="131dd-132">Libovolný uzel může být typu, který může mít podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="131dd-132">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="131dd-133">Každého uzlu, který má podřízených prvků, vyžaduje nám navštivte tyto děti a zjistit, co je tento uzel.</span><span class="sxs-lookup"><span data-stu-id="131dd-133">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="131dd-134">Tady je si verzi, která využívá rekurze přejděte operace přidání vyčištěnými:</span><span class="sxs-lookup"><span data-stu-id="131dd-134">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

<span data-ttu-id="131dd-135">Tento algoritmus je základem algoritmu, který najdete všechny libovolný `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="131dd-135">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="131dd-136">Je celá řada díry, který kód byl vytvořen pouze konkrétně hledá velmi malé ukázkové sady možné uzly stromu výrazu, které mohou nastat.</span><span class="sxs-lookup"><span data-stu-id="131dd-136">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="131dd-137">Však stále další odlišují od ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="131dd-137">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="131dd-138">(Výchozí velká písmena v `Visitor.CreateFromExpression` metoda vytiskne zprávu ke konzole chyba vyskytne nového typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="131dd-138">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="131dd-139">Tímto způsobem, víte, chcete-li přidat nový typ výrazu.)</span><span class="sxs-lookup"><span data-stu-id="131dd-139">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="131dd-140">Když spustíte tohoto návštěvníka na výše uvedeném Přidání výrazu, získáte tento výstup:</span><span class="sxs-lookup"><span data-stu-id="131dd-140">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="131dd-141">Teď, když jste sestavili obecnější implementace návštěvníka, můžete navštívit a zpracovat více různých typech výrazy.</span><span class="sxs-lookup"><span data-stu-id="131dd-141">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="131dd-142">Zkoumání přidání výraz s mnoha úrovně</span><span class="sxs-lookup"><span data-stu-id="131dd-142">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="131dd-143">Pojďme zkuste složitější příklad, ale stále omezit typy uzlů k přidání pouze:</span><span class="sxs-lookup"><span data-stu-id="131dd-143">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="131dd-144">Před spuštěním to na algoritmu návštěvníka, zkuste myšlenku cvičení pracovat se co může být výstup.</span><span class="sxs-lookup"><span data-stu-id="131dd-144">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="131dd-145">Nezapomeňte, že `+` operátor je *binární operátor*: musí mít dva podřízené objekty představující operandy vlevo a vpravo.</span><span class="sxs-lookup"><span data-stu-id="131dd-145">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="131dd-146">Existuje několik způsobů možné vytvořit stromu, které by mohly být správné:</span><span class="sxs-lookup"><span data-stu-id="131dd-146">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="131dd-147">Můžete zobrazit oddělení do dvě možné odpovědi chcete zvýraznit nejslibnějším.</span><span class="sxs-lookup"><span data-stu-id="131dd-147">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="131dd-148">První představuje *právo asociativní* výrazy.</span><span class="sxs-lookup"><span data-stu-id="131dd-148">The first represents *right associative* expressions.</span></span> <span data-ttu-id="131dd-149">Druhý představují *zbývajících asociativní* výrazy.</span><span class="sxs-lookup"><span data-stu-id="131dd-149">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="131dd-150">Obě tyto dva formáty výhodou je, že formát lze škálovat na libovolný libovolný počet přidání výrazy.</span><span class="sxs-lookup"><span data-stu-id="131dd-150">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="131dd-151">Pokud spustíte tento výraz prostřednictvím návštěvníka, zobrazí se tato tento výstup ověření, že je výraz jednoduchého přidání *zbývajících asociativní*.</span><span class="sxs-lookup"><span data-stu-id="131dd-151">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="131dd-152">Aby bylo možné tuto ukázku spustit a najdete v části stromu úplné výrazu, musel jsem jeden změnu provést na strom výrazu zdroje.</span><span class="sxs-lookup"><span data-stu-id="131dd-152">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="131dd-153">Když strom výrazu obsahuje všechny konstanty, výsledný strom jednoduše obsahuje konstantní hodnota `10`.</span><span class="sxs-lookup"><span data-stu-id="131dd-153">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="131dd-154">Kompilátor provede všechny přidání a snižuje výraz, který má své nejjednodušší podobě.</span><span class="sxs-lookup"><span data-stu-id="131dd-154">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="131dd-155">Zobrazíte stromu původní stačí jednoduše přidáním jednu proměnnou ve výrazu:</span><span class="sxs-lookup"><span data-stu-id="131dd-155">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="131dd-156">Vytvořte pro tento součet návštěvníka a spustit návštěvníka uvidíte tento výstup:</span><span class="sxs-lookup"><span data-stu-id="131dd-156">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

<span data-ttu-id="131dd-157">Můžete také spustit žádné z ostatních vzorků prostřednictvím kódu návštěvníka a najdete v části stromu, co představuje.</span><span class="sxs-lookup"><span data-stu-id="131dd-157">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="131dd-158">Tady je příklad `sum3` výraz výše (s dalším parametrem zabránit computing konstanta kompilátor):</span><span class="sxs-lookup"><span data-stu-id="131dd-158">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="131dd-159">Toto je výstup z návštěvníka:</span><span class="sxs-lookup"><span data-stu-id="131dd-159">Here's the output from the visitor:</span></span>

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="131dd-160">Všimněte si, že závorkách nejsou součástí výstupu.</span><span class="sxs-lookup"><span data-stu-id="131dd-160">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="131dd-161">Nejsou žádné uzly strom výrazu, které představují závorkách v vstupní výraz.</span><span class="sxs-lookup"><span data-stu-id="131dd-161">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="131dd-162">Struktura stromu výraz obsahuje všechny informace potřebné pro komunikaci prioritu.</span><span class="sxs-lookup"><span data-stu-id="131dd-162">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="131dd-163">Rozšíření od této ukázky</span><span class="sxs-lookup"><span data-stu-id="131dd-163">Extending from this sample</span></span>

<span data-ttu-id="131dd-164">Ukázka se zabývá jenom nejvíce elementární stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="131dd-164">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="131dd-165">Kód, který jste viděli v této části zpracovává pouze konstantní celá čísla a binárního souboru `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="131dd-165">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="131dd-166">Jako poslední vzorek můžeme aktualizovat návštěvníka pro zpracování složitějších výraz.</span><span class="sxs-lookup"><span data-stu-id="131dd-166">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="131dd-167">Pojďme aby fungoval pro toto:</span><span class="sxs-lookup"><span data-stu-id="131dd-167">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="131dd-168">Tento kód představuje jeden možné implementace matematickém *faktoriál* funkce.</span><span class="sxs-lookup"><span data-stu-id="131dd-168">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="131dd-169">Způsob, jak tento kód jsme nenapsali označuje dvě limitiations vytváření stromů výrazů přiřazením výrazy lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="131dd-169">The way I've written this code highlights two limitiations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="131dd-170">Nejprve lambda nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="131dd-170">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="131dd-171">To znamená, nelze použít smyčky, bloky, pokud / else – příkazy a další ovládací struktury běžné v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="131dd-171">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="131dd-172">Jsem omezeno na použití výrazy.</span><span class="sxs-lookup"><span data-stu-id="131dd-172">I'm limited to using expressions.</span></span> <span data-ttu-id="131dd-173">Druhý nelze rekurzivní volání stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="131dd-173">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="131dd-174">Může I pokud již byly delegáta, ale nelze volat v jeho výrazu stromu formuláře.</span><span class="sxs-lookup"><span data-stu-id="131dd-174">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="131dd-175">V tomto článku v [vytváření stromů výrazů](expression-trees-building.md) dozvíte techniky k překonat tato omezení.</span><span class="sxs-lookup"><span data-stu-id="131dd-175">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>


<span data-ttu-id="131dd-176">V tomto výrazu narazíte uzly těchto typů:</span><span class="sxs-lookup"><span data-stu-id="131dd-176">In this expression, you'll encounter nodes of all these types:</span></span>
1. <span data-ttu-id="131dd-177">Rovná (binárního výrazu)</span><span class="sxs-lookup"><span data-stu-id="131dd-177">Equal (binary expression)</span></span>
2. <span data-ttu-id="131dd-178">Násobení (binárního výrazu)</span><span class="sxs-lookup"><span data-stu-id="131dd-178">Multiply (binary expression)</span></span>
3. <span data-ttu-id="131dd-179">Podmíněné (na?</span><span class="sxs-lookup"><span data-stu-id="131dd-179">Conditional (the ?</span></span> <span data-ttu-id="131dd-180">: výraz)</span><span class="sxs-lookup"><span data-stu-id="131dd-180">: expression)</span></span>
4. <span data-ttu-id="131dd-181">Metoda volání výrazu (volání `Range()` a `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="131dd-181">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="131dd-182">Jeden způsob, jak upravit algoritmus návštěvníka je zachovat, její provedení a zapisovat typ uzlu pokaždé, když se dostanete vaší `default` klauzule.</span><span class="sxs-lookup"><span data-stu-id="131dd-182">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="131dd-183">Po několika iterací budete viděli jste, každý z potenciální uzlů.</span><span class="sxs-lookup"><span data-stu-id="131dd-183">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="131dd-184">Potom budete mít vše, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="131dd-184">Then, you have all you need.</span></span> <span data-ttu-id="131dd-185">Výsledkem bude přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="131dd-185">The result would be something like this:</span></span>

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

<span data-ttu-id="131dd-186">ConditionalVisitor a MethodCallVisitor procesu tyto dva uzly:</span><span class="sxs-lookup"><span data-stu-id="131dd-186">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

<span data-ttu-id="131dd-187">A by výstup pro strom výrazu:</span><span class="sxs-lookup"><span data-stu-id="131dd-187">And the output for the expression tree would be:</span></span>

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a><span data-ttu-id="131dd-188">Rozšíření knihovny ukázka</span><span class="sxs-lookup"><span data-stu-id="131dd-188">Extending the Sample Library</span></span>

<span data-ttu-id="131dd-189">Ukázky v této části ukazují základní techniky navštivte a zkontrolujte uzly ve stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="131dd-189">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="131dd-190">I glossed přes mnoho akce, které může být nutné, aby bylo možné soustředit se jenom na klíčové úlohy návštěvou a přístup k uzlům v strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="131dd-190">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="131dd-191">Nejprve návštěvníkům zpracovat pouze konstanty, které jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="131dd-191">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="131dd-192">Konstantní hodnoty může být jiné číselného typu a jazyka C# podporuje převody a reklamními nabídkami mezi tyto typy.</span><span class="sxs-lookup"><span data-stu-id="131dd-192">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="131dd-193">Robustnější verzi tento kód by zrcadlení všechny tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="131dd-193">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="131dd-194">V posledním příkladu rozpozná podmnožinu typy uzlu.</span><span class="sxs-lookup"><span data-stu-id="131dd-194">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="131dd-195">Vám může stále informačního kanálu je mnoho výrazů, které způsobí, že k selhání.</span><span class="sxs-lookup"><span data-stu-id="131dd-195">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="131dd-196">Úplnou implementaci je zahrnuta v rozhraní .NET standardní pod názvem [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) a dokáže zpracovat všechny typy uzlu.</span><span class="sxs-lookup"><span data-stu-id="131dd-196">A full implementation is included in the .NET Standard under the name [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) and can handle all the possible node types.</span></span>

<span data-ttu-id="131dd-197">Knihovna, kterou lze použít v tomto článku se nakonec bylo vytvořeno pro demonstrační a učit se.</span><span class="sxs-lookup"><span data-stu-id="131dd-197">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="131dd-198">Není optimalizována ho.</span><span class="sxs-lookup"><span data-stu-id="131dd-198">It's not optimized.</span></span> <span data-ttu-id="131dd-199">I napsali, abyste se struktury používá velmi jasně a abyste měli na očích technik navštívit uzly a analýza, co je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="131dd-199">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="131dd-200">Provozní implementace by více zaměřit na výkon než je nutné.</span><span class="sxs-lookup"><span data-stu-id="131dd-200">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="131dd-201">I když tyto omezení musí být i na moct zápis algoritmy, které pro čtení a pochopení stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="131dd-201">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="131dd-202">Další--Vytváření výrazy</span><span class="sxs-lookup"><span data-stu-id="131dd-202">Next -- Building Expressions</span></span>](expression-trees-building.md)
