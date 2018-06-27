---
title: Continue – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 6a409fe8c7fd07342138eac11bfd1766014da1bd
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948352"
---
# <a name="continue-c-reference"></a><span data-ttu-id="21880-102">continue (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="21880-102">continue (C# Reference)</span></span>

<span data-ttu-id="21880-103">`continue` Příkaz předá řízení do další iterace uzavření [při](../../../csharp/language-reference/keywords/while.md), [provést](../../../csharp/language-reference/keywords/do.md), [pro](../../../csharp/language-reference/keywords/for.md), nebo [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="21880-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="21880-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="21880-104">Example</span></span>

<span data-ttu-id="21880-105">V tomto příkladu je inicializovat čítače počítat od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="21880-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="21880-106">Pomocí `continue` příkaz ve spojení s výraz `(i < 9)`, příkazy mezi `continue` a na konci `for` body jsou přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="21880-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="21880-107">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="21880-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="21880-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21880-108">See also</span></span>

[<span data-ttu-id="21880-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="21880-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="21880-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="21880-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="21880-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="21880-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="21880-112">break – příkaz</span><span class="sxs-lookup"><span data-stu-id="21880-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
[<span data-ttu-id="21880-113">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="21880-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)