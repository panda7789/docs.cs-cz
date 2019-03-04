---
title: Lambda – výrazy
description: Další použití lambda výrazů, které jsou bloky spustitelného kódu, které mohou být předány jako argumenty.
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 642422a4cc077ffebb5ee6db9d7ffb937fc1e173
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212349"
---
# <a name="lambda-expressions"></a><span data-ttu-id="3ffe0-103">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="3ffe0-103">Lambda expressions</span></span>

<span data-ttu-id="3ffe0-104">A *výraz lambda* je blok kódu (výraz nebo blok příkazů, který), který je zpracováván jako objekt.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-104">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="3ffe0-105">Může být předán jako argument metody, a to může být vrácen voláním metody.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-105">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="3ffe0-106">Výrazy lambda jsou často používány pro:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-106">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="3ffe0-107">Předejte kód, který má být proveden na asynchronní metody, jako je <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-107">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span></span>

- <span data-ttu-id="3ffe0-108">Zápis [LINQ – výrazy dotazů](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ffe0-108">Writing [LINQ query expressions](linq/index.md).</span></span>

- <span data-ttu-id="3ffe0-109">Vytváření [stromů výrazů](expression-trees-building.md).</span><span class="sxs-lookup"><span data-stu-id="3ffe0-109">Creating [expression trees](expression-trees-building.md).</span></span>

<span data-ttu-id="3ffe0-110">Použití výrazů lambda je kód, který může být reprezentována jako delegát nebo jako strom výrazů, který se zkompiluje do delegáta.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-110">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="3ffe0-111">Na typ delegáta konkrétní výraz lambda závisí na jeho parametry a vracet hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-111">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="3ffe0-112">Výrazy lambda, které nevracejí hodnotu odpovídají konkrétní `Action` delegovat, v závislosti na jeho počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-112">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="3ffe0-113">Lambda výrazy, které vracejí hodnotu odpovídají konkrétní `Func` delegovat, v závislosti na jeho počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-113">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="3ffe0-114">Například výraz lambda, který má dva parametry, ale nevrací žádnou hodnotu odpovídá <xref:System.Action%602> delegovat.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-114">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="3ffe0-115">Výraz lambda, který má jeden parametr a vrátí hodnotu odpovídá <xref:System.Func%602> delegovat.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-115">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="3ffe0-116">Používá výraz lambda `=>`, [deklarace operátoru lambda](language-reference/operators/lambda-operator.md), seznam parametrů lambda pro oddělení od jeho spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-116">A lambda expression uses `=>`, the [lambda declaration operator](language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="3ffe0-117">Pokud chcete vytvořit výraz lambda, zadejte vstupní parametry (pokud existuje) na levé straně operátoru lambda a umístěte blok výrazu nebo příkazu na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-117">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="3ffe0-118">Například výraz lambda jednořádkového `x => x * x` určuje parametr s názvem `x` a vrátí hodnotu `x` ve čtverci.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-118">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="3ffe0-119">Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-119">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

<span data-ttu-id="3ffe0-120">Nebo jej lze předat přímo jako argument metody:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a><span data-ttu-id="3ffe0-121">Výrazové lambdy</span><span class="sxs-lookup"><span data-stu-id="3ffe0-121">Expression lambdas</span></span>

 <span data-ttu-id="3ffe0-122">Výraz lambda s výrazem na pravé straně = > – operátor je volána *výrazu lambda*.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-122">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="3ffe0-123">Výrazové lambdy se často používají v konstrukci [stromů výrazů](expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="3ffe0-123">Expression lambdas are used extensively in the construction of [expression trees](expression-trees.md).</span></span> <span data-ttu-id="3ffe0-124">Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input parameters) => expression
```

<span data-ttu-id="3ffe0-125">Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="3ffe0-126">Zadejte nulové vstupní parametry s prázdnými závorkami:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-126">Specify zero input parameters with empty parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

<span data-ttu-id="3ffe0-127">Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

<span data-ttu-id="3ffe0-128">Kompilátor používá obvykle odvození typu při určování typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-128">Ordinarily, the compiler uses type inference in determining parameter types.</span></span> <span data-ttu-id="3ffe0-129">Někdy je však obtížné či nemožné odvodit vstupní typy kompilátor.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-129">However, sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="3ffe0-130">Pokud k tomu dojde, můžete určit typy explicitně, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-130">When this occurs, you can specify the types explicitly, as in the following example:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

<span data-ttu-id="3ffe0-131">V předchozím příkladu si všimněte, že hlavní část výrazové lambdy může být tvořena voláním metody.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-131">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="3ffe0-132">Ale pokud vytváříte stromy výrazů, které jsou vyhodnocovány mimo rozhraní .NET Framework, například systému SQL Server nebo Entity Framework (EF), můžete neměly by pomocí volání metody v lambda výrazech, protože může metody nemají význam mimo kontext implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-132">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server or Entity Framework (EF), you should refrain from using method calls in lambda expressions, since the methods may have no meaning outside the context of the .NET implementation.</span></span> <span data-ttu-id="3ffe0-133">Pokud budete chtít v tomto případě používat volání metody, nezapomeňte otestovat jejich důkladně a zkontrolujte, že metoda, kterou lze úspěšně vyřešit volání.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-133">If you do choose to use method calls in this case, be sure to test them thoroughly to ensure that the method calls can be successfully resolved.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="3ffe0-134">Příkazové lambdy</span><span class="sxs-lookup"><span data-stu-id="3ffe0-134">Statement lambdas</span></span>

<span data-ttu-id="3ffe0-135">Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp
(input parameters) => { statement; }
```

<span data-ttu-id="3ffe0-136">Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

<span data-ttu-id="3ffe0-137">Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-137">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="3ffe0-138">Asynchronní lambdy</span><span class="sxs-lookup"><span data-stu-id="3ffe0-138">Async lambdas</span></span>

<span data-ttu-id="3ffe0-139">Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](language-reference/keywords/async.md) a [await](language-reference/keywords/await.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](language-reference/keywords/async.md) and [await](language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="3ffe0-140">Například v příkladu volá `ShowSquares` metodu, která se spustí asynchronně.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-140">For example, the example calls a `ShowSquares` method that executes asynchronously.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

<span data-ttu-id="3ffe0-141">Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ffe0-141">For more information about how to create and use async methods, see [Asynchronous programming with async and await](programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="3ffe0-142">Výrazy lambda a řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="3ffe0-142">Lambda expressions and tuples</span></span>

<span data-ttu-id="3ffe0-143">Od verze C# 7.0, jazyk C# obsahuje integrovanou podporu pro řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-143">Starting with C# 7.0, the C# language provides built-in support for tuples.</span></span> <span data-ttu-id="3ffe0-144">Řazená kolekce členů můžete zadat jako argument výraz lambda, a výraz lambda může také vrátit řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-144">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="3ffe0-145">V některých případech kompilátor jazyka C# používá odvození typu k určení typů součásti řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-145">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="3ffe0-146">Můžete definovat řazené kolekce členů uzavřením čárkami oddělený seznam svých komponent do závorek.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-146">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="3ffe0-147">Následující příklad používá řazené kolekce členů s 5 součásti předat výraz lambda, zdvojnásobí každou hodnotu, která vrací řazenou kolekci členů s 5 komponenty, který obsahuje výsledek součinů sekvenci čísel.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-147">The following example uses tuple with 5 components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with 5 components that contains the result of the multiplications.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

<span data-ttu-id="3ffe0-148">Obvykle jsou pojmenované pole řazená kolekce členů `Item1`, `Item2`atd. Řazená kolekce členů s s názvem komponenty, můžete definovat, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-148">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

<span data-ttu-id="3ffe0-149">Další informace o podpoře pro řazené kolekce členů v C# najdete v tématu [typy řazené kolekce členů jazyka C#](tuples.md).</span><span class="sxs-lookup"><span data-stu-id="3ffe0-149">For more information on support for tuples in C#, see [C# Tuple types](tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="3ffe0-150">Výrazy lambda s operátory standardního dotazu</span><span class="sxs-lookup"><span data-stu-id="3ffe0-150">Lambdas with the standard query operators</span></span>

<span data-ttu-id="3ffe0-151">LINQ na objekty v jiných implementacích má vstupní parametr, jehož typ je jednou z <xref:System.Func%601> řady obecných delegátů.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-151">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="3ffe0-152">Tyto delegáty používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-152">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="3ffe0-153">`Func` Delegáti jsou velmi užiteční pro zapouzdření výrazů definovaných uživatelem, které jsou použity pro každý prvek v sadě zdrojových dat.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-153">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="3ffe0-154">Představme si třeba, <xref:System.Func%601> delegáta, jehož syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-154">For example, consider the <xref:System.Func%601> delegate, whose syntax is:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

<span data-ttu-id="3ffe0-155">Delegát může být vytvořena s kód podobný tomuto</span><span class="sxs-lookup"><span data-stu-id="3ffe0-155">The delegate can be instantiated with code like the following</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

<span data-ttu-id="3ffe0-156">kde `int` je vstupní parametr a `bool` je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-156">where `int` is an input parameter, and `bool` is the return value.</span></span> <span data-ttu-id="3ffe0-157">Vrácená hodnota je vždy určena v posledním parametru typu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-157">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="3ffe0-158">Když následující `Func` je vyvolán delegát, vrátí hodnotu true nebo false označuje, zda je vstupní parametr roven hodnotě 5:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-158">When the following `Func` delegate is invoked, it returns true or false to indicate whether the input parameter is equal to 5:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

<span data-ttu-id="3ffe0-159">Výraz lambda lze také zadat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například ve standardních operátorech dotazu, které jsou definovány v <xref:System.Linq.Queryable> typu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-159">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="3ffe0-160">Pokud zadáte <xref:System.Linq.Expressions.Expression%601> je argument, výraz lambda kompilována na strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-160">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span> <span data-ttu-id="3ffe0-161">V následujícím příkladu [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standardní operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-161">The following example uses the [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standard query operator.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

<span data-ttu-id="3ffe0-162">Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-162">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="3ffe0-163">Tento konkrétní výraz lambda vrátí ta celá čísla (`n`), která po vydělení dvěma, mají zbytek 1.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-163">This particular lambda expression counts those integers (`n`) that, when divided by two, have a remainder of 1.</span></span>

<span data-ttu-id="3ffe0-164">Následující příklad vytvoří posloupnost, která obsahuje všechny prvky `numbers` pole, které před 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-164">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

<span data-ttu-id="3ffe0-165">Následující příklad určuje většího počtu vstupních parametrů uzavřením do závorek.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-165">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="3ffe0-166">Metoda vrátí všechny prvky v poli čísel, dokud nenarazí na číslo, jehož hodnota je menší než její pořadové umístění v poli.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-166">The method returns all the elements in the numbers array until it encounters a number whose value is less than its ordinal position in the array.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="3ffe0-167">Odvození typu proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="3ffe0-167">Type inference in lambda expressions</span></span>

<span data-ttu-id="3ffe0-168">Při psaní výrazů lambda, často není nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě hlavní část výrazu lambda, typy parametrů a dalších faktorů, jak je popsáno ve specifikaci jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-168">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors, as described in the C# Language Specification.</span></span> <span data-ttu-id="3ffe0-169">Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-169">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="3ffe0-170">Pokud se dotazuje `IEnumerable<Customer>`, pak je vstupní proměnná odvozena jako `Customer` objekt, což znamená, že máte přístup k jejím metodám a vlastnostem:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-170">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

<span data-ttu-id="3ffe0-171">Obecná pravidla pro odvození typu proměnné pro výrazy lambda jsou:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-171">The general rules for type inference for lambdas are:</span></span>

- <span data-ttu-id="3ffe0-172">Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-172">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="3ffe0-173">Každá vstupní argument ve výrazu lambda musí být implicitně převeditelný na odpovídající parametr delegátu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-173">Each input argument in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="3ffe0-174">Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-174">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>

<span data-ttu-id="3ffe0-175">Výrazy lambda nemají vlastní určený typ, protože systém běžných typů nezná vnitřní pojem „výraz lambda“.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-175">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="3ffe0-176">Někdy je však vhodné hovořit neformálně o „typu“ výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-176">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="3ffe0-177">V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ na který je převeden výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-177">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="3ffe0-178">Rozsah proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="3ffe0-178">Variable Scope in Lambda Expressions</span></span>

<span data-ttu-id="3ffe0-179">Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](programming-guide/statements-expressions-operators/anonymous-methods.md)), které jsou v oboru v metodě, která definuje funkci lambda, nebo v rozsahu typu, který obsahuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-179">Lambdas can refer to *outer variables* (see [Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="3ffe0-180">Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-180">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="3ffe0-181">Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-181">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="3ffe0-182">Následující příklad znázorňuje tato pravidla.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-182">The following example demonstrates these rules.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 <span data-ttu-id="3ffe0-183">Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-183">The following rules apply to variable scope in lambda expressions:</span></span>

- <span data-ttu-id="3ffe0-184">Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-184">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="3ffe0-185">Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné ve vnější metodě.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-185">Variables introduced within a lambda expression are not visible in the outer method.</span></span>

- <span data-ttu-id="3ffe0-186">Výraz lambda nemůže přímo zachytit `in`, `ref`, nebo `out` parametr z ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-186">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>

- <span data-ttu-id="3ffe0-187">Příkaz return ve výrazu lambda nezpůsobí vrácení ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-187">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>

- <span data-ttu-id="3ffe0-188">Výraz lambda nemůže obsahovat `goto` příkazu `break` příkazu, nebo `continue` příkaz, který se nachází uvnitř funkce lambda, pokud cíl příkazu skoku je mimo blok.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-188">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="3ffe0-189">Je také chybou mít příkaz skoku mimo blok funkce lambda, pokud je cíl uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="3ffe0-189">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ffe0-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ffe0-190">See also</span></span>

- [<span data-ttu-id="3ffe0-191">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="3ffe0-191">LINQ (Language-Integrated Query)</span></span>](../standard/using-linq.md)
- [<span data-ttu-id="3ffe0-192">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="3ffe0-192">Anonymous methods</span></span>](programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="3ffe0-193">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="3ffe0-193">Expression trees</span></span>](expression-trees.md)
