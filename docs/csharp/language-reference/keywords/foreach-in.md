---
title: Příkaz foreach jazyka C#
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 3fbaacb96be2714aaff49679836e5d2d4a3783da
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422467"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="bfa7b-102">foreach, in (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bfa7b-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="bfa7b-103">`foreach` Příkaz opakuje příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="bfa7b-104">`foreach` Příkaz není omezena pouze na tyto typy které můžou uplatnit na instanci typu, který splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="bfa7b-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="bfa7b-105">nemá veřejný konstruktor bez parametrů `GetEnumerator` metoda, jejíž návratový typ je třída, struktura nebo typ rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfa7b-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="bfa7b-106">Návratový typ `GetEnumerator` metoda má veřejnou `Current` vlastnost a veřejný konstruktor bez parametrů `MoveNext` metoda, jejíž návratový typ je <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="bfa7b-107">Od verze C# 7.3, pokud čítače výčtu `Current` vrátí vlastnost [odkazovat na návratovou hodnotu](ref.md#reference-return-values) (`ref T` kde `T` je typ prvku kolekce), můžete deklarovat proměnnou iterace `ref` nebo `ref readonly` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="bfa7b-108">Na libovolný bod v rámci `foreach` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu nebo kroku na následující iteraci ve smyčce pomocí [pokračovat](continue.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="bfa7b-109">Také můžete ukončit `foreach` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="bfa7b-110">Pokud `foreach` příkazu je použita na `null`, <xref:System.NullReferenceException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="bfa7b-111">Pokud zdrojové kolekce `foreach` příkaz je prázdný, text `foreach` smyčky není spuštěn a přeskočí.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="bfa7b-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="bfa7b-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="bfa7b-113">Následující příklad ukazuje použití `foreach` příkaz s instancí <xref:System.Collections.Generic.List%601> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="bfa7b-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="bfa7b-114">Následující příklad používá `foreach` příkaz s instancí <xref:System.Span%601?displayProperty=nameWithType> typ, který neimplementuje žádné rozhraní:</span><span class="sxs-lookup"><span data-stu-id="bfa7b-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="bfa7b-115">Následující příklad používá `ref` iterační proměnné a hodnotu každé položky v poli Výraz stackalloc.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="bfa7b-116">`ref readonly` Verze iterace kolekce, kterou chcete vytisknout všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="bfa7b-117">`readonly` Deklarace používá implicitní deklarace lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="bfa7b-118">Implicitní deklarace proměnných je možné buď pomocí `ref` nebo `ref readonly` deklarace, jak můžete explicitně zadané deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="bfa7b-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="bfa7b-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfa7b-119">C# language specification</span></span>

<span data-ttu-id="bfa7b-120">Další informace najdete v tématu [příkazu foreach](~/_csharplang/spec/statements.md#the-foreach-statement) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfa7b-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfa7b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfa7b-121">See also</span></span>

- [<span data-ttu-id="bfa7b-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfa7b-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bfa7b-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bfa7b-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bfa7b-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfa7b-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bfa7b-125">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="bfa7b-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="bfa7b-126">For – příkaz</span><span class="sxs-lookup"><span data-stu-id="bfa7b-126">for statement</span></span>](for.md)
