---
title: foreach, in (Referenční dokumentace jazyka C#)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: b6b7dc0a4d3970ddfbbb6635ccebbbd5b75671e4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="2e53e-102">foreach, in (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2e53e-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="2e53e-103">`foreach` Příkaz spustí příkaz nebo blok příkazů pro jednotlivé elementy v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2e53e-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="2e53e-104">`foreach` Příkaz není omezen na tyto typy a dají se použít k instanci žádný typ, který splňuje tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="2e53e-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="2e53e-105">má public bez parametrů `GetEnumerator` metoda, jejíž návratový typ je třída, struktura nebo typ rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e53e-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="2e53e-106">Návratový typ `GetEnumerator` metoda má veřejnosti `Current` vlastnost a public bez parametrů `MoveNext` metoda s návratovým typem <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="2e53e-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="2e53e-107">Kdykoli bodu v rámci `foreach` příkaz bloku, může dojít k narušení mimo smyčky pomocí [zalomení](break.md) – klíčové slovo nebo krok do další iterace ve smyčce pomocí [pokračovat](continue.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2e53e-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span> <span data-ttu-id="2e53e-108">Také můžete ukončit `foreach` cykly pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="2e53e-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="2e53e-109">Příklady</span><span class="sxs-lookup"><span data-stu-id="2e53e-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="2e53e-110">Následující příklad ukazuje použití `foreach` příkaz s instanci <xref:System.Collections.Generic.List%601> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="2e53e-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="2e53e-111">Další příklad používá `foreach` příkaz s instanci <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádné rozhraní:</span><span class="sxs-lookup"><span data-stu-id="2e53e-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="2e53e-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2e53e-112">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2e53e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e53e-113">See also</span></span>

[<span data-ttu-id="2e53e-114">Foreach – příkaz (specifikace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2e53e-114">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="2e53e-115">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="2e53e-115">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="2e53e-116">for</span><span class="sxs-lookup"><span data-stu-id="2e53e-116">for</span></span>](for.md)  
[<span data-ttu-id="2e53e-117">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="2e53e-117">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="2e53e-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2e53e-118">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="2e53e-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2e53e-119">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="2e53e-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2e53e-120">C# Programming Guide</span></span>](../../programming-guide/index.md)  