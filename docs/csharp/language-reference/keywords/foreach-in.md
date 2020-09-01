---
description: foreach, in (Referenční dokumentace jazyka C#)
title: Příkaz C# foreach
ms.date: 07/22/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 2ed89fa52b2d3d369d668bf79ab32eaf7be18a8a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142073"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="f001a-103">foreach, in (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f001a-103">foreach, in (C# reference)</span></span>

<span data-ttu-id="f001a-104">`foreach`Příkaz spustí příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní nebo, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="f001a-104">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="f001a-105">`foreach`Příkaz není omezen na tyto typy.</span><span class="sxs-lookup"><span data-stu-id="f001a-105">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="f001a-106">Můžete ji použít s instancí libovolného typu, který splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="f001a-106">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="f001a-107">typ má metodu public bez parametrů `GetEnumerator` , jejíž návratový typ je buď třída, struktura, nebo typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f001a-107">a type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="f001a-108">návratový typ `GetEnumerator` metody má veřejnou `Current` vlastnost a metodu public bez parametrů, `MoveNext` jejíž návratový typ je <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="f001a-108">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="f001a-109">Následující příklad používá `foreach` příkaz s instancí <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádná rozhraní:</span><span class="sxs-lookup"><span data-stu-id="f001a-109">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="f001a-110">Počínaje jazykem C# 7,3, pokud vlastnost enumerátoru `Current` vrátí [návratovou hodnotu odkazu](ref.md#reference-return-values) ( `ref T` kde `T` je typ prvku kolekce), můžete deklarovat proměnnou iterace pomocí `ref` `ref readonly` modifikátoru nebo, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="f001a-110">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="f001a-111">Počínaje jazykem C# 8,0 můžete použít `await foreach` příkaz pro využívání asynchronního datového proudu dat, tedy typu kolekce, který implementuje <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f001a-111">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="f001a-112">Každá iterace smyčky může být pozastavena, zatímco je další prvek načten asynchronně.</span><span class="sxs-lookup"><span data-stu-id="f001a-112">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="f001a-113">Následující příklad ukazuje, jak použít `await foreach` příkaz:</span><span class="sxs-lookup"><span data-stu-id="f001a-113">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="f001a-114">Ve výchozím nastavení jsou prvky Stream zpracovávány v zachyceném kontextu.</span><span class="sxs-lookup"><span data-stu-id="f001a-114">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="f001a-115">Pokud chcete zakázat zachycování kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f001a-115">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="f001a-116">Další informace o kontextech synchronizace a záznamech aktuálního kontextu naleznete v tématu [spotřebovávání asynchronního vzoru založeného na úlohách](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f001a-116">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="f001a-117">Další informace o asynchronních datových proudech naleznete v části [asynchronní datové proudy](../../whats-new/csharp-8.md#asynchronous-streams) [v článku novinky v C# 8,0](../../whats-new/csharp-8.md) .</span><span class="sxs-lookup"><span data-stu-id="f001a-117">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="f001a-118">V jakémkoli bodě `foreach` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="f001a-118">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f001a-119">Můžete také ukončit `foreach` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="f001a-119">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="f001a-120">Pokud `foreach` je příkaz použit na `null` , <xref:System.NullReferenceException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f001a-120">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="f001a-121">Pokud je zdrojová kolekce `foreach` příkazu prázdná, tělo `foreach` smyčky se neprovede a přeskočí.</span><span class="sxs-lookup"><span data-stu-id="f001a-121">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="f001a-122">Typ proměnné iterace</span><span class="sxs-lookup"><span data-stu-id="f001a-122">Type of an iteration variable</span></span>

<span data-ttu-id="f001a-123">Klíčové slovo lze použít `var` k umožnění kompilátoru odvodit typ iterační proměnné v `foreach` příkazu, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f001a-123">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="f001a-124">Můžete také explicitně zadat typ proměnné iterace, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f001a-124">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="f001a-125">V předchozím formuláři `T` musí být typ elementu kolekce implicitně nebo explicitně převoditelné na typ `V` proměnné iterace.</span><span class="sxs-lookup"><span data-stu-id="f001a-125">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="f001a-126">Pokud explicitní převod z `T` na `V` neuspěje v době běhu, `foreach` příkaz vyvolá výjimku <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="f001a-126">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="f001a-127">Například pokud `T` je typ třídy, který není zapečetěný, `V` může být libovolný typ rozhraní, a to i ten, který `T` neimplementuje.</span><span class="sxs-lookup"><span data-stu-id="f001a-127">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="f001a-128">V době běhu může být typ elementu kolekce ten, který je odvozen z `T` a skutečně implementuje `V` .</span><span class="sxs-lookup"><span data-stu-id="f001a-128">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="f001a-129">V takovém případě <xref:System.InvalidCastException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f001a-129">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f001a-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f001a-130">C# language specification</span></span>

<span data-ttu-id="f001a-131">Další informace naleznete v oddílu [foreach příkazu](~/_csharplang/spec/statements.md#the-foreach-statement) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f001a-131">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f001a-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f001a-132">See also</span></span>

- [<span data-ttu-id="f001a-133">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="f001a-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f001a-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f001a-134">C# keywords</span></span>](index.md)
- [<span data-ttu-id="f001a-135">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="f001a-135">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="f001a-136">for – příkaz</span><span class="sxs-lookup"><span data-stu-id="f001a-136">for statement</span></span>](for.md)
