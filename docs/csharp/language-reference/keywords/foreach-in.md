---
title: Příkaz C# foreach
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 188d909fd33b14755d9b121953b1fa434ecf536d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738817"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="c1db0-102">foreach, v (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="c1db0-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="c1db0-103">Příkaz `foreach` provede příkaz nebo blok příkazů pro každý prvek v instanci <xref:System.Collections.IEnumerable?displayProperty=nameWithType> typu, který implementuje rozhraní nebo. <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c1db0-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c1db0-104">Příkaz `foreach` není omezen na tyto typy a lze použít na instanci libovolného typu, který splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="c1db0-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="c1db0-105">má metodu `GetEnumerator` public parameterless, jejíž návratový typ je buď třída, struktura nebo typ rozhraní,</span><span class="sxs-lookup"><span data-stu-id="c1db0-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="c1db0-106">návratový typ `GetEnumerator` metody má `Current` public property a `MoveNext` public parameterless <xref:System.Boolean>metodu, jejíž návratový typ je .</span><span class="sxs-lookup"><span data-stu-id="c1db0-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="c1db0-107">Počínaje C# 7.3, `Current` pokud vlastnost čítače vrátí referenční`ref T` [vrácenou hodnotu](ref.md#reference-return-values) (kde `T` je typ prvku kolekce), `ref` `ref readonly` můžete deklarovat itidati proměnnou s modifikátorem nebo.</span><span class="sxs-lookup"><span data-stu-id="c1db0-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="c1db0-108">Počínaje C# 8.0, `await` operátor může být `foreach` použita na příkaz <xref:System.Collections.Generic.IAsyncEnumerable%601> při typ kolekce implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c1db0-108">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="c1db0-109">Každá iterace smyčky může být pozastavena, zatímco další prvek je načten asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c1db0-109">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="c1db0-110">Ve výchozím nastavení jsou prvky datového proudu zpracovány v zachyceném kontextu.</span><span class="sxs-lookup"><span data-stu-id="c1db0-110">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="c1db0-111">Pokud chcete zakázat zachycení kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c1db0-111">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="c1db0-112">Další informace o kontextech synchronizace a zachycení aktuálního kontextu naleznete v článku o [využití asynchronního vzoru založeného na úlohách](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c1db0-112">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="c1db0-113">V libovolném `foreach` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí [příkazu break](break.md) nebo krok k další iteraci ve smyčce pomocí [příkazu continue.](continue.md)</span><span class="sxs-lookup"><span data-stu-id="c1db0-113">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c1db0-114">`foreach` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="c1db0-114">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="c1db0-115">Pokud `foreach` je příkaz `null`použit <xref:System.NullReferenceException> na , je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="c1db0-115">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="c1db0-116">Pokud je zdrojová `foreach` kolekce příkazu prázdná, tělo `foreach` smyčky není spuštěno a přeskočeno.</span><span class="sxs-lookup"><span data-stu-id="c1db0-116">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="c1db0-117">Příklady</span><span class="sxs-lookup"><span data-stu-id="c1db0-117">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c1db0-118">Následující příklad ukazuje použití `foreach` příkazu s <xref:System.Collections.Generic.List%601> instancí typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c1db0-118">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="c1db0-119">Další příklad používá `foreach` příkaz s instancí typu, který neimplementuje <xref:System.Span%601?displayProperty=nameWithType> žádná rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c1db0-119">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="c1db0-120">Následující příklad používá `ref` itikovou proměnnou k nastavení hodnoty každé položky v poli stackalloc.</span><span class="sxs-lookup"><span data-stu-id="c1db0-120">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="c1db0-121">Verze `ref readonly` iteduje kolekce vytisknout všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c1db0-121">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="c1db0-122">Deklarace `readonly` používá implicitní deklaraci místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="c1db0-122">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="c1db0-123">Implicitní deklarace proměnných `ref` lze `ref readonly` použít s buď nebo deklarace, jak může explicitně zadali deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="c1db0-123">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

<span data-ttu-id="c1db0-124">Následující příklad `await foreach` používá k iterační kolekci, která generuje každý prvek asynchronně:</span><span class="sxs-lookup"><span data-stu-id="c1db0-124">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a><span data-ttu-id="c1db0-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1db0-125">C# language specification</span></span>

<span data-ttu-id="c1db0-126">Další informace naleznete v části [foreach prohlášení](~/_csharplang/spec/statements.md#the-foreach-statement) [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c1db0-126">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="c1db0-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1db0-127">See also</span></span>

- [<span data-ttu-id="c1db0-128">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1db0-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c1db0-129">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1db0-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c1db0-130">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c1db0-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c1db0-131">Použití foreach s poli</span><span class="sxs-lookup"><span data-stu-id="c1db0-131">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="c1db0-132">pro výpis</span><span class="sxs-lookup"><span data-stu-id="c1db0-132">for statement</span></span>](for.md)
