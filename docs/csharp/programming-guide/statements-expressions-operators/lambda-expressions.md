---
title: Výrazy lambda – C# Průvodce programováním
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 786c2937a3f413170665c39464dc2c94417008ad
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331367"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="7093a-102">Výrazy lambda (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="7093a-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="7093a-103">*Výraz lambda* je blok kódu (výraz nebo blok příkazu), který je považován za objekt.</span><span class="sxs-lookup"><span data-stu-id="7093a-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="7093a-104">Může být předán jako argument metodám a může být také vrácen voláním metody.</span><span class="sxs-lookup"><span data-stu-id="7093a-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="7093a-105">Výrazy lambda se používají rozsáhle pro:</span><span class="sxs-lookup"><span data-stu-id="7093a-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="7093a-106">Předání kódu, který má být proveden na asynchronní metody, například <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7093a-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="7093a-107">Zápis [výrazů dotazů LINQ](../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="7093a-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="7093a-108">Vytváření [stromů výrazů](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="7093a-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="7093a-109">Lambda výrazy jsou kód, který lze reprezentovat buď jako delegát, nebo jako strom výrazu, který se zkompiluje do delegáta.</span><span class="sxs-lookup"><span data-stu-id="7093a-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="7093a-110">Konkrétní typ delegáta výrazu lambda závisí na jeho parametrech a návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="7093a-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="7093a-111">Lambda výrazy, které nevracejí hodnotu odpovídají konkrétnímu `Action` delegátu, v závislosti na počtu parametrů.</span><span class="sxs-lookup"><span data-stu-id="7093a-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="7093a-112">Lambda výrazy, které vracejí hodnotu odpovídají konkrétnímu `Func` delegátu v závislosti na počtu parametrů.</span><span class="sxs-lookup"><span data-stu-id="7093a-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="7093a-113">Například výraz lambda, který má dva parametry, ale nevrací žádnou hodnotu, <xref:System.Action%602> odpovídá delegátu.</span><span class="sxs-lookup"><span data-stu-id="7093a-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="7093a-114">Výraz lambda, který má jeden parametr a vrací hodnotu, odpovídá <xref:System.Func%602> delegátu.</span><span class="sxs-lookup"><span data-stu-id="7093a-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="7093a-115">Výraz lambda používá `=>` [operátor deklarace lambda](../../language-reference/operators/lambda-operator.md), který odděluje seznam parametrů lambda ze spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="7093a-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="7093a-116">Chcete-li vytvořit výraz lambda, zadejte vstupní parametry (pokud existují) na levé straně operátoru lambda a umístěte blok výrazu nebo příkazu na druhou stranu.</span><span class="sxs-lookup"><span data-stu-id="7093a-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="7093a-117">Například výraz `x => x * x` lambda s jedním řádkem určuje parametr s názvem `x` `x` a vrátí hodnotu Square.</span><span class="sxs-lookup"><span data-stu-id="7093a-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="7093a-118">Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="7093a-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="7093a-119">Lambda výraz můžete také přiřadit typu stromu výrazu:</span><span class="sxs-lookup"><span data-stu-id="7093a-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="7093a-120">Nebo ho můžete předat přímo jako argument metody:</span><span class="sxs-lookup"><span data-stu-id="7093a-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="7093a-121">Použijete-li syntaxi založenou na metodě pro <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> volání metody <xref:System.Linq.Enumerable?displayProperty=nameWithType> ve třídě (stejně jako v LINQ to Objects a LINQ to XML), parametr je typ <xref:System.Func%602?displayProperty=nameWithType>delegáta.</span><span class="sxs-lookup"><span data-stu-id="7093a-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7093a-122">Výraz lambda je nejvhodnějším způsobem vytvoření tohoto delegátu.</span><span class="sxs-lookup"><span data-stu-id="7093a-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="7093a-123">Při volání <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Queryable?displayProperty=nameWithType> ve třídě (stejně jako v LINQ to SQL) je typ parametru typ [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="7093a-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="7093a-124">Výraz lambda je opět pouze velmi stručným způsobem vytvoření tohoto stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="7093a-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="7093a-125">Výrazy lambda umožňují, `Select` aby volání vypadaly podobně, i když ve skutečnosti typ objektu vytvořeného z výrazu lambda je jiný.</span><span class="sxs-lookup"><span data-stu-id="7093a-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>

<span data-ttu-id="7093a-126">Všechna omezení, která platí pro [anonymní metody](anonymous-methods.md) , platí také pro výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="7093a-126">All restrictions that apply to [anonymous methods](anonymous-methods.md) also apply to lambda expressions.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="7093a-127">Výrazy lambda výrazu</span><span class="sxs-lookup"><span data-stu-id="7093a-127">Expression lambdas</span></span>

<span data-ttu-id="7093a-128">Výraz lambda s výrazem na pravé straně `=>` operátoru se nazývá výrazová *lambda*.</span><span class="sxs-lookup"><span data-stu-id="7093a-128">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="7093a-129">Výrazy lambda výrazů se v konstrukci [stromů výrazů](../concepts/expression-trees/index.md)používají rozsáhle.</span><span class="sxs-lookup"><span data-stu-id="7093a-129">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="7093a-130">Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:</span><span class="sxs-lookup"><span data-stu-id="7093a-130">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="7093a-131">Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="7093a-131">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="7093a-132">Zadejte nulové vstupní parametry s prázdnými závorkami:</span><span class="sxs-lookup"><span data-stu-id="7093a-132">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="7093a-133">Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:</span><span class="sxs-lookup"><span data-stu-id="7093a-133">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="7093a-134">V některých případech je možné, že kompilátor odvodí vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="7093a-134">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="7093a-135">Můžete určit typy explicitně, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7093a-135">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="7093a-136">Typy vstupních parametrů musí být všechny explicitní nebo všechny implicitní; v opačném případě dojde k chybě kompilátoru [CS0748](../../misc/cs0748.md) .</span><span class="sxs-lookup"><span data-stu-id="7093a-136">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="7093a-137">Tělo výrazu lambda se může skládat z volání metody.</span><span class="sxs-lookup"><span data-stu-id="7093a-137">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="7093a-138">Pokud však vytváříte stromy výrazů, které jsou vyhodnocovány mimo kontext modulu CLR (Common Language Runtime) .NET, například v SQL Server, neměli byste používat volání metody ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="7093a-138">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="7093a-139">Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7093a-139">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="7093a-140">Výrazy lambda příkazů</span><span class="sxs-lookup"><span data-stu-id="7093a-140">Statement lambdas</span></span>

<span data-ttu-id="7093a-141">Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:</span><span class="sxs-lookup"><span data-stu-id="7093a-141">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="7093a-142">Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.</span><span class="sxs-lookup"><span data-stu-id="7093a-142">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="7093a-143">Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.</span><span class="sxs-lookup"><span data-stu-id="7093a-143">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="7093a-144">Asynchronní výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="7093a-144">Async lambdas</span></span>

<span data-ttu-id="7093a-145">Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí klíčových slov [Async](../../language-reference/keywords/async.md) a [await](../../language-reference/keywords/await.md) .</span><span class="sxs-lookup"><span data-stu-id="7093a-145">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="7093a-146">Například následující příklad model Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="7093a-146">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="7093a-147">Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy.</span><span class="sxs-lookup"><span data-stu-id="7093a-147">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="7093a-148">Chcete-li přidat tuto obslužnou rutinu, přidejte `async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="7093a-148">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="7093a-149">Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="7093a-149">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="7093a-150">Výrazy lambda a řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="7093a-150">Lambda expressions and tuples</span></span>

<span data-ttu-id="7093a-151">Od verze C# 7,0 poskytuje C# jazyk integrovanou podporu pro [řazené kolekce členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="7093a-151">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="7093a-152">Můžete zadat řazenou kolekci členů jako argument pro lambda výraz a váš výraz lambda může také vrátit řazenou kolekci členů.</span><span class="sxs-lookup"><span data-stu-id="7093a-152">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="7093a-153">V některých případech C# kompilátor používá odvození typu k určení typů komponent řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="7093a-153">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="7093a-154">Řazenou kolekci členů můžete definovat tak, že v závorkách seřadíte seznam jeho komponent oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="7093a-154">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="7093a-155">Následující příklad používá řazené kolekce členů se třemi komponenty k předání sekvence čísel lambda výrazu, který zdvojnásobuje každou hodnotu a vrátí řazenou kolekci členů se třemi komponentami, které obsahují výsledek násobení.</span><span class="sxs-lookup"><span data-stu-id="7093a-155">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="7093a-156">Obvykle se pole řazené kolekce členů `Item1`nazývají, `Item2`atd. Můžete však definovat řazenou kolekci členů s pojmenovanými součástmi, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7093a-156">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="7093a-157">Další informace o C# řazených kolekcích členů naleznete v tématu [ C# typy řazené kolekce členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="7093a-157">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="7093a-158">Výrazy lambda se standardními operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="7093a-158">Lambdas with the standard query operators</span></span>

<span data-ttu-id="7093a-159">LINQ to Objects, mimo jiné implementace, má vstupní parametr, jehož typ je jeden z <xref:System.Func%601> řad generických delegátů.</span><span class="sxs-lookup"><span data-stu-id="7093a-159">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="7093a-160">Tito Delegáti používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="7093a-160">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="7093a-161">`Func`Delegáti jsou velmi užiteční pro zapouzdření uživatelsky definovaných výrazů, které jsou aplikovány na každý prvek v sadě zdrojových dat.</span><span class="sxs-lookup"><span data-stu-id="7093a-161">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="7093a-162">Zvažte například typ <xref:System.Func%602> delegáta:</span><span class="sxs-lookup"><span data-stu-id="7093a-162">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="7093a-163">Delegát může být vytvořen jako `Func<int, bool>` instance, kde `int` je vstupní parametr a `bool` je návratovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7093a-163">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="7093a-164">Vrácená hodnota je vždy určena v posledním parametru typu.</span><span class="sxs-lookup"><span data-stu-id="7093a-164">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="7093a-165">Například `Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry `string`, `int` a a návratový typ `bool`.</span><span class="sxs-lookup"><span data-stu-id="7093a-165">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="7093a-166">Následující `Func` delegát, pokud je vyvolána, vrátí logickou hodnotu, která označuje, zda je vstupní parametr roven pěti:</span><span class="sxs-lookup"><span data-stu-id="7093a-166">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="7093a-167">Výraz lambda lze také zadat <xref:System.Linq.Expressions.Expression%601>, pokud je typ argumentu, například ve standardních operátorech dotazu, které jsou definovány <xref:System.Linq.Queryable> v typu.</span><span class="sxs-lookup"><span data-stu-id="7093a-167">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="7093a-168">Při zadání <xref:System.Linq.Expressions.Expression%601> argumentu je výraz lambda zkompilován do stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="7093a-168">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="7093a-169">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> standardní operátor dotazu:</span><span class="sxs-lookup"><span data-stu-id="7093a-169">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="7093a-170">Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně.</span><span class="sxs-lookup"><span data-stu-id="7093a-170">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="7093a-171">Tento konkrétní výraz lambda počítá tato celá čísla (`n`), která při vydělení dvěma mají zbytek 1.</span><span class="sxs-lookup"><span data-stu-id="7093a-171">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="7093a-172">Následující příklad vytvoří sekvenci, která obsahuje všechny prvky v `numbers` poli, které předcházejí hodnotě 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:</span><span class="sxs-lookup"><span data-stu-id="7093a-172">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="7093a-173">Následující příklad určuje více vstupních parametrů uzavřením do závorek.</span><span class="sxs-lookup"><span data-stu-id="7093a-173">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="7093a-174">Metoda vrátí všechny prvky v `numbers` poli, dokud nenarazí na číslo, jehož hodnota je menší než pořadové místo v poli:</span><span class="sxs-lookup"><span data-stu-id="7093a-174">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="7093a-175">Odvození typu ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="7093a-175">Type inference in lambda expressions</span></span>

<span data-ttu-id="7093a-176">Při psaní výrazů lambda není často nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě těla lambda, typů parametrů a dalších faktorů, jak je popsáno ve specifikaci C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="7093a-176">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="7093a-177">Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="7093a-177">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="7093a-178">Pokud se dotazuje `IEnumerable<Customer>`na, pak vstupní proměnná je odvozena `Customer` jako objekt, což znamená, že máte přístup ke svým metodám a vlastnostem:</span><span class="sxs-lookup"><span data-stu-id="7093a-178">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="7093a-179">Obecná pravidla pro odvození typu pro výrazy lambda jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7093a-179">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="7093a-180">Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="7093a-180">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="7093a-181">Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.</span><span class="sxs-lookup"><span data-stu-id="7093a-181">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="7093a-182">Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="7093a-182">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="7093a-183">Všimněte si, že lambda výrazy samy nemají typ, protože společný typ systému nemá žádný vnitřní koncept výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="7093a-183">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="7093a-184">Někdy je však vhodné mluvit neformálně jako "typ" výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="7093a-184">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="7093a-185">V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ, na který je výraz lambda převeden.</span><span class="sxs-lookup"><span data-stu-id="7093a-185">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="7093a-186">Zachycení vnějších proměnných a rozsahu proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="7093a-186">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="7093a-187">Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](anonymous-methods.md)), které jsou v oboru v metodě definující výraz lambda nebo v rozsahu v typu, který obsahuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="7093a-187">Lambdas can refer to *outer variables* (see [Anonymous methods](anonymous-methods.md)) that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="7093a-188">Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7093a-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="7093a-189">Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="7093a-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="7093a-190">Následující příklad znázorňuje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="7093a-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="7093a-191">Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="7093a-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="7093a-192">Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7093a-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="7093a-193">Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné v nadřazené metodě.</span><span class="sxs-lookup"><span data-stu-id="7093a-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="7093a-194">Výraz lambda nemůže přímo zachytit parametr [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)nebo [out](../../language-reference/keywords/out-parameter-modifier.md) z nadřazené metody.</span><span class="sxs-lookup"><span data-stu-id="7093a-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="7093a-195">Příkaz [return](../../language-reference/keywords/return.md) ve výrazu lambda nezpůsobí vrácení ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="7093a-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="7093a-196">Výraz lambda nemůže obsahovat příkaz [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)nebo [Continue](../../language-reference/keywords/continue.md) , pokud cíl tohoto příkazu skoku je mimo blok výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="7093a-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="7093a-197">Je také možné, že příkaz skoku je mimo blok výrazu lambda, pokud je cíl uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="7093a-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7093a-198">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7093a-198">C# language specification</span></span>

<span data-ttu-id="7093a-199">Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7093a-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="7093a-200">Doporučená kapitola knihy</span><span class="sxs-lookup"><span data-stu-id="7093a-200">Featured book chapter</span></span>

<span data-ttu-id="7093a-201">[Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3,0 kuchařka, třetí vydání: Více než 250 řešení pro C# 3,0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="7093a-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7093a-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7093a-202">See also</span></span>

- [<span data-ttu-id="7093a-203">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7093a-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7093a-204">LINQ (jazykově integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="7093a-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="7093a-205">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="7093a-205">Anonymous Methods</span></span>](anonymous-methods.md)
- [<span data-ttu-id="7093a-206">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="7093a-206">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="7093a-207">Místní funkce ve srovnání s lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="7093a-207">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="7093a-208">Implicitně typované výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="7093a-208">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="7093a-209">Ukázky sady Visual C# Studio 2008 (viz soubory ukázkových dotazů LINQ a program XQuery)</span><span class="sxs-lookup"><span data-stu-id="7093a-209">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="7093a-210">Rekurzivní výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="7093a-210">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
