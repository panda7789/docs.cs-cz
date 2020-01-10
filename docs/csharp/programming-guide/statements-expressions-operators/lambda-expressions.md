---
title: Výrazy lambda – C# Průvodce programováním
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 668bb08526a6eeb1cf640c9ecdac3b8f2c850a99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711945"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="ffa95-102">Výrazy lambda (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ffa95-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="ffa95-103">*Výraz lambda* je výraz kterékoli z následujících dvou forem:</span><span class="sxs-lookup"><span data-stu-id="ffa95-103">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="ffa95-104">[Výraz lambda výrazu](#expression-lambdas) , který má výraz jako tělo:</span><span class="sxs-lookup"><span data-stu-id="ffa95-104">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="ffa95-105">Výraz [lambda](#statement-lambdas) , který má blok příkazu jako jeho tělo:</span><span class="sxs-lookup"><span data-stu-id="ffa95-105">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="ffa95-106">Použijte [operátor deklarace lambda `=>`](../../language-reference/operators/lambda-operator.md) k oddělení seznamu parametrů lambda od jeho těla.</span><span class="sxs-lookup"><span data-stu-id="ffa95-106">Use the [lambda declaration operator `=>`](../../language-reference/operators/lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="ffa95-107">Chcete-li vytvořit výraz lambda, zadejte vstupní parametry (pokud existují) na levé straně operátoru lambda a výraz nebo blok příkazu na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="ffa95-107">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="ffa95-108">Libovolný výraz lambda lze převést na typ [delegáta](../../language-reference/builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="ffa95-108">Any lambda expression can be converted to a [delegate](../../language-reference/builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="ffa95-109">Typ delegáta, na který lze výraz lambda převést, je definován typy jeho parametrů a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ffa95-109">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="ffa95-110">Pokud výraz lambda nevrací hodnotu, může být převeden na jeden z `Action`ch typů delegátů; v opačném případě je možné ji převést na jeden z `Func` typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="ffa95-110">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="ffa95-111">Například lambda výraz, který má dva parametry a nevrací žádnou hodnotu, lze převést na <xref:System.Action%602> delegáta.</span><span class="sxs-lookup"><span data-stu-id="ffa95-111">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="ffa95-112">Lambda výraz, který má jeden parametr a vrací hodnotu, lze převést na <xref:System.Func%602> delegáta.</span><span class="sxs-lookup"><span data-stu-id="ffa95-112">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="ffa95-113">V následujícím příkladu výraz lambda `x => x * x`, který určuje parametr s názvem `x` a vrátí hodnotu `x` na druhou, je přiřazen proměnné typu delegáta:</span><span class="sxs-lookup"><span data-stu-id="ffa95-113">In the following example, the lambda expression `x => x * x`, which specifies a parameter that’s named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="ffa95-114">Lambda výrazy lze také převést na typy [stromu výrazů](../concepts/expression-trees/index.md) , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ffa95-114">Expression lambdas also can be converted to the [expression tree](../concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="ffa95-115">Můžete použít výrazy lambda v jakémkoli kódu, který vyžaduje instance typů delegátů nebo stromů výrazů, například jako argument metody <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> k předání kódu, který by měl být proveden na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ffa95-115">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="ffa95-116">Lambda výrazy můžete použít také při psaní [LINQ in C# ](../../linq/index.md), jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ffa95-116">You also can use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="ffa95-117">Použijete-li syntaxi na základě metody pro volání metody <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> ve třídě <xref:System.Linq.Enumerable?displayProperty=nameWithType>, například v LINQ to Objects a LINQ to XML, je parametrem typ delegáta <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ffa95-117">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ffa95-118">Při volání metody <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> ve třídě <xref:System.Linq.Queryable?displayProperty=nameWithType>, například v LINQ to SQL, je typ parametru typ stromu výrazu [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span><span class="sxs-lookup"><span data-stu-id="ffa95-118">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="ffa95-119">V obou případech můžete použít stejný výraz lambda k zadání hodnoty parametru.</span><span class="sxs-lookup"><span data-stu-id="ffa95-119">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="ffa95-120">To umožňuje, aby dvě `Select` volání vypadaly podobně, i když ve skutečnosti se typ objektů vytvořených z výrazů lambda liší.</span><span class="sxs-lookup"><span data-stu-id="ffa95-120">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="ffa95-121">Výrazy lambda výrazu</span><span class="sxs-lookup"><span data-stu-id="ffa95-121">Expression lambdas</span></span>

<span data-ttu-id="ffa95-122">Výraz lambda s výrazem na pravé straně operátoru `=>` se nazývá *výrazová lambda*.</span><span class="sxs-lookup"><span data-stu-id="ffa95-122">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="ffa95-123">Výrazy lambda výrazů se v konstrukci [stromů výrazů](../concepts/expression-trees/index.md)používají rozsáhle.</span><span class="sxs-lookup"><span data-stu-id="ffa95-123">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="ffa95-124">Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:</span><span class="sxs-lookup"><span data-stu-id="ffa95-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="ffa95-125">Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="ffa95-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="ffa95-126">Zadejte nulové vstupní parametry s prázdnými závorkami:</span><span class="sxs-lookup"><span data-stu-id="ffa95-126">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="ffa95-127">Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:</span><span class="sxs-lookup"><span data-stu-id="ffa95-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="ffa95-128">V některých případech je možné, že kompilátor odvodí vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="ffa95-128">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="ffa95-129">Můžete určit typy explicitně, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ffa95-129">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="ffa95-130">Typy vstupních parametrů musí být všechny explicitní nebo všechny implicitní; v opačném případě dojde k chybě kompilátoru [CS0748](../../misc/cs0748.md) .</span><span class="sxs-lookup"><span data-stu-id="ffa95-130">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="ffa95-131">Tělo výrazu lambda se může skládat z volání metody.</span><span class="sxs-lookup"><span data-stu-id="ffa95-131">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="ffa95-132">Pokud však vytváříte stromy výrazů, které jsou vyhodnocovány mimo kontext modulu CLR (Common Language Runtime) .NET, například v SQL Server, neměli byste používat volání metody ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="ffa95-132">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="ffa95-133">Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ffa95-133">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="ffa95-134">Výrazy lambda příkazů</span><span class="sxs-lookup"><span data-stu-id="ffa95-134">Statement lambdas</span></span>

<span data-ttu-id="ffa95-135">Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:</span><span class="sxs-lookup"><span data-stu-id="ffa95-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="ffa95-136">Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.</span><span class="sxs-lookup"><span data-stu-id="ffa95-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="ffa95-137">Výrazy lambda příkazu nejde použít k vytváření stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="ffa95-137">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="ffa95-138">Asynchronní výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="ffa95-138">Async lambdas</span></span>

<span data-ttu-id="ffa95-139">Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí klíčových slov [Async](../../language-reference/keywords/async.md) a [await](../../language-reference/operators/await.md) .</span><span class="sxs-lookup"><span data-stu-id="ffa95-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/operators/await.md) keywords.</span></span> <span data-ttu-id="ffa95-140">Například následující příklad model Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="ffa95-140">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="ffa95-141">Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy.</span><span class="sxs-lookup"><span data-stu-id="ffa95-141">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="ffa95-142">Chcete-li přidat tuto obslužnou rutinu, přidejte modifikátor `async` před seznam parametrů lambda, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ffa95-142">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="ffa95-143">Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="ffa95-143">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="ffa95-144">Výrazy lambda a řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="ffa95-144">Lambda expressions and tuples</span></span>

<span data-ttu-id="ffa95-145">Od verze C# 7,0 poskytuje C# jazyk integrovanou podporu pro [řazené kolekce členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="ffa95-145">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="ffa95-146">Můžete zadat řazenou kolekci členů jako argument pro lambda výraz a váš výraz lambda může také vrátit řazenou kolekci členů.</span><span class="sxs-lookup"><span data-stu-id="ffa95-146">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="ffa95-147">V některých případech C# kompilátor používá odvození typu k určení typů komponent řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="ffa95-147">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="ffa95-148">Řazenou kolekci členů můžete definovat tak, že v závorkách seřadíte seznam jeho komponent oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="ffa95-148">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="ffa95-149">Následující příklad používá řazené kolekce členů se třemi komponenty k předání sekvence čísel lambda výrazu, který zdvojnásobuje každou hodnotu a vrátí řazenou kolekci členů se třemi komponentami, které obsahují výsledek násobení.</span><span class="sxs-lookup"><span data-stu-id="ffa95-149">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="ffa95-150">Pole řazené kolekce členů jsou obvykle pojmenovány `Item1`, `Item2`atd. Můžete však definovat řazenou kolekci členů s pojmenovanými součástmi, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-150">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="ffa95-151">Další informace o C# řazených kolekcích členů naleznete v tématu [ C# typy řazené kolekce členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="ffa95-151">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="ffa95-152">Výrazy lambda se standardními operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="ffa95-152">Lambdas with the standard query operators</span></span>

<span data-ttu-id="ffa95-153">LINQ to Objects, kromě jiných implementací, mají vstupní parametr, jehož typ je jedna z <xref:System.Func%601> rodina generických delegátů.</span><span class="sxs-lookup"><span data-stu-id="ffa95-153">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="ffa95-154">Tito Delegáti používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="ffa95-154">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="ffa95-155">Delegáti `Func` jsou velmi užitečné pro zapouzdření uživatelsky definovaných výrazů, které jsou aplikovány na každý prvek v sadě zdrojových dat.</span><span class="sxs-lookup"><span data-stu-id="ffa95-155">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="ffa95-156">Zvažte například <xref:System.Func%602> typ delegáta:</span><span class="sxs-lookup"><span data-stu-id="ffa95-156">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="ffa95-157">Delegát může být vytvořen jako instance `Func<int, bool>`, kde `int` je vstupním parametrem a `bool` je návratovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="ffa95-157">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="ffa95-158">Vrácená hodnota je vždy určena v posledním parametru typu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-158">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="ffa95-159">Například `Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry, `int` a `string`a návratový typ `bool`.</span><span class="sxs-lookup"><span data-stu-id="ffa95-159">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="ffa95-160">Následující `Func` delegát po jeho vyvolání vrátí logickou hodnotu, která označuje, zda je vstupní parametr roven pěti:</span><span class="sxs-lookup"><span data-stu-id="ffa95-160">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="ffa95-161">Výraz lambda lze také zadat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například ve standardních operátorech dotazu, které jsou definovány v typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="ffa95-161">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="ffa95-162">Při zadání argumentu <xref:System.Linq.Expressions.Expression%601> je výraz lambda zkompilován do stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-162">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="ffa95-163">Následující příklad používá operátor dotazu <xref:System.Linq.Enumerable.Count%2A> Standard:</span><span class="sxs-lookup"><span data-stu-id="ffa95-163">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="ffa95-164">Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně.</span><span class="sxs-lookup"><span data-stu-id="ffa95-164">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="ffa95-165">Tento konkrétní výraz lambda počítá tato celá čísla (`n`), která při vydělení dvěma mají zbytek 1.</span><span class="sxs-lookup"><span data-stu-id="ffa95-165">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="ffa95-166">Následující příklad vytvoří sekvenci, která obsahuje všechny prvky v poli `numbers`, které předcházejí hodnotě 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:</span><span class="sxs-lookup"><span data-stu-id="ffa95-166">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="ffa95-167">Následující příklad určuje více vstupních parametrů uzavřením do závorek.</span><span class="sxs-lookup"><span data-stu-id="ffa95-167">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="ffa95-168">Metoda vrátí všechny prvky v poli `numbers`, dokud nenalezne číslo, jehož hodnota je menší než pořadové místo v poli:</span><span class="sxs-lookup"><span data-stu-id="ffa95-168">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="ffa95-169">Odvození typu ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="ffa95-169">Type inference in lambda expressions</span></span>

<span data-ttu-id="ffa95-170">Při psaní výrazů lambda není často nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě těla lambda, typů parametrů a dalších faktorů, jak je popsáno ve specifikaci C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="ffa95-170">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="ffa95-171">Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ffa95-171">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="ffa95-172">Pokud se dotazuje na `IEnumerable<Customer>`, vstupní proměnná je odvozená jako `Customer` objekt, což znamená, že máte přístup ke svým metodám a vlastnostem:</span><span class="sxs-lookup"><span data-stu-id="ffa95-172">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="ffa95-173">Obecná pravidla pro odvození typu pro výrazy lambda jsou následující:</span><span class="sxs-lookup"><span data-stu-id="ffa95-173">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="ffa95-174">Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-174">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="ffa95-175">Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-175">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="ffa95-176">Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="ffa95-176">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="ffa95-177">Všimněte si, že lambda výrazy samy nemají typ, protože společný typ systému nemá žádný vnitřní koncept výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="ffa95-177">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="ffa95-178">Někdy je však vhodné mluvit neformálně jako "typ" výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="ffa95-178">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="ffa95-179">V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ, na který je výraz lambda převeden.</span><span class="sxs-lookup"><span data-stu-id="ffa95-179">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="ffa95-180">Zachycení vnějších proměnných a rozsahu proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="ffa95-180">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="ffa95-181">Výrazy lambda mohou odkazovat na *vnější proměnné*.</span><span class="sxs-lookup"><span data-stu-id="ffa95-181">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="ffa95-182">Toto jsou proměnné, které jsou v oboru v metodě definující výraz lambda nebo v rozsahu typu, který obsahuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="ffa95-182">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="ffa95-183">Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ffa95-183">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="ffa95-184">Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="ffa95-184">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="ffa95-185">Následující příklad znázorňuje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="ffa95-185">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="ffa95-186">Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="ffa95-186">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="ffa95-187">Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ffa95-187">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="ffa95-188">Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné v nadřazené metodě.</span><span class="sxs-lookup"><span data-stu-id="ffa95-188">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="ffa95-189">Výraz lambda nemůže přímo zachytit parametr [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)nebo [out](../../language-reference/keywords/out-parameter-modifier.md) z nadřazené metody.</span><span class="sxs-lookup"><span data-stu-id="ffa95-189">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="ffa95-190">Příkaz [return](../../language-reference/keywords/return.md) ve výrazu lambda nezpůsobí vrácení ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="ffa95-190">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="ffa95-191">Výraz lambda nemůže obsahovat příkaz [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)nebo [Continue](../../language-reference/keywords/continue.md) , pokud cíl tohoto příkazu skoku je mimo blok výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="ffa95-191">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="ffa95-192">Je také možné, že příkaz skoku je mimo blok výrazu lambda, pokud je cíl uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="ffa95-192">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ffa95-193">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ffa95-193">C# language specification</span></span>

<span data-ttu-id="ffa95-194">Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ffa95-194">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="ffa95-195">Doporučená kapitola knihy</span><span class="sxs-lookup"><span data-stu-id="ffa95-195">Featured book chapter</span></span>

<span data-ttu-id="ffa95-196">[Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3,0 kuchařka, třetí vydání: více než 250 řešení pro C# 3,0 programátorů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="ffa95-196">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa95-197">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffa95-197">See also</span></span>

- [<span data-ttu-id="ffa95-198">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ffa95-198">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ffa95-199">LINQ (jazykově integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="ffa95-199">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="ffa95-200">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="ffa95-200">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="ffa95-201">Místní funkce ve srovnání s lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="ffa95-201">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="ffa95-202">Implicitně typované výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="ffa95-202">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="ffa95-203">Ukázky sady Visual C# Studio 2008 (viz soubory ukázkových dotazů LINQ a program XQuery)</span><span class="sxs-lookup"><span data-stu-id="ffa95-203">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="ffa95-204">Rekurzivní výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="ffa95-204">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
