---
title: "Výrazy lambda"
description: "Principy štíhlého vývoje pro použití výrazů lambda, které jsou bloky spustitelného kódu, které lze předat jako argumenty."
keywords: "Rozhraní .NET, .NET core, výrazů lambda, lambdas, delegáti"
ms-author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 1a97d830c675c8e3980eddae78f3face279ec6dc
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="lambda-expressions"></a><span data-ttu-id="1a6ef-104">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="1a6ef-104">Lambda expressions</span></span> #

<span data-ttu-id="1a6ef-105">A *výrazu lambda* je blok kódu (výraz nebo příkaz blok), který je považován za objekt.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-105">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="1a6ef-106">Mohla být předána jako argument pro metody a může vracet také pomocí volání metody.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-106">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="1a6ef-107">Lambda – výrazy jsou používány pro:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-107">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="1a6ef-108">Předávání kód, který se má provádět na asynchronní metody, jako například <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-108">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span></span>

- <span data-ttu-id="1a6ef-109">Zápis [LINQ – výrazy dotazů](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="1a6ef-109">Writing [LINQ query expressions](linq/index.md).</span></span>

- <span data-ttu-id="1a6ef-110">Vytváření [stromů výrazů](expression-trees-building.md).</span><span class="sxs-lookup"><span data-stu-id="1a6ef-110">Creating [expression trees](expression-trees-building.md).</span></span>

<span data-ttu-id="1a6ef-111">Lambda – výrazy jsou kód, který může být reprezentován jako delegáta, nebo jako strom výrazu kompilovaný s delegátem.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-111">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="1a6ef-112">Delegát konkrétní typ výrazu lambda závisí na jeho parametry a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-112">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="1a6ef-113">Výrazy lambda, které nevrací hodnotu odpovídají na konkrétní `Action` delegovat, v závislosti na jeho počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-113">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="1a6ef-114">Výrazy lambda, která vrátí hodnotu odpovídají na konkrétní `Func` delegovat, v závislosti na jeho počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-114">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="1a6ef-115">Například odpovídá výrazu lambda, která má dva parametry, ale nevrací žádnou hodnotu <xref:System.Action%602> delegovat.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-115">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="1a6ef-116">Výraz lambda, který má jeden parametr a vrátí hodnotu odpovídá <xref:System.Func%602> delegovat.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-116">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="1a6ef-117">Výraz lambda používá `=>`, [lambda deklarace operátor](language-reference/operators/lambda-operator.md), oddělte lambda seznam parametrů z jeho spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-117">A lambda expression uses `=>`, the [lambda declaration operator](language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="1a6ef-118">K vytvoření výrazu lambda, zadáte vstupních parametrů (pokud existuje) na levé straně operátoru lambda, a umístí výraz nebo příkaz bloku na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-118">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="1a6ef-119">Například výrazu lambda jeden řádek `x => x * x` určuje parametr, který je pojmenován `x` a vrátí hodnotu `x` kvadratických.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-119">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="1a6ef-120">Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-120">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

<span data-ttu-id="1a6ef-121">Nebo můžete předat přímo jako argument metody:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-121">Or you can pass it directly as a method argument:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a><span data-ttu-id="1a6ef-122">Lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="1a6ef-122">Expression lambdas</span></span> ##

 <span data-ttu-id="1a6ef-123">Výraz lambda s výrazu na pravé straně = > operátor je volána *výrazu lambda*.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-123">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="1a6ef-124">Lambda výrazy jsou používány při sestavování [stromů výrazů](expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="1a6ef-124">Expression lambdas are used extensively in the construction of [expression trees](expression-trees.md).</span></span> <span data-ttu-id="1a6ef-125">Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-125">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input parameters) => expression
```

<span data-ttu-id="1a6ef-126">Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-126">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="1a6ef-127">Zadejte nulové vstupní parametry s prázdnými závorkami:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-127">Specify zero input parameters with empty parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

<span data-ttu-id="1a6ef-128">Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

<span data-ttu-id="1a6ef-129">Normálně kompilátor použije odvození typu při určování typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-129">Ordinarily, the compiler uses type inference in determining parameter types.</span></span> <span data-ttu-id="1a6ef-130">V některých případech je však obtížné nebo dokonce znemožňují kompilátor pro odvození vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-130">However, sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="1a6ef-131">V takovém případě můžete určit typy explicitně, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-131">When this occurs, you can specify the types explicitly, as in the following example:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

<span data-ttu-id="1a6ef-132">V předchozím příkladu si všimněte, že hlavní část výrazové lambdy může být tvořena voláním metody.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="1a6ef-133">Ale při vytváření stromů výrazů, které se vyhodnocují mimo rozhraní .NET Framework, jako třeba v systému SQL Server nebo Entity Framework (EF), můžete neměly by pomocí volání metody v výrazy lambda, protože metody může mít žádný význam mimo kontext implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server or Entity Framework (EF), you should refrain from using method calls in lambda expressions, since the methods may have no meaning outside the context of the .NET implementation.</span></span> <span data-ttu-id="1a6ef-134">Pokud vyberete v takovém případě použijte volání metod, nezapomeňte otestovat důkladně lze zajistit, aby se můžete úspěšně vyřešit volání metody.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-134">If you do choose to use method calls in this case, be sure to test them thoroughly to ensure that the method calls can be successfuly resolved.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="1a6ef-135">Lambdas – příkaz</span><span class="sxs-lookup"><span data-stu-id="1a6ef-135">Statement lambdas</span></span> ##

<span data-ttu-id="1a6ef-136">Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp
(input parameters) => { statement; }
```

<span data-ttu-id="1a6ef-137">Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-137">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

<span data-ttu-id="1a6ef-138">Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-138">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="1a6ef-139">Asynchronní lambdas</span><span class="sxs-lookup"><span data-stu-id="1a6ef-139">Async lambdas</span></span> ##

<span data-ttu-id="1a6ef-140">Můžete snadno vytvořit lambda – výrazy a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](language-reference/keywords/async.md) a [await](language-reference/keywords/await.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-140">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](language-reference/keywords/async.md) and [await](language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="1a6ef-141">Například v příkladu volá `ShowSquares` metoda, která spustí asynchronně.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-141">For example, the example calls a `ShowSquares` method that executes asynchronously.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

<span data-ttu-id="1a6ef-142">Další informace o tom, jak vytvořit a použít asynchronní metody najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="1a6ef-142">For more information about how to create and use async methods, see [Asynchronous programming with async and await](programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="1a6ef-143">Lambda – výrazy a řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="1a6ef-143">Lambda expressions and tuples</span></span> ##

<span data-ttu-id="1a6ef-144">Od verze 7.0 C#, jazyka C# poskytuje integrovanou podporu pro řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-144">Starting with C# 7.0, the C# language provides built-in support for tuples.</span></span> <span data-ttu-id="1a6ef-145">Můžete zadat jako argument výraz lambda řazené kolekce členů a vaše výrazu lambda může také vrátit řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-145">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="1a6ef-146">V některých případech kompilátor jazyka C# pomocí odvození typu Určuje typy součástí řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-146">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span> 

<span data-ttu-id="1a6ef-147">Můžete definovat řazené kolekce členů uzavřením čárkami oddělený seznam jeho součástí do závorek.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-147">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="1a6ef-148">Následující příklad používá řazené kolekce členů s 5 součásti předat výrazu lambda, která zdvojnásobí každou hodnotu a vrátí řazené kolekce členů s 5 komponenty obsahující výsledek součinů pořadí čísel.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-148">The following example uses tuple with 5 components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with 5 components that contains the result of the multiplications.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

<span data-ttu-id="1a6ef-149">Obvykle jsou pojmenované pole řazené kolekce členů `Item1`, `Item2`atd. Můžete však definovat řazené kolekce členů s s názvem součásti, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-149">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

<span data-ttu-id="1a6ef-150">Další informace o podpoře pro řazené kolekce členů v jazyce C#, najdete v části [typy C# řazené kolekce členů](tuples.md).</span><span class="sxs-lookup"><span data-stu-id="1a6ef-150">For more information on support for tuples in C#, see [C# Tuple types](tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="1a6ef-151">Lambdas s standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="1a6ef-151">Lambdas with the standard query operators</span></span> ##

<span data-ttu-id="1a6ef-152">LINQ na objekty mezi jiných implementacích mít vstupní parametr s typem je jedním z <xref:System.Func%601> rodiny obecných delegátů.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-152">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="1a6ef-153">Tyto delegáti pomocí parametrů typu lze definovat počet a typ vstupní parametry a návratový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-153">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="1a6ef-154">`Func`Delegáti jsou velmi užitečné pro zapouzdření uživatelem definované výrazy, které se použijí pro každý prvek v sadě zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-154">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="1a6ef-155">Představte si třeba <xref:System.Func%601> delegáta, kde je syntaxe:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-155">For example, consider the <xref:System.Func%601> delegate, whose syntax is:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

<span data-ttu-id="1a6ef-156">Delegát může být vytvořena s podobně jako tento kód</span><span class="sxs-lookup"><span data-stu-id="1a6ef-156">The delegate can be instantiated with code like the following</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

<span data-ttu-id="1a6ef-157">kde `int` je vstupní parametr, a `bool` je návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-157">where `int` is an input parameter, and `bool` is the return value.</span></span> <span data-ttu-id="1a6ef-158">Vrácená hodnota je vždy určena v posledním parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-158">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="1a6ef-159">Pokud následující `Func` delegát vyvolán, vrátí hodnotu PRAVDA nebo NEPRAVDA označuje, zda vstupní parametr rovna 5:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-159">When the following `Func` delegate is invoked, it returns true or false to indicate whether the input parameter is equal to 5:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

<span data-ttu-id="1a6ef-160">Výraz lambda může taky poskytovat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například v operátory standardní dotazu, které jsou definovány v <xref:System.Linq.Queryable> typu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-160">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="1a6ef-161">Pokud zadáte <xref:System.Linq.Expressions.Expression%601> argument, argument lambda kompiluje na strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-161">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span> <span data-ttu-id="1a6ef-162">Následující příklad používá [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) operátor standardní dotazu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-162">The following example uses the [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standard query operator.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

<span data-ttu-id="1a6ef-163">Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-163">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="1a6ef-164">Tento výraz lambda konkrétní počty těchto celých čísel (`n`), pokud dělený dva, mít zbytek 1.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-164">This particular lambda expression counts those integers (`n`) that, when divided by two, have a remainder of 1.</span></span>

<span data-ttu-id="1a6ef-165">Následující příklad vytvoří sekvenci, která obsahuje všechny elementy ve `numbers` pole, které předcházet 9, protože se jedná o první číslo v pořadí, které nesplňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-165">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

<span data-ttu-id="1a6ef-166">Následující příklad určuje více vstupních parametrů uzavřené v závorkách.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-166">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="1a6ef-167">V poli čísla, dokud zjistí číslo, jehož hodnota je menší než jeho pořadové číslo pozice v poli, vrátí metoda všechny elementy.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-167">The method returns all the elements in the numbers array until it encounters a number whose value is less than its ordinal position in the array.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="1a6ef-168">Odvození typu v výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="1a6ef-168">Type inference in lambda expressions</span></span> ##

<span data-ttu-id="1a6ef-169">Při zápisu lambdas, často není nutné zadávat typ pro vstupní parametry, protože kompilátor můžete odvození typu na základě textu lambda, typy parametrů a dalších faktorech, jak je popsáno v specifikace jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-169">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors, as described in the C# Language Specification.</span></span> <span data-ttu-id="1a6ef-170">Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-170">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="1a6ef-171">Pokud se dotazuje `IEnumerable<Customer>`, pak je potřeba odvodit vstupní proměnné `Customer` objekt, což znamená, máte přístup k jeho metody a vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-171">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

<span data-ttu-id="1a6ef-172">Obecná pravidla pro odvození typu pro lambdas jsou:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-172">The general rules for type inference for lambdas are:</span></span>

- <span data-ttu-id="1a6ef-173">Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-173">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="1a6ef-174">Všechny vstupní argumenty v argument lambda musí být implicitně převést na jeho odpovídající parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-174">Each input argument in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="1a6ef-175">Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-175">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>

<span data-ttu-id="1a6ef-176">Výrazy lambda nemají vlastní určený typ, protože systém běžných typů nezná vnitřní pojem „výraz lambda“.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-176">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="1a6ef-177">Někdy je však vhodné hovořit neformálně o „typu“ výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-177">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="1a6ef-178">V těchto případech se typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ výrazu lambda je převeden.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-178">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="1a6ef-179">Rozsah proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="1a6ef-179">Variable Scope in Lambda Expressions</span></span> ##

<span data-ttu-id="1a6ef-180">Lambdas mohou odkazovat na *vnější proměnné* (viz [anonymní metody](programming-guide/statements-expressions-operators/anonymous-methods.md)), které jsou v oboru v metody, která definuje funkci lambda, nebo v oboru v typu, který obsahuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-180">Lambdas can refer to *outer variables* (see [Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="1a6ef-181">Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-181">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="1a6ef-182">Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-182">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="1a6ef-183">Následující příklad ukazuje, tato pravidla.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-183">The following example demonstrates these rules.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 <span data-ttu-id="1a6ef-184">Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="1a6ef-184">The following rules apply to variable scope in lambda expressions:</span></span>

- <span data-ttu-id="1a6ef-185">Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-185">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="1a6ef-186">Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné ve vnější metodě.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-186">Variables introduced within a lambda expression are not visible in the outer method.</span></span>

- <span data-ttu-id="1a6ef-187">Výraz lambda nemůže zaznamenat přímo `ref` nebo `out` parametr z metody nadřazených.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-187">A lambda expression cannot directly capture a `ref` or `out` parameter from an enclosing method.</span></span>

- <span data-ttu-id="1a6ef-188">Příkaz return ve výrazu lambda nezpůsobí vrácení ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-188">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>

- <span data-ttu-id="1a6ef-189">Nemůže obsahovat výraz lambda `goto` příkaz `break` prohlášení, nebo `continue` příkaz, který je uvnitř funkce lambda, pokud příkaz přechod cíl je mimo blok.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-189">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="1a6ef-190">Je také chybou mít příkaz skoku mimo blok funkce lambda, pokud je cíl uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="1a6ef-190">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a6ef-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a6ef-191">See also</span></span> ##

<span data-ttu-id="1a6ef-192">[LINQ (Language-Integrated Query)](../standard/using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="1a6ef-192">[LINQ (Language-Integrated Query)](../standard/using-linq.md) </span></span>  
<span data-ttu-id="1a6ef-193">[Anonymní metody](programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="1a6ef-193">[Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
[<span data-ttu-id="1a6ef-194">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="1a6ef-194">Expression trees</span></span>](expression-trees.md)
