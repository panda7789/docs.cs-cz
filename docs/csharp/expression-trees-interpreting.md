---
title: Interpretace výrazů
description: Naučte se psát kód pro kontrolu struktury stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 5734e1be6b59bfe3eae97f29d1bd91e7e3a3623f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761860"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="ce8c1-103">Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="ce8c1-103">Interpreting Expressions</span></span>

[<span data-ttu-id="ce8c1-104">Předchozí výrazy, které se spouštějí</span><span class="sxs-lookup"><span data-stu-id="ce8c1-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="ce8c1-105">Nyní napíšeme nějaký kód pro prověření struktury *stromu výrazů*.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="ce8c1-106">Každý uzel ve stromové struktuře výrazu bude objektem třídy, která je odvozena z `Expression` .</span><span class="sxs-lookup"><span data-stu-id="ce8c1-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="ce8c1-107">Tento návrh usnadňuje návštěvu všech uzlů ve stromu výrazů a poměrně rovnou rekurzivní operaci dopřednou.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="ce8c1-108">Obecnou strategií je začít na kořenovém uzlu a určit, jaký typ uzlu je.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="ce8c1-109">Pokud uzel má podřízené položky, rekurzivně navštíví podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="ce8c1-110">V každém podřízeném uzlu opakujte proces použitý v kořenovém uzlu: určení typu, a pokud má typ podřízené, navštivte jednotlivé podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="ce8c1-111">Zkoumání výrazu bez podřízených</span><span class="sxs-lookup"><span data-stu-id="ce8c1-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="ce8c1-112">Pojďme začít návštěvou každého uzlu ve vysoce jednoduchém stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="ce8c1-113">Zde je kód, který vytvoří konstantní výraz a pak prověřuje jeho vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="ce8c1-114">Vytiskne se následující:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="ce8c1-115">Nyní napíšeme kód, který by prozkoumal tento výraz, a vypíšeme z něj některé důležité vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="ce8c1-116">Zde je tento kód:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="ce8c1-117">Prozkoumání jednoduchého výrazu sčítání</span><span class="sxs-lookup"><span data-stu-id="ce8c1-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="ce8c1-118">Pojďme začít s ukázkou sčítání z úvodu do této části.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="ce8c1-119">Nepoužívám `var` deklaraci tohoto stromu výrazů, protože není možné, protože pravá strana přiřazení je implicitně typu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span>

<span data-ttu-id="ce8c1-120">Kořenový uzel je `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="ce8c1-120">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="ce8c1-121">Aby bylo možné získat zajímavý kód na pravé straně `=>` operátoru, je nutné najít jeden z podřízených objektů `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="ce8c1-121">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="ce8c1-122">Provedeme to se všemi výrazy v této části.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-122">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="ce8c1-123">Nadřazený uzel nám pomohly najít návratový typ `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="ce8c1-123">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="ce8c1-124">Abychom prozkoumali jednotlivé uzly v tomto výrazu, budeme muset rekurzivně navštívit několik uzlů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-124">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="ce8c1-125">Tady je jednoduchá první implementace:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-125">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="ce8c1-126">Tato ukázka vytiskne následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-126">This sample prints the following output:</span></span>

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

<span data-ttu-id="ce8c1-127">Ve výše uvedeném příkladu kódu si všimnete spousty opakování.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-127">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="ce8c1-128">Pojďme vyčistit a vytvořit obecnější návštěvníka uzlu výrazu pro obecné účely.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-128">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="ce8c1-129">To bude vyžadovat, abychom napsali rekurzivní algoritmus.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-129">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="ce8c1-130">Libovolný uzel může být typu, který může mít podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-130">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="ce8c1-131">Všechny uzly, které mají podřízené objekty, vyžadují, aby nás navštívili tyto podřízené položky a určili, co je tento uzel.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-131">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="ce8c1-132">Zde je vyčištěná verze, která využívá rekurzi k návštěvě operací sčítání:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-132">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="ce8c1-133">Tento algoritmus je základem algoritmu, který může libovolně navštívit libovolný objekt `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="ce8c1-133">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="ce8c1-134">Existuje spousta děr, což znamená, že kód, který jsem vytvořil, vyhledává jenom velmi malý vzorek možných sad uzlů stromu výrazů, ke kterým může dojít.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-134">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="ce8c1-135">Stále ale můžete zjistit, jak trochu z toho vyprodukuje.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-135">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="ce8c1-136">(Výchozí případ v `Visitor.CreateFromExpression` metodě vytiskne zprávu do chybové konzoly při zjištění nového typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-136">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="ce8c1-137">Tímto způsobem víte, že chcete přidat nový typ výrazu.)</span><span class="sxs-lookup"><span data-stu-id="ce8c1-137">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="ce8c1-138">Po spuštění tohoto návštěvníka na výše uvedeném výrazu sčítání získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-138">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

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

<span data-ttu-id="ce8c1-139">Teď, když jste vytvořili obecnější implementaci návštěvníka, můžete navštívit a zpracovat spoustu více různých typů výrazů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-139">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="ce8c1-140">Zkoumání výrazu sčítání s mnoha úrovněmi</span><span class="sxs-lookup"><span data-stu-id="ce8c1-140">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="ce8c1-141">Pojďme si vyzkoušet složitější příklad, stále ale omezit typy uzlů jenom na sčítání:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-141">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="ce8c1-142">Před spuštěním tohoto algoritmu pro návštěvníky Vyzkoušejte myšlenkový postup, který bude fungovat jako výstup.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-142">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="ce8c1-143">Uvědomte si, že `+` operátor je *binární operátor*: musí mít dvě podřízené prvky, reprezentující levý a pravý operand.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-143">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="ce8c1-144">Existuje několik možných způsobů, jak vytvořit stromovou strukturu, která může být správná:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-144">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="ce8c1-145">V případě, že se chcete podívat na nejvíc vyslibování, můžete zobrazit rozdělení na dvě možné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-145">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="ce8c1-146">První představuje *pravé asociativní* výrazy.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-146">The first represents *right associative* expressions.</span></span> <span data-ttu-id="ce8c1-147">Druhý představuje *levé asociativní* výrazy.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-147">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="ce8c1-148">Výhodou obou obou formátů je, že formát se škáluje libovolným počtem výrazů sčítání.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-148">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="ce8c1-149">Pokud tento výraz spouštíte prostřednictvím návštěvníka, zobrazí se tento výstup a ověří se, jestli je výraz jednoduchého přidání *ponechán asociativní*.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-149">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="ce8c1-150">Chcete-li spustit tuto ukázku a zobrazit úplný strom výrazů, je nutné provést jednu změnu stromu zdrojového výrazu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-150">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="ce8c1-151">Pokud strom výrazu obsahuje všechny konstanty, výsledný strom jednoduše obsahuje konstantní hodnotu `10` .</span><span class="sxs-lookup"><span data-stu-id="ce8c1-151">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="ce8c1-152">Kompilátor provede veškeré přidání a zmenší výraz na jeho nejjednodušší formu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-152">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="ce8c1-153">Stačí přidat jednu proměnnou ve výrazu stačí k zobrazení původního stromu:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-153">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="ce8c1-154">Vytvořte návštěvníka tohoto součtu a spusťte návštěvníka, na který se zobrazí tento výstup:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-154">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

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

<span data-ttu-id="ce8c1-155">Můžete také spustit libovolný z dalších ukázek prostřednictvím kódu návštěvníka a zjistit, který strom představuje.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-155">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="ce8c1-156">Zde je příklad `sum3` výše uvedeného výrazu (s dalším parametrem, který zabrání kompilátoru v výpočtu konstanty):</span><span class="sxs-lookup"><span data-stu-id="ce8c1-156">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="ce8c1-157">Tady je výstup návštěvníka:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-157">Here's the output from the visitor:</span></span>

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

<span data-ttu-id="ce8c1-158">Všimněte si, že kulaté závorky nejsou součástí výstupu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-158">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="ce8c1-159">Ve stromové struktuře výrazu nejsou žádné uzly, které představují závorky ve vstupním výrazu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-159">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="ce8c1-160">Struktura stromu výrazů obsahuje všechny informace potřebné pro komunikaci s prioritou.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-160">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="ce8c1-161">Rozšíření z této ukázky</span><span class="sxs-lookup"><span data-stu-id="ce8c1-161">Extending from this sample</span></span>

<span data-ttu-id="ce8c1-162">Ukázka se zabývá pouze základní stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-162">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="ce8c1-163">Kód, který jste viděli v této části, zpracovává pouze konstantní celá čísla a binární `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-163">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="ce8c1-164">Jako poslední ukázka Pojďme aktualizovat návštěvníka na zpracování složitějšího výrazu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-164">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="ce8c1-165">Pojďme na to, aby to fungovalo:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-165">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="ce8c1-166">Tento kód představuje jednu možnou implementaci funkce matematického *faktoriál* .</span><span class="sxs-lookup"><span data-stu-id="ce8c1-166">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="ce8c1-167">Způsob, jakým jsem tento kód napsal, zvýrazní dvě omezení pro vytváření stromů výrazů přiřazením výrazů lambda výrazům.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-167">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="ce8c1-168">První příkazy výrazy lambda nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-168">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="ce8c1-169">To znamená, že nemůžu použít smyčky, bloky, příkazy if/else a další řídicí struktury společné v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-169">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="ce8c1-170">Je omezeno na použití výrazů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-170">I'm limited to using expressions.</span></span> <span data-ttu-id="ce8c1-171">Za druhé nelze rekurzivně volat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-171">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="ce8c1-172">Můžu se už delegovat, ale nemůžu ho zavolat ve formuláři jeho stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-172">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="ce8c1-173">V části o [sestavování stromů výrazů](expression-trees-building.md) se naučíte techniky, jak překonat tato omezení.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-173">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="ce8c1-174">V tomto výrazu se setkáte s uzly všech těchto typů:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-174">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="ce8c1-175">EQUAL (binární výraz)</span><span class="sxs-lookup"><span data-stu-id="ce8c1-175">Equal (binary expression)</span></span>
2. <span data-ttu-id="ce8c1-176">Násobení (binární výraz)</span><span class="sxs-lookup"><span data-stu-id="ce8c1-176">Multiply (binary expression)</span></span>
3. <span data-ttu-id="ce8c1-177">Podmíněný (?</span><span class="sxs-lookup"><span data-stu-id="ce8c1-177">Conditional (the ?</span></span> <span data-ttu-id="ce8c1-178">vyjádření</span><span class="sxs-lookup"><span data-stu-id="ce8c1-178">: expression)</span></span>
4. <span data-ttu-id="ce8c1-179">Výraz volání metody (volání `Range()` a `Aggregate()` )</span><span class="sxs-lookup"><span data-stu-id="ce8c1-179">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="ce8c1-180">Jedním ze způsobů, jak změnit algoritmus návštěvníka, je zachovat jeho spuštění a napsat typ uzlu při každém dosažení `default` klauzule.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-180">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="ce8c1-181">Po několika iteracích se vám podíváte na každý z možných uzlů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-181">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="ce8c1-182">Pak budete mít všechno, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-182">Then, you have all you need.</span></span> <span data-ttu-id="ce8c1-183">Výsledek by byl podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-183">The result would be something like this:</span></span>

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

<span data-ttu-id="ce8c1-184">ConditionalVisitor a MethodCallVisitor zpracují tyto dva uzly:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-184">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="ce8c1-185">A výstup pro strom výrazu by byl:</span><span class="sxs-lookup"><span data-stu-id="ce8c1-185">And the output for the expression tree would be:</span></span>

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

## <a name="extending-the-sample-library"></a><span data-ttu-id="ce8c1-186">Rozšíření knihovny ukázek</span><span class="sxs-lookup"><span data-stu-id="ce8c1-186">Extending the Sample Library</span></span>

<span data-ttu-id="ce8c1-187">Ukázky v této části znázorňují základní postupy pro návštěvě a prohlédnutí uzlů ve stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-187">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="ce8c1-188">V rámci řady akcí může být nutné se soustředit na základní úlohy při návštěvě a přístupu k uzlům ve stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-188">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="ce8c1-189">Nejprve Návštěvníci zpracovávají pouze konstanty, které jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-189">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="ce8c1-190">Konstantní hodnoty mohou být jakékoli jiné číselné typy a jazyk C# podporuje převody a propagační akce mezi těmito typy.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-190">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="ce8c1-191">Robustnější verze tohoto kódu by znamenala zrcadlení všech možností.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-191">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="ce8c1-192">I poslední příklad rozpozná podmnožinu možných typů uzlů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-192">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="ce8c1-193">Můžete si i nadále zaniknout mnoho výrazů, které způsobí selhání.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-193">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="ce8c1-194">Úplná implementace je obsažena v .NET Standard pod názvem <xref:System.Linq.Expressions.ExpressionVisitor> a může zpracovat všechny možné typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-194">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="ce8c1-195">Nakonec se knihovna, kterou jste použili v tomto článku, vytvořila pro účely ukázky a učení.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-195">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="ce8c1-196">Není optimalizovaná.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-196">It's not optimized.</span></span> <span data-ttu-id="ce8c1-197">Napsal jsem si, že se tyto struktury využívaly velmi jasné, a zvýraznit techniky používané k návštěvě uzlů a analyzovat, co je tam.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-197">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="ce8c1-198">Implementace v produkčním prostředí by měla věnovat větší pozornost výkonu, než mám.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-198">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="ce8c1-199">I s těmito omezeními byste měli být na cestě, jak píšete algoritmy, které čtou a porozumět stromům výrazů.</span><span class="sxs-lookup"><span data-stu-id="ce8c1-199">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="ce8c1-200">Další – sestavování výrazů</span><span class="sxs-lookup"><span data-stu-id="ce8c1-200">Next -- Building Expressions</span></span>](expression-trees-building.md)
