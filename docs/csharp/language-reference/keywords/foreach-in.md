---
title: Příkaz C# foreach
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401885"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="df688-102">foreach, in (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="df688-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="df688-103">`foreach`Příkaz spustí příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní nebo.</span><span class="sxs-lookup"><span data-stu-id="df688-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="df688-104">`foreach`Příkaz není omezen na tyto typy a lze jej použít na instanci libovolného typu, který splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="df688-104">The `foreach` statement isn't limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="df688-105">má veřejnou metodu bez parametrů `GetEnumerator` , jejíž návratový typ je buď třída, struktura, nebo typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df688-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="df688-106">návratový typ `GetEnumerator` metody má veřejnou `Current` vlastnost a metodu public bez parametrů, `MoveNext` jejíž návratový typ je <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="df688-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="df688-107">Ve většině případů používá `foreach` iteraci `IEnumerable<T>` výraz, ve kterém je každý element typu `T` .</span><span class="sxs-lookup"><span data-stu-id="df688-107">In most uses, `foreach` iterates an `IEnumerable<T>` expression where each element is of type `T`.</span></span> <span data-ttu-id="df688-108">Prvky však mohou být libovolného typu, který má implicitní nebo explicitní převod z typu `Current` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df688-108">However, the elements may be any type that has an implicit or explicit conversion from the type of the `Current` property.</span></span> <span data-ttu-id="df688-109">Pokud se `Current` vlastnost vrátí `SomeType` , může být typ prvků:</span><span class="sxs-lookup"><span data-stu-id="df688-109">If the `Current` property returns `SomeType`, the type of the elements may be:</span></span>

- <span data-ttu-id="df688-110">Jakékoli základní třídy `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="df688-110">Any of the base classes of `SomeType`.</span></span>
- <span data-ttu-id="df688-111">Jakákoli rozhraní implementovaná `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="df688-111">Any of the interfaces implemented by `SomeType`.</span></span>

<span data-ttu-id="df688-112">Kromě toho, pokud `SomeType` je `class` nebo `interface` a nikoli `sealed` , může typ prvků zahrnovat:</span><span class="sxs-lookup"><span data-stu-id="df688-112">Furthermore, if `SomeType` is a `class` or an `interface` and not `sealed`, the type of elements may include:</span></span>

- <span data-ttu-id="df688-113">Jakýkoli typ odvozený z `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="df688-113">Any type derived from `SomeType`.</span></span>
- <span data-ttu-id="df688-114">Jakékoli libovolné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df688-114">Any arbitrary interface.</span></span> <span data-ttu-id="df688-115">Jakékoli rozhraní je povoleno, protože jakékoli rozhraní může být implementováno třídou odvozenou z nebo implementací `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="df688-115">Any interface is allowed because any interface may be implemented by a class derived from or implementing `SomeType`.</span></span>

<span data-ttu-id="df688-116">Proměnnou iterace můžete deklarovat pomocí libovolného typu, který odpovídá předchozím pravidlům.</span><span class="sxs-lookup"><span data-stu-id="df688-116">You may declare the iteration variable using any type that matches the preceding rules.</span></span> <span data-ttu-id="df688-117">Pokud převod z `SomeType` na typ proměnné iterace vyžaduje explicitní přetypování, může tato operace vyvolat výjimku, <xref:System.InvalidCastException> když se převod nezdařil.</span><span class="sxs-lookup"><span data-stu-id="df688-117">If the conversion from `SomeType` to the type of the iteration variable requires an explicit cast, that operation may throw an <xref:System.InvalidCastException> when the conversion fails.</span></span>

<span data-ttu-id="df688-118">Počínaje jazykem C# 7,3, pokud vlastnost enumerátoru `Current` vrátí [návratovou hodnotu odkazu](ref.md#reference-return-values) ( `ref T` kde `T` je typ prvku kolekce), můžete proměnnou iterace deklarovat pomocí `ref` `ref readonly` modifikátoru or.</span><span class="sxs-lookup"><span data-stu-id="df688-118">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="df688-119">Počínaje jazykem C# 8,0 `await` může být operátor aplikován na `foreach` příkaz, když typ kolekce implementuje <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df688-119">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="df688-120">Každá iterace smyčky může být pozastavena, zatímco je další prvek načten asynchronně.</span><span class="sxs-lookup"><span data-stu-id="df688-120">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="df688-121">Ve výchozím nastavení jsou prvky Stream zpracovávány v zachyceném kontextu.</span><span class="sxs-lookup"><span data-stu-id="df688-121">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="df688-122">Pokud chcete zakázat zachycování kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="df688-122">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="df688-123">Další informace o kontextech synchronizace a zaznamenávání aktuálního kontextu naleznete v článku o [využívání asynchronního vzoru založeného na úlohách](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="df688-123">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="df688-124">V jakémkoli bodě `foreach` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="df688-124">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="df688-125">Můžete také ukončit `foreach` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="df688-125">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="df688-126">Pokud `foreach` je příkaz použit na `null` , <xref:System.NullReferenceException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="df688-126">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="df688-127">Pokud je zdrojová kolekce `foreach` příkazu prázdná, tělo `foreach` smyčky se neprovede a přeskočí.</span><span class="sxs-lookup"><span data-stu-id="df688-127">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="df688-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="df688-128">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="df688-129">Následující příklad ukazuje použití `foreach` příkazu s instancí <xref:System.Collections.Generic.List%601> typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="df688-129">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="df688-130">Následující příklad používá `foreach` příkaz s instancí <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádná rozhraní:</span><span class="sxs-lookup"><span data-stu-id="df688-130">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="df688-131">Následující příklad používá `ref` proměnnou iterace k nastavení hodnoty každé položky v poli stackalloc.</span><span class="sxs-lookup"><span data-stu-id="df688-131">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="df688-132">`ref readonly`Verze projde kolekci pro tisk všech hodnot.</span><span class="sxs-lookup"><span data-stu-id="df688-132">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="df688-133">`readonly`Deklarace používá implicitní deklaraci lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="df688-133">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="df688-134">Deklarace implicitních proměnných lze použít s `ref` `ref readonly` deklaracemi nebo, jako lze explicitně napsat deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="df688-134">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="df688-135">Následující příklad používá `await foreach` k iteraci kolekce, která generuje každý prvek asynchronně:</span><span class="sxs-lookup"><span data-stu-id="df688-135">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a><span data-ttu-id="df688-136">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df688-136">C# language specification</span></span>

<span data-ttu-id="df688-137">Další informace naleznete v oddílu [foreach příkazu](~/_csharplang/spec/statements.md#the-foreach-statement) [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="df688-137">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="df688-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="df688-138">See also</span></span>

- [<span data-ttu-id="df688-139">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df688-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="df688-140">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="df688-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="df688-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df688-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="df688-142">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="df688-142">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="df688-143">for – příkaz</span><span class="sxs-lookup"><span data-stu-id="df688-143">for statement</span></span>](for.md)
