---
title: foreach, in (Referenční dokumentace jazyka C#)
ms.date: 06/28/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: e4b5ba6fb97d82d2b6f03e77995b9d3c2b9d68c6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104413"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="c1e4a-102">foreach, in (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c1e4a-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="c1e4a-103">`foreach` Příkaz spustí příkaz nebo blok příkazů pro jednotlivé elementy v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c1e4a-104">`foreach` Příkaz není omezen na tyto typy a dají se použít k instanci žádný typ, který splňuje tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="c1e4a-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="c1e4a-105">má public bez parametrů `GetEnumerator` metoda, jejíž návratový typ je třída, struktura nebo typ rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1e4a-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="c1e4a-106">Návratový typ `GetEnumerator` metoda má veřejnosti `Current` vlastnost a public bez parametrů `MoveNext` metoda s návratovým typem <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="c1e4a-107">Kdykoli bodu v rámci `foreach` příkaz bloku, může dojít k narušení mimo smyčky pomocí [zalomení](break.md) příkaz nebo krok do další iterace ve smyčce pomocí [pokračovat](continue.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c1e4a-108">Také můžete ukončit `foreach` cykly pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="c1e4a-109">Příklady</span><span class="sxs-lookup"><span data-stu-id="c1e4a-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c1e4a-110">Následující příklad ukazuje použití `foreach` příkaz s instanci <xref:System.Collections.Generic.List%601> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c1e4a-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="c1e4a-111">Další příklad používá `foreach` příkaz s instanci <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádné rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c1e4a-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="c1e4a-112">Počínaje 7.3 C#, když typ kolekce podporuje `ref` přístup k jeho prvky, můžou deklarovat proměnnou iteraci pomocí `ref` nebo `ref readonly` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-112">Beginning with C# 7.3, when the collection type supports `ref` access to its elements, you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span> <span data-ttu-id="c1e4a-113">Následující příklad používá `ref` proměnné iterace nastavit hodnotu každé položky v poli stackalloc.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="c1e4a-114">`ref readonly` Verze iterace kolekce k vytištění všech hodnot.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="c1e4a-115">`readonly` Deklarace používá implicitní deklarace místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="c1e4a-116">Implicitní deklarace proměnných lze použít s buď `ref` nebo `ref readonly` deklarace, jak můžete explicitně zadali deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="c1e4a-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="c1e4a-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1e4a-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c1e4a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1e4a-118">See also</span></span>

[<span data-ttu-id="c1e4a-119">Foreach – příkaz (specifikace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c1e4a-119">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="c1e4a-120">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="c1e4a-120">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="c1e4a-121">for</span><span class="sxs-lookup"><span data-stu-id="c1e4a-121">for</span></span>](for.md)  
[<span data-ttu-id="c1e4a-122">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="c1e4a-122">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="c1e4a-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1e4a-123">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="c1e4a-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1e4a-124">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="c1e4a-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c1e4a-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  