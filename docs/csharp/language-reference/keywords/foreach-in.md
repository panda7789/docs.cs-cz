---
title: C#příkaz foreach
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 9c1521f39dea72b51801a81b13e8a0203956731c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422796"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="c68b0-102">foreach, in (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="c68b0-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="c68b0-103">Příkaz `foreach` spustí příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje rozhraní <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c68b0-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c68b0-104">Příkaz `foreach` není omezen na tyto typy a lze jej použít na instanci libovolného typu, který splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="c68b0-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="c68b0-105">má veřejnou `GetEnumerator` metodu bez parametrů, jejíž návratový typ je buď třída, struktura, nebo typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c68b0-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="c68b0-106">návratový typ metody `GetEnumerator` má vlastnost Public `Current` a veřejnou metodu `MoveNext` bez parametrů, jejíž návratový typ je <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="c68b0-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="c68b0-107">Počínaje C# 7,3, pokud vlastnost `Current` čítače vrátí [návratovou hodnotu odkazu](ref.md#reference-return-values) (`ref T` kde `T` je typ prvku kolekce), můžete proměnnou iterace deklarovat pomocí modifikátoru `ref` nebo `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="c68b0-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="c68b0-108">V jakémkoli okamžiku v rámci bloku příkazu `foreach` lze rozdělit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="c68b0-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c68b0-109">Můžete také ukončit `foreach` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="c68b0-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="c68b0-110">Pokud je pro `null`použit příkaz `foreach`, je vyvolána <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="c68b0-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="c68b0-111">Pokud je zdrojová kolekce příkazu `foreach` prázdná, tělo `foreach` smyčky se neprovede a přeskočí.</span><span class="sxs-lookup"><span data-stu-id="c68b0-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="c68b0-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="c68b0-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c68b0-113">Následující příklad ukazuje použití příkazu `foreach` s instancí typu <xref:System.Collections.Generic.List%601>, která implementuje rozhraní <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="c68b0-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="c68b0-114">V dalším příkladu se používá příkaz `foreach` s instancí typu <xref:System.Span%601?displayProperty=nameWithType>, která neimplementuje žádná rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c68b0-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="c68b0-115">Následující příklad používá proměnnou iterace `ref` k nastavení hodnoty každé položky v poli stackalloc.</span><span class="sxs-lookup"><span data-stu-id="c68b0-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="c68b0-116">Verze `ref readonly` provede iteraci kolekce pro tisk všech hodnot.</span><span class="sxs-lookup"><span data-stu-id="c68b0-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="c68b0-117">Deklarace `readonly` používá implicitní deklaraci lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="c68b0-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="c68b0-118">Deklarace implicitních proměnných lze použít s deklaracemi `ref` nebo `ref readonly`, jako lze explicitně napsat deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="c68b0-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="c68b0-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c68b0-119">C# language specification</span></span>

<span data-ttu-id="c68b0-120">Další informace naleznete v části [příkazu foreach](~/_csharplang/spec/statements.md#the-foreach-statement) [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c68b0-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="c68b0-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c68b0-121">See also</span></span>

- [<span data-ttu-id="c68b0-122">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="c68b0-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c68b0-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c68b0-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c68b0-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c68b0-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c68b0-125">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="c68b0-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="c68b0-126">příkaz for</span><span class="sxs-lookup"><span data-stu-id="c68b0-126">for statement</span></span>](for.md)
