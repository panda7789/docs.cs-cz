---
title: Výrazy lambda - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: dd9b77a90030a96d17104c8c0e48964b6a85d165
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125730"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="2abd6-102">Výrazy lambda (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="2abd6-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="2abd6-103">A *výraz lambda* je blok kódu (výraz nebo blok příkazů, který), který je zpracováván jako objekt.</span><span class="sxs-lookup"><span data-stu-id="2abd6-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="2abd6-104">Může být předán jako argument metody, a to může být vrácen voláním metody.</span><span class="sxs-lookup"><span data-stu-id="2abd6-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="2abd6-105">Výrazy lambda jsou často používány pro:</span><span class="sxs-lookup"><span data-stu-id="2abd6-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="2abd6-106">Předejte kód, který má být proveden na asynchronní metody, jako je <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2abd6-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="2abd6-107">Zápis [LINQ – výrazy dotazů](../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="2abd6-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="2abd6-108">Vytváření [stromů výrazů](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="2abd6-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="2abd6-109">Použití výrazů lambda je kód, který může být reprezentována jako delegát nebo jako strom výrazů, který se zkompiluje do delegáta.</span><span class="sxs-lookup"><span data-stu-id="2abd6-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="2abd6-110">Na typ delegáta konkrétní výraz lambda závisí na jeho parametry a vracet hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="2abd6-111">Výrazy lambda, které nevracejí hodnotu odpovídají konkrétní `Action` delegovat, v závislosti na jeho počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="2abd6-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="2abd6-112">Lambda výrazy, které vracejí hodnotu odpovídají konkrétní `Func` delegovat, v závislosti na jeho počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="2abd6-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="2abd6-113">Například výraz lambda, který má dva parametry, ale nevrací žádnou hodnotu odpovídá <xref:System.Action%602> delegovat.</span><span class="sxs-lookup"><span data-stu-id="2abd6-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="2abd6-114">Výraz lambda, který má jeden parametr a vrátí hodnotu odpovídá <xref:System.Func%602> delegovat.</span><span class="sxs-lookup"><span data-stu-id="2abd6-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="2abd6-115">Používá výraz lambda `=>`, [deklarace operátoru lambda](../../language-reference/operators/lambda-operator.md), seznam parametrů lambda pro oddělení od jeho spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="2abd6-116">Pokud chcete vytvořit výraz lambda, zadejte vstupní parametry (pokud existuje) na levé straně operátoru lambda a umístěte blok výrazu nebo příkazu na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="2abd6-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="2abd6-117">Například výraz lambda jednořádkového `x => x * x` určuje parametr s názvem `x` a vrátí hodnotu `x` ve čtverci.</span><span class="sxs-lookup"><span data-stu-id="2abd6-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="2abd6-118">Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2abd6-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="2abd6-119">Výraz lambda také můžete přiřadit k typu stromu výrazu:</span><span class="sxs-lookup"><span data-stu-id="2abd6-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="2abd6-120">Nebo jej lze předat přímo jako argument metody:</span><span class="sxs-lookup"><span data-stu-id="2abd6-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="2abd6-121">Při použití syntaxe založených na volání metody na volání <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> metodu <xref:System.Linq.Enumerable?displayProperty=nameWithType> třídy (stejně jako v LINQ na objekty a LINQ to XML) je parametr typu delegáta <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2abd6-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2abd6-122">Výraz lambda je nejvhodnějším způsobem vytvoření tohoto delegátu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="2abd6-123">Při volání <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metoda ve <xref:System.Linq.Queryable?displayProperty=nameWithType> třídy (stejně jako v technologii LINQ to SQL) je typ parametru typu stromu výrazu [ `Expression<Func<TSource,TResult>>` ](<xref:System.Linq.Expressions.Expression%601>).</span><span class="sxs-lookup"><span data-stu-id="2abd6-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="2abd6-124">Výraz lambda je opět pouze velmi stručným způsobem vytvoření tohoto stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="2abd6-125">Výrazy lambda umožňují `Select` volání vypadalo podobně, i když ve skutečnosti typ objektu vytvořeného z výrazu lambda jiný.</span><span class="sxs-lookup"><span data-stu-id="2abd6-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>

<span data-ttu-id="2abd6-126">Všechna omezení, které se vztahují [anonymní metody](anonymous-methods.md) platí také pro výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="2abd6-126">All restrictions that apply to [anonymous methods](anonymous-methods.md) also apply to lambda expressions.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="2abd6-127">Výrazové lambdy</span><span class="sxs-lookup"><span data-stu-id="2abd6-127">Expression lambdas</span></span>

<span data-ttu-id="2abd6-128">Výraz lambda s výrazem na pravé straně `=>` operátor je volána *výrazu lambda*.</span><span class="sxs-lookup"><span data-stu-id="2abd6-128">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="2abd6-129">Výrazové lambdy se často používají v konstrukci [stromů výrazů](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="2abd6-129">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="2abd6-130">Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:</span><span class="sxs-lookup"><span data-stu-id="2abd6-130">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="2abd6-131">Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="2abd6-131">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="2abd6-132">Zadejte nulové vstupní parametry s prázdnými závorkami:</span><span class="sxs-lookup"><span data-stu-id="2abd6-132">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="2abd6-133">Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:</span><span class="sxs-lookup"><span data-stu-id="2abd6-133">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="2abd6-134">Někdy je pro kompilátor odvodit vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="2abd6-134">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="2abd6-135">Můžete určit typy explicitně, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2abd6-135">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="2abd6-136">Vstupní parametr typy musí být všechny explicitní, nebo všechny implicitní; v opačném případě [CS0748](../../misc/cs0748.md) dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2abd6-136">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="2abd6-137">Tělo výrazu lambda se může skládat z volání metody.</span><span class="sxs-lookup"><span data-stu-id="2abd6-137">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="2abd6-138">Ale pokud vytváříte stromy výrazů, které jsou vyhodnocovány mimo kontext .NET common language runtime, například v systému SQL Server, byste neměli používat volání metody ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="2abd6-138">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="2abd6-139">Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2abd6-139">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="2abd6-140">Příkazové lambdy</span><span class="sxs-lookup"><span data-stu-id="2abd6-140">Statement lambdas</span></span>

<span data-ttu-id="2abd6-141">Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:</span><span class="sxs-lookup"><span data-stu-id="2abd6-141">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="2abd6-142">Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.</span><span class="sxs-lookup"><span data-stu-id="2abd6-142">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="2abd6-143">Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-143">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="2abd6-144">Asynchronní lambdy</span><span class="sxs-lookup"><span data-stu-id="2abd6-144">Async lambdas</span></span>

<span data-ttu-id="2abd6-145">Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../language-reference/keywords/async.md) a [await](../../language-reference/keywords/await.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="2abd6-145">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="2abd6-146">Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="2abd6-146">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="2abd6-147">Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy.</span><span class="sxs-lookup"><span data-stu-id="2abd6-147">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="2abd6-148">Chcete-li přidat tuto obslužnou rutinu, přidejte `async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2abd6-148">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="2abd6-149">Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="2abd6-149">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="2abd6-150">Výrazy lambda a řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="2abd6-150">Lambda expressions and tuples</span></span>

<span data-ttu-id="2abd6-151">Počínaje C# 7.0, C# jazyk poskytuje integrovanou podporu pro [řazených kolekcí členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="2abd6-151">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="2abd6-152">Řazená kolekce členů můžete zadat jako argument výraz lambda, a výraz lambda může také vrátit řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="2abd6-152">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="2abd6-153">V některých případech kompilátor jazyka C# používá odvození typu k určení typů součásti řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="2abd6-153">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="2abd6-154">Můžete definovat řazené kolekce členů uzavřením čárkami oddělený seznam svých komponent do závorek.</span><span class="sxs-lookup"><span data-stu-id="2abd6-154">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="2abd6-155">Následující příklad používá řazené kolekce členů s tři komponenty předat výraz lambda, zdvojnásobí každou hodnotu, která vrací řazenou kolekci členů s tři komponenty, který obsahuje výsledek součinů sekvenci čísel.</span><span class="sxs-lookup"><span data-stu-id="2abd6-155">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="2abd6-156">Obvykle jsou pojmenované pole řazená kolekce členů `Item1`, `Item2`atd. Řazená kolekce členů s s názvem komponenty, můžete definovat, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-156">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="2abd6-157">Další informace o C# řazených kolekcí členů, naleznete v tématu [ C# typy řazené kolekce členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="2abd6-157">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="2abd6-158">Výrazy lambda s operátory standardního dotazu</span><span class="sxs-lookup"><span data-stu-id="2abd6-158">Lambdas with the standard query operators</span></span>

<span data-ttu-id="2abd6-159">LINQ na objekty v jiných implementacích má vstupní parametr, jehož typ je jednou z <xref:System.Func%601> řady obecných delegátů.</span><span class="sxs-lookup"><span data-stu-id="2abd6-159">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="2abd6-160">Tyto delegáty používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="2abd6-160">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="2abd6-161">`Func` Delegáti jsou velmi užiteční pro zapouzdření výrazů definovaných uživatelem, které jsou použity pro každý prvek v sadě zdrojových dat.</span><span class="sxs-lookup"><span data-stu-id="2abd6-161">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="2abd6-162">Představme si třeba, <xref:System.Func%602> typ delegáta:</span><span class="sxs-lookup"><span data-stu-id="2abd6-162">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="2abd6-163">Delegát může být vytvořen jako `Func<int, bool>` instance where `int` je vstupní parametr a `bool` je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="2abd6-163">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="2abd6-164">Vrácená hodnota je vždy určena v posledním parametru typu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-164">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="2abd6-165">Například `Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry, `int` a `string`a návratový typ `bool`.</span><span class="sxs-lookup"><span data-stu-id="2abd6-165">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="2abd6-166">Následující `Func` delegáta, při jejím vyvolání a vrátí logickou hodnotu označující, zda je vstupní parametr roven pěti:</span><span class="sxs-lookup"><span data-stu-id="2abd6-166">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="2abd6-167">Výraz lambda lze také zadat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například ve standardních operátorech dotazu, které jsou definovány v <xref:System.Linq.Queryable> typu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-167">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="2abd6-168">Pokud zadáte <xref:System.Linq.Expressions.Expression%601> je argument, výraz lambda kompilována na strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-168">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="2abd6-169">V následujícím příkladu <xref:System.Linq.Enumerable.Count%2A> standardní operátor dotazu:</span><span class="sxs-lookup"><span data-stu-id="2abd6-169">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="2abd6-170">Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně.</span><span class="sxs-lookup"><span data-stu-id="2abd6-170">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="2abd6-171">Tento konkrétní výraz lambda vrátí ta celá čísla (`n`) která po vydělení dvěma mají zbytek 1.</span><span class="sxs-lookup"><span data-stu-id="2abd6-171">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="2abd6-172">Následující příklad vytvoří posloupnost, která obsahuje všechny prvky `numbers` pole, které před 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:</span><span class="sxs-lookup"><span data-stu-id="2abd6-172">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="2abd6-173">Následující příklad určuje většího počtu vstupních parametrů uzavřením do závorek.</span><span class="sxs-lookup"><span data-stu-id="2abd6-173">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="2abd6-174">Metoda vrátí všechny prvky `numbers` pole, dokud nenarazí na číslo, jehož hodnota je menší než její pořadové umístění v poli:</span><span class="sxs-lookup"><span data-stu-id="2abd6-174">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="2abd6-175">Odvození typu proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="2abd6-175">Type inference in lambda expressions</span></span>

<span data-ttu-id="2abd6-176">Při psaní výrazů lambda, často není nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě hlavní část výrazu lambda, typy parametrů a dalších faktorů, jak je popsáno v C# specifikace jazyka.</span><span class="sxs-lookup"><span data-stu-id="2abd6-176">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="2abd6-177">Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="2abd6-177">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="2abd6-178">Pokud se dotazuje `IEnumerable<Customer>`, pak je vstupní proměnná odvozena jako `Customer` objekt, což znamená, že máte přístup k jejím metodám a vlastnostem:</span><span class="sxs-lookup"><span data-stu-id="2abd6-178">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="2abd6-179">Obecná pravidla pro odvození typu proměnné pro výrazy lambda jsou následující:</span><span class="sxs-lookup"><span data-stu-id="2abd6-179">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="2abd6-180">Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-180">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="2abd6-181">Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-181">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="2abd6-182">Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="2abd6-182">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="2abd6-183">Všimněte si, že výrazy lambda nemají typ, protože má obecný systém typů nezná vnitřní pojem "výraz lambda".</span><span class="sxs-lookup"><span data-stu-id="2abd6-183">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="2abd6-184">Někdy je však vhodné hovořit neformálně o "typu" výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="2abd6-184">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="2abd6-185">V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ na který je převeden výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="2abd6-185">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="2abd6-186">Rozsah proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="2abd6-186">Variable scope in lambda expressions</span></span>

<span data-ttu-id="2abd6-187">Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](anonymous-methods.md)), které jsou v oboru v metodě, která definuje výraz lambda nebo v rozsahu typu, který obsahuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="2abd6-187">Lambdas can refer to *outer variables* (see [Anonymous methods](anonymous-methods.md)) that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="2abd6-188">Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2abd6-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="2abd6-189">Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="2abd6-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="2abd6-190">Následující příklad znázorňuje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="2abd6-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="2abd6-191">Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="2abd6-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="2abd6-192">Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2abd6-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="2abd6-193">Proměnné, které jsou představeny v rámci výrazu lambda nejsou viditelné v ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="2abd6-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="2abd6-194">Výraz lambda nemůže přímo zachytit [v](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), nebo [si](../../language-reference/keywords/out-parameter-modifier.md) parametr z ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="2abd6-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="2abd6-195">A [vrátit](../../language-reference/keywords/return.md) příkaz ve výrazu lambda nezpůsobí vrácení ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="2abd6-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="2abd6-196">Výraz lambda nemůže obsahovat [goto](../../language-reference/keywords/goto.md), [přerušení](../../language-reference/keywords/break.md), nebo [pokračovat](../../language-reference/keywords/continue.md) příkaz, pokud cíl, který příkaz skoku je mimo blok výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="2abd6-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="2abd6-197">Je také chybou mít příkaz skoku mimo blok výrazu lambda, pokud je cíl uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="2abd6-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2abd6-198">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2abd6-198">C# language specification</span></span>

<span data-ttu-id="2abd6-199">Další informace najdete v tématu [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2abd6-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="2abd6-200">Doporučená kapitola knihy</span><span class="sxs-lookup"><span data-stu-id="2abd6-200">Featured book chapter</span></span>

<span data-ttu-id="2abd6-201">[Delegáty, události a výrazy Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3.0 Cookbook, Third Edition: Víc než 250 řešení pro C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="2abd6-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abd6-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2abd6-202">See also</span></span>

- [<span data-ttu-id="2abd6-203">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2abd6-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2abd6-204">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="2abd6-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="2abd6-205">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="2abd6-205">Anonymous Methods</span></span>](anonymous-methods.md)
- [<span data-ttu-id="2abd6-206">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="2abd6-206">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="2abd6-207">Lokální funkce ve srovnání s výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="2abd6-207">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="2abd6-208">Implicitně typovaná lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="2abd6-208">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="2abd6-209">Visual Studio 2008 C# – ukázky (viz ukázkové soubory dotazů LINQ a XQuery program)</span><span class="sxs-lookup"><span data-stu-id="2abd6-209">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="2abd6-210">Rekurzivní výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="2abd6-210">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
