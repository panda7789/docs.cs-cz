---
title: Interpretace výrazů
description: Zjistěte, jak napsat kód, který zkontrolujte strukturu stromu výrazů.
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 49c030706a0a6196dfdd72e3c2fbff90b7667f48
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201973"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="6a6d5-103">Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="6a6d5-103">Interpreting Expressions</span></span>

[<span data-ttu-id="6a6d5-104">Předchozí – Provádění výrazů</span><span class="sxs-lookup"><span data-stu-id="6a6d5-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="6a6d5-105">Nyní napíšeme nějaký kód ke kontrole struktury *stromu výrazů*.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="6a6d5-106">Každý uzel ve stromu výrazů bude objekt, který je odvozen od třídy `Expression`.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="6a6d5-107">Tento návrh díky navštívit všech uzlů ve stromu výrazu relativně přímo dopředné rekurzivní operace.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="6a6d5-108">Ke spuštění v kořenovém uzlu a zjistit, jaký druh uzlu je je obecná strategie.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="6a6d5-109">Pokud má typ uzlu podřízené položky, navštivte rekurzivně podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="6a6d5-110">V každém uzlu podřízené zopakovat tento proces používá v kořenovém uzlu: určení typu a pokud má typ podřízené položky, navštivte každou podřízenou položku.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="6a6d5-111">Zkoumání výraz s žádné podřízené položky</span><span class="sxs-lookup"><span data-stu-id="6a6d5-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="6a6d5-112">Začněme tím, že navštívit každý uzel ve stromu výrazu velmi jednoduché.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="6a6d5-113">Tady je kód, který vytvoří konstantní výraz a poté zkoumá jeho vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="6a6d5-114">Tím se vytisknou následující:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-114">This will print the following:</span></span>

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="6a6d5-115">Nyní napíšeme kód, který by prozkoumat tento výraz a vypsat některé důležité vlastnosti o něm.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="6a6d5-116">Zde je, že kód:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="6a6d5-117">Prozkoumání jednoduchého Přidání výrazu</span><span class="sxs-lookup"><span data-stu-id="6a6d5-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="6a6d5-118">Začněme s ukázkou přidání z úvodu k této sekci.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="6a6d5-119">Nepoužívám `var` deklarovat tento strom výrazu, protože není možné protože pravá strana přiřazení je implicitně typované.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="6a6d5-120">Pro lepší vysvětlení hlouběji, přečtěte si [tady](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6a6d5-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="6a6d5-121">Je kořenový uzel `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="6a6d5-122">Pokud chcete získat kód zajímavé na pravé straně výrazu `=>` operátoru, je potřeba najít jeden z podřízených položek `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="6a6d5-123">Můžeme to udělat pomocí všechny výrazy v této části.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="6a6d5-124">Nadřazený uzel pomohl nám pomohly s nalezením návratového typu `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="6a6d5-125">Prozkoumat každý uzel v tomto výrazu, budeme potřebovat k rekurzivnímu navštěvovat počet uzlů.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="6a6d5-126">Tady je jednoduchý první implementace:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-126">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="6a6d5-127">Tato ukázka zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-127">This sample prints the following output:</span></span>

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

<span data-ttu-id="6a6d5-128">Můžete si všimnout velké množství opakování v ukázkovém kódu výše.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="6a6d5-129">Pojďme, který vyčistit a sestavit další obecné účely výraz uzlu návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="6a6d5-130">Který se bude vyžadovat nám napsat rekurzivní algoritmus.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="6a6d5-131">Libovolný uzel může být typu, který může mít podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="6a6d5-132">Libovolný uzel, který má podřízené položky vyžaduje, abychom navštivte tyto podřízené objekty a zjistit, co je tento uzel.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="6a6d5-133">Tady je verze, která využívá rekurze pro návštěvu operace sčítání vyčištěnou:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="6a6d5-134">Tento algoritmus je základem algoritmus, který získáte všechny libovolného `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="6a6d5-135">Existuje mnoho děr, konkrétně bude vypadat kód jsem vytvořil jenom velmi malé ukázku možné sad uzlů stromu výrazu, které mohou nastat.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="6a6d5-136">Ale taky další odlišují od ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="6a6d5-137">(Výchozí případ `Visitor.CreateFromExpression` metoda vytiskne zprávu do konzoly chyba vyskytne nového typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="6a6d5-138">Díky tomu víte, chcete-li přidat nový typ výrazu.)</span><span class="sxs-lookup"><span data-stu-id="6a6d5-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="6a6d5-139">Když spustíte tohoto návštěvníka na přidání výrazu je znázorněno výše, získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

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

<span data-ttu-id="6a6d5-140">Teď, když jste vytvořili více obecnou implementaci návštěvníka, můžete navštívit a zpracovávat více různé typy výrazů.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="6a6d5-141">Zkoumání Přidání výrazu s několika úrovněmi</span><span class="sxs-lookup"><span data-stu-id="6a6d5-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="6a6d5-142">Teď zkuste složitější příklad, ale stále omezit na přidání pouze typy uzlů:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="6a6d5-143">Předtím, než spustíte to na algoritmu návštěvníka, zkuste cvičení promyslet tak co může být výstup.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="6a6d5-144">Nezapomeňte, že `+` operátor je *binární operátor*: musí mít dva podřízené prvky představující operandy vlevo a vpravo.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="6a6d5-145">Vytvoření stromu, který by mohl být správné několika možné způsoby:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="6a6d5-146">Zobrazí se oddělení do dva možné odpovědi, zvýrazněte nejvíce příslibů.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="6a6d5-147">První představuje *asociativní zprava* výrazy.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="6a6d5-148">Druhý představují *asociativní zleva* výrazy.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="6a6d5-149">Obě tyto dva formáty výhodou je, formát škáluje, aby libovolný libovolný počet výrazů sčítání.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="6a6d5-150">Při spuštění tohoto výrazu prostřednictvím návštěvníka, zobrazí se tím tento výstup, ověření, je přidání jednoduchého výrazu *asociativní zleva*.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="6a6d5-151">Pokud chcete tuto ukázku spustit a viděli stromu úplného výrazu, můžu museli měnit jeden na strom výrazu zdroje.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="6a6d5-152">Strom výrazu obsahuje všechny konstanty, výsledný strom jednoduše obsahuje konstantní hodnotu `10`.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="6a6d5-153">Kompilátor provádí všechna sčítání a snižuje výraz, který má své nejjednodušší podobě.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="6a6d5-154">Zobrazíte stromu původní stačí jednoduše přidat jednu proměnnou ve výrazu:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="6a6d5-155">Vytvořte pro tento součet návštěvník a spusťte návštěvníka, který se zobrazí tento výstup:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

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

<span data-ttu-id="6a6d5-156">Můžete také spustit některý z ostatních vzorků návštěvníka kód a zobrazit stromu, které představuje.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="6a6d5-157">Tady je příklad `sum3` výraz výše (s dalším parametrem pro zabránění kompilátoru computingu konstanty):</span><span class="sxs-lookup"><span data-stu-id="6a6d5-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="6a6d5-158">Zde se nachází výstup z návštěvníka:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-158">Here's the output from the visitor:</span></span>

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

<span data-ttu-id="6a6d5-159">Všimněte si, že závorky nejsou součástí výstupu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="6a6d5-160">Nejsou žádné uzly ve stromu výrazů, které představují závorky v vstupní výraz.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="6a6d5-161">Struktura stromu výrazů obsahuje všechny informace potřebné ke komunikaci prioritu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="6a6d5-162">Rozšíření od této ukázky</span><span class="sxs-lookup"><span data-stu-id="6a6d5-162">Extending from this sample</span></span>

<span data-ttu-id="6a6d5-163">Ukázka se zabývá pouze nejvíce základní stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="6a6d5-164">Kód v této části jste viděli pouze zpracovává konstantních celých čísel a binární soubor `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="6a6d5-165">Jako ukázku poslední můžeme aktualizovat návštěvníka pro zpracování složitějších výrazů.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="6a6d5-166">Můžeme nechat pracovat pro toto:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="6a6d5-167">Tento kód představuje jednu možnou implementaci matematické *faktoriál* funkce.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="6a6d5-168">Způsob, jakým napsali tento kód ukazuje dvě omezení vytváření stromů výrazů přiřazením výrazy lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-168">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="6a6d5-169">Nejprve lambda nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="6a6d5-170">To znamená nejde mi využít smyčky, bloky, pokud / else příkazy a další ovládací prvek struktury, které jsou běžné v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="6a6d5-171">Já jsem můžete používat výrazy.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-171">I'm limited to using expressions.</span></span> <span data-ttu-id="6a6d5-172">Za druhé nelze rekurzivní volání stejného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="6a6d5-173">Uvidím, pokud již byly delegáta, ale nelze volat v podobě stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="6a6d5-174">V části o [vytváření stromů výrazů](expression-trees-building.md) dozvíte techniky k překonání těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>


<span data-ttu-id="6a6d5-175">V tomto výrazu narazíte uzly z těchto typů:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-175">In this expression, you'll encounter nodes of all these types:</span></span>
1. <span data-ttu-id="6a6d5-176">Stejné (binární výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6d5-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="6a6d5-177">Násobení (binární výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6d5-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="6a6d5-178">Podmíněný ()?</span><span class="sxs-lookup"><span data-stu-id="6a6d5-178">Conditional (the ?</span></span> <span data-ttu-id="6a6d5-179">: výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6d5-179">: expression)</span></span>
4. <span data-ttu-id="6a6d5-180">Metoda volání výrazu (volání `Range()` a `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="6a6d5-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="6a6d5-181">Jedním způsobem, jak upravit návštěvníka algoritmus je zachovat, ale jeho spuštění, a zapisovat typ uzlu pokaždé, když dostanete vaše `default` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="6a6d5-182">Po několika iteracích budete mít víte, každý potenciální uzlů.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="6a6d5-183">Pak máte všechno, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-183">Then, you have all you need.</span></span> <span data-ttu-id="6a6d5-184">Výsledek bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-184">The result would be something like this:</span></span>

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

<span data-ttu-id="6a6d5-185">ConditionalVisitor a MethodCallVisitor zpracovat tyto dva uzly:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="6a6d5-186">A bude výstup do stromu výrazů:</span><span class="sxs-lookup"><span data-stu-id="6a6d5-186">And the output for the expression tree would be:</span></span>

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

## <a name="extending-the-sample-library"></a><span data-ttu-id="6a6d5-187">Rozšíření ukázky knihovny</span><span class="sxs-lookup"><span data-stu-id="6a6d5-187">Extending the Sample Library</span></span>

<span data-ttu-id="6a6d5-188">Příklady v této části ukazují techniky core najdete a uzlů ve stromu výrazů zkoumat.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="6a6d5-189">Můžu glossed přes mnoho akcí, které je třeba, abyste se mohli soustředit na základní úkoly návštěv a přístup k uzly ve stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="6a6d5-190">Nejprve návštěvníkům zpracovat pouze konstanty, které jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="6a6d5-191">Konstantní hodnoty, může být libovolného číselného typu a jazyka C# podporuje převody a propagační akce mezi těmito typy.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="6a6d5-192">Robustnější verze tohoto kódu bude zrcadlit všechny tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="6a6d5-193">V poslední příkladu rozpozná podmnožinu typů možného uzlu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="6a6d5-194">Vám může stále informačního kanálu je mnoho výrazů, které způsobí, že selhala.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="6a6d5-195">Celé provedení je zahrnuto v .NET Standard pod názvem <xref:System.Linq.Expressions.ExpressionVisitor> a dokáže pojmout všechny typy možného uzlu.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="6a6d5-196">A konečně byla vytvořena knihovna, kterou jsem používal v tomto článku pro ukázkové a výukové.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="6a6d5-197">Není optimalizována.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-197">It's not optimized.</span></span> <span data-ttu-id="6a6d5-198">Napsal jsem ho tak, aby struktury používá jasný a abyste měli na očích techniky najdete uzly a analýzu, co je.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="6a6d5-199">Provozní implementace by platit další pozornost k výkonu, než budu mít.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="6a6d5-200">I s těmito omezeními měli byste být na dobré cestě k psaní algoritmy, které čtou a vysvětlení stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="6a6d5-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="6a6d5-201">Další--Sestavení výrazy</span><span class="sxs-lookup"><span data-stu-id="6a6d5-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
