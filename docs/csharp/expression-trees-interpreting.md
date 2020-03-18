---
title: Interpretace výrazů
description: Naučte se psát kód prozkoumat strukturu stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 1283d7d957c72558652b96cb428efd0f071f0184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146005"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="0468b-103">Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="0468b-103">Interpreting Expressions</span></span>

[<span data-ttu-id="0468b-104">Předchozí -- Provádění výrazů</span><span class="sxs-lookup"><span data-stu-id="0468b-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="0468b-105">Nyní napíšeme nějaký kód, který prozkoumá strukturu *stromu výrazů*.</span><span class="sxs-lookup"><span data-stu-id="0468b-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="0468b-106">Každý uzel ve stromu výrazů bude objektem třídy, která je odvozena z `Expression`.</span><span class="sxs-lookup"><span data-stu-id="0468b-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="0468b-107">Tento návrh umožňuje návštěvě všech uzlů ve stromu výrazu relativně přímočaré rekurzivní operace.</span><span class="sxs-lookup"><span data-stu-id="0468b-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="0468b-108">Obecnou strategií je začít v kořenovém uzlu a určit, jaký druh uzlu je.</span><span class="sxs-lookup"><span data-stu-id="0468b-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="0468b-109">Pokud typ uzlu má podřízené, rekurzivně navštivte děti.</span><span class="sxs-lookup"><span data-stu-id="0468b-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="0468b-110">V každém podřízeném uzlu opakujte proces použitý v kořenovém uzlu: určete typ a pokud má typ podřízené děti, navštivte každou z podřízených.</span><span class="sxs-lookup"><span data-stu-id="0468b-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="0468b-111">Zkoumání výrazu bez podřízených výrazů</span><span class="sxs-lookup"><span data-stu-id="0468b-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="0468b-112">Začněme návštěvou každého uzlu ve velmi jednoduchém stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="0468b-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="0468b-113">Zde je kód, který vytvoří konstantní výraz a pak zkoumá jeho vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0468b-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="0468b-114">Vytiskne se následující:</span><span class="sxs-lookup"><span data-stu-id="0468b-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="0468b-115">Nyní napíšeme kód, který by prozkoumat tento výraz a napsat některé důležité vlastnosti o něm.</span><span class="sxs-lookup"><span data-stu-id="0468b-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="0468b-116">Tady je ten kód:</span><span class="sxs-lookup"><span data-stu-id="0468b-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="0468b-117">Zkoumání jednoduchého výrazu sčítání</span><span class="sxs-lookup"><span data-stu-id="0468b-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="0468b-118">Začněme s ukázkou přidání z úvodu do této části.</span><span class="sxs-lookup"><span data-stu-id="0468b-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="0468b-119">Nepoužívám `var` k deklarování tohoto stromu výrazů, protože to není možné, protože pravá strana přiřazení je implicitně zadána.</span><span class="sxs-lookup"><span data-stu-id="0468b-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="0468b-120">Chcete-li pochopit, že hlouběji, přečtěte si [zde](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0468b-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="0468b-121">Kořenový uzel je `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="0468b-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="0468b-122">Chcete-li získat zajímavý kód na pravé `=>` straně operátora, musíte najít jednu `LambdaExpression`z poddajných .</span><span class="sxs-lookup"><span data-stu-id="0468b-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="0468b-123">Uděláme to se všemi výrazy v této sekci.</span><span class="sxs-lookup"><span data-stu-id="0468b-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="0468b-124">Nadřazený uzel nám pomáhá najít `LambdaExpression`návratový typ .</span><span class="sxs-lookup"><span data-stu-id="0468b-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="0468b-125">Chcete-li prozkoumat každý uzel v tomto výrazu, budeme muset rekurzivně navštívit několik uzlů.</span><span class="sxs-lookup"><span data-stu-id="0468b-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="0468b-126">Zde je jednoduchá první implementace:</span><span class="sxs-lookup"><span data-stu-id="0468b-126">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="0468b-127">Tato ukázka vytiskne následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0468b-127">This sample prints the following output:</span></span>

```output
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

<span data-ttu-id="0468b-128">V ukázkové části kódu si všimnete mnoha opakování.</span><span class="sxs-lookup"><span data-stu-id="0468b-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="0468b-129">Pojďme vyčistit, že se a vybudovat obecnější účel výraz uzlu návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="0468b-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="0468b-130">To bude vyžadovat, abychom napsali rekurzivní algoritmus.</span><span class="sxs-lookup"><span data-stu-id="0468b-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="0468b-131">Libovolný uzel může být typu, který může mít podřízené.</span><span class="sxs-lookup"><span data-stu-id="0468b-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="0468b-132">Každý uzel, který má děti vyžaduje, abychom navštívili tyto děti a určit, co tento uzel je.</span><span class="sxs-lookup"><span data-stu-id="0468b-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="0468b-133">Zde je vyčištěna verze, která využívá rekurze k návštěvě sčítání operace:</span><span class="sxs-lookup"><span data-stu-id="0468b-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="0468b-134">Tento algoritmus je základem algoritmu, který `LambdaExpression`může navštívit libovolné .</span><span class="sxs-lookup"><span data-stu-id="0468b-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="0468b-135">Existuje mnoho děr, a to, že kód, který jsem vytvořil, hledá pouze velmi malý vzorek možných sad uzlů stromu výrazů, se kterými se může setkat.</span><span class="sxs-lookup"><span data-stu-id="0468b-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="0468b-136">Nicméně, stále se můžete naučit docela dost z toho, co produkuje.</span><span class="sxs-lookup"><span data-stu-id="0468b-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="0468b-137">(Výchozí případ v `Visitor.CreateFromExpression` metodě vytiskne zprávu do konzoly chyb, když je zjištěn nový typ uzlu.</span><span class="sxs-lookup"><span data-stu-id="0468b-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="0468b-138">Tímto způsobem víte, přidat nový typ výrazu.)</span><span class="sxs-lookup"><span data-stu-id="0468b-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="0468b-139">Když spustíte tohoto návštěvníka na přidání výraz uvýšený, získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0468b-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```output
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

<span data-ttu-id="0468b-140">Nyní, když jste vytvořili obecnější implementaci návštěvníků, můžete navštívit a zpracovat mnoho dalších různých typů výrazů.</span><span class="sxs-lookup"><span data-stu-id="0468b-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="0468b-141">Zkoumání výrazu sčítání s mnoha úrovněmi</span><span class="sxs-lookup"><span data-stu-id="0468b-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="0468b-142">Zkusme složitější příklad, ale přesto omezit typy uzlů pouze sčítání:</span><span class="sxs-lookup"><span data-stu-id="0468b-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="0468b-143">Než to spustíte na algoritmu návštěvníka, zkuste myšlenkové cvičení, abyste zjistili, jaký by mohl být výstup.</span><span class="sxs-lookup"><span data-stu-id="0468b-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="0468b-144">Nezapomeňte, `+` že operátor je *binární operátor*: musí mít dvě podřízené objekty představující levé a pravé operandy.</span><span class="sxs-lookup"><span data-stu-id="0468b-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="0468b-145">Existuje několik možných způsobů, jak vytvořit strom, který by mohl být správný:</span><span class="sxs-lookup"><span data-stu-id="0468b-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="0468b-146">Můžete vidět oddělení do dvou možných odpovědí upozornit na nejslibnější.</span><span class="sxs-lookup"><span data-stu-id="0468b-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="0468b-147">První představuje *právo asociativní* výrazy.</span><span class="sxs-lookup"><span data-stu-id="0468b-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="0468b-148">Druhý představují *levé asociativní* výrazy.</span><span class="sxs-lookup"><span data-stu-id="0468b-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="0468b-149">Výhodou obou těchto dvou formátů je, že formát se škáluje na libovolný počet výrazů sčítání.</span><span class="sxs-lookup"><span data-stu-id="0468b-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="0468b-150">Pokud spustíte tento výraz prostřednictvím návštěvníka, zobrazí se tento výstup, ověření, že jednoduchý výraz sčítání je *ponechána asociativní*.</span><span class="sxs-lookup"><span data-stu-id="0468b-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="0468b-151">Chcete-li spustit tuto ukázku a zobrazit celý strom výrazu, musel jsem provést jednu změnu stromu zdrojového výrazu.</span><span class="sxs-lookup"><span data-stu-id="0468b-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="0468b-152">Pokud strom výrazu obsahuje všechny konstanty, výsledný strom `10`jednoduše obsahuje konstantní hodnotu .</span><span class="sxs-lookup"><span data-stu-id="0468b-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="0468b-153">Kompilátor provede všechny sčítání a snižuje výraz na jeho nejjednodušší formu.</span><span class="sxs-lookup"><span data-stu-id="0468b-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="0468b-154">Jednoduše přidání jedné proměnné ve výrazu je dostačující pro zobrazení původního stromu:</span><span class="sxs-lookup"><span data-stu-id="0468b-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="0468b-155">Vytvořte návštěvníka pro tuto částku a spusťte návštěvníka uvidíte tento výstup:</span><span class="sxs-lookup"><span data-stu-id="0468b-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```output
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

<span data-ttu-id="0468b-156">Můžete také spustit některý z dalších vzorků prostřednictvím kódu návštěvníka a zjistit, jaký strom představuje.</span><span class="sxs-lookup"><span data-stu-id="0468b-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="0468b-157">Zde je příklad výše `sum3` uvedeného výrazu (s dalším parametrem, který zabrání kompilátoru v výpočtu konstanty):</span><span class="sxs-lookup"><span data-stu-id="0468b-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="0468b-158">Zde je výstup z návštěvníka:</span><span class="sxs-lookup"><span data-stu-id="0468b-158">Here's the output from the visitor:</span></span>

```output
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

<span data-ttu-id="0468b-159">Všimněte si, že závorky nejsou součástí výstupu.</span><span class="sxs-lookup"><span data-stu-id="0468b-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="0468b-160">Ve stromu výrazů nejsou žádné uzly, které představují závorky ve vstupním výrazu.</span><span class="sxs-lookup"><span data-stu-id="0468b-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="0468b-161">Struktura stromu výrazobsahuje všechny informace potřebné ke sdělení priority.</span><span class="sxs-lookup"><span data-stu-id="0468b-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="0468b-162">Rozšíření z tohoto vzorku</span><span class="sxs-lookup"><span data-stu-id="0468b-162">Extending from this sample</span></span>

<span data-ttu-id="0468b-163">Ukázka se zabývá pouze nejvíce základní výraz stromy.</span><span class="sxs-lookup"><span data-stu-id="0468b-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="0468b-164">Kód, který jste viděli v této části zpracovává pouze konstantní `+` celá čísla a binární operátor.</span><span class="sxs-lookup"><span data-stu-id="0468b-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="0468b-165">Jako poslední ukázku aktualizujte návštěvníka, aby zpracovat složitější výraz.</span><span class="sxs-lookup"><span data-stu-id="0468b-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="0468b-166">Ať to funguje na toto:</span><span class="sxs-lookup"><span data-stu-id="0468b-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="0468b-167">Tento kód představuje jednu možnou implementaci matematické *faktoriální* funkce.</span><span class="sxs-lookup"><span data-stu-id="0468b-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="0468b-168">Způsob, jakým jsem napsal tento kód zvýrazní dvě omezení vytváření stromů výrazů přiřazením lambda výrazy výrazy výrazy.</span><span class="sxs-lookup"><span data-stu-id="0468b-168">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="0468b-169">Za prvé, prohlášení lambdas nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="0468b-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="0468b-170">To znamená, že nelze použít smyčky, bloky, if / else příkazy a další řídicí struktury běžné v C#.</span><span class="sxs-lookup"><span data-stu-id="0468b-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="0468b-171">Jsem omezen na používání výrazů.</span><span class="sxs-lookup"><span data-stu-id="0468b-171">I'm limited to using expressions.</span></span> <span data-ttu-id="0468b-172">Za druhé nemohu rekurzivně volat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="0468b-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="0468b-173">Mohl bych, kdyby to byl již delegát, ale nemohu volat ve formě stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="0468b-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="0468b-174">V části o [vytváření stromů výrazů](expression-trees-building.md) se naučíte techniky k překonání těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="0468b-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="0468b-175">V tomto výrazu narazíte na uzly všech těchto typů:</span><span class="sxs-lookup"><span data-stu-id="0468b-175">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="0468b-176">Equal (binární výraz)</span><span class="sxs-lookup"><span data-stu-id="0468b-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="0468b-177">Násobení (binární výraz)</span><span class="sxs-lookup"><span data-stu-id="0468b-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="0468b-178">Podmíněné (?</span><span class="sxs-lookup"><span data-stu-id="0468b-178">Conditional (the ?</span></span> <span data-ttu-id="0468b-179">: výraz)</span><span class="sxs-lookup"><span data-stu-id="0468b-179">: expression)</span></span>
4. <span data-ttu-id="0468b-180">Výraz volání metody `Range()` `Aggregate()`(volání a )</span><span class="sxs-lookup"><span data-stu-id="0468b-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="0468b-181">Jedním ze způsobů, jak upravit algoritmus návštěvníka je, aby jeho provádění `default` a psát typ uzlu pokaždé, když dosáhnete klauzule.</span><span class="sxs-lookup"><span data-stu-id="0468b-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="0468b-182">Po několika iterací, budete mít viděli každý z potenciálních uzlů.</span><span class="sxs-lookup"><span data-stu-id="0468b-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="0468b-183">Pak máte vše, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="0468b-183">Then, you have all you need.</span></span> <span data-ttu-id="0468b-184">Výsledkem by bylo něco takového:</span><span class="sxs-lookup"><span data-stu-id="0468b-184">The result would be something like this:</span></span>

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

<span data-ttu-id="0468b-185">ConditionalVisitor a MethodCallVisitor zpracovat tyto dva uzly:</span><span class="sxs-lookup"><span data-stu-id="0468b-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="0468b-186">A výstup pro strom výrazby:</span><span class="sxs-lookup"><span data-stu-id="0468b-186">And the output for the expression tree would be:</span></span>

```output
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

## <a name="extending-the-sample-library"></a><span data-ttu-id="0468b-187">Rozšíření ukázkové knihovny</span><span class="sxs-lookup"><span data-stu-id="0468b-187">Extending the Sample Library</span></span>

<span data-ttu-id="0468b-188">Ukázky v této části zobrazit základní techniky k návštěvě a prozkoumání uzly ve stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="0468b-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="0468b-189">I glosoval mnoho akcí, které byste mohli potřebovat, aby se soustředit na základní úkoly návštěvy a přístup uzly ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="0468b-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="0468b-190">Za prvé, návštěvníci zpracovávají pouze konstanty, které jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="0468b-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="0468b-191">Konstantní hodnoty může být jakýkoli jiný číselný typ a jazyk C# podporuje převody a propagační akce mezi těmito typy.</span><span class="sxs-lookup"><span data-stu-id="0468b-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="0468b-192">Robustnější verze tohoto kódu by zrcadlit všechny tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="0468b-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="0468b-193">I poslední příklad rozpozná podmnožinu možných typů uzlů.</span><span class="sxs-lookup"><span data-stu-id="0468b-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="0468b-194">Stále jej můžete krmit mnoha výrazy, které způsobí, že se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="0468b-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="0468b-195">Úplná implementace je zahrnuta v standardu .NET pod názvem <xref:System.Linq.Expressions.ExpressionVisitor> a může zpracovat všechny možné typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="0468b-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="0468b-196">Konečně, knihovna jsem použil v tomto článku byl postaven pro demonstraci a učení.</span><span class="sxs-lookup"><span data-stu-id="0468b-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="0468b-197">Není to optimalizované.</span><span class="sxs-lookup"><span data-stu-id="0468b-197">It's not optimized.</span></span> <span data-ttu-id="0468b-198">Napsal jsem to, aby se struktury používané velmi jasné, a upozornit na techniky používané k návštěvě uzly a analyzovat, co tam je.</span><span class="sxs-lookup"><span data-stu-id="0468b-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="0468b-199">Implementace výroby by věnovala větší pozornost výkonu než já.</span><span class="sxs-lookup"><span data-stu-id="0468b-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="0468b-200">I s těmito omezeními byste měli být na dobré cestě k psaní algoritmů, které čtou a rozumí stromům výrazů.</span><span class="sxs-lookup"><span data-stu-id="0468b-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="0468b-201">Další -- Stavební výrazy</span><span class="sxs-lookup"><span data-stu-id="0468b-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
