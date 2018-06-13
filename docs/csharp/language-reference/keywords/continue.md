---
title: continue (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: b3a9a17bb16ded19330cbc880b2e5e7271f269c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215667"
---
# <a name="continue-c-reference"></a><span data-ttu-id="61409-102">continue (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="61409-102">continue (C# Reference)</span></span>
<span data-ttu-id="61409-103">`continue` Příkaz předá řízení do další iterace uzavření [při](../../../csharp/language-reference/keywords/while.md), [provést](../../../csharp/language-reference/keywords/do.md), [pro](../../../csharp/language-reference/keywords/for.md), nebo [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="61409-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61409-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="61409-104">Example</span></span>  
 <span data-ttu-id="61409-105">V tomto příkladu je inicializovat čítače počítat od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="61409-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="61409-106">Pomocí `continue` příkaz ve spojení s výraz `(i < 9)`, příkazy mezi `continue` a na konci `for` body jsou přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="61409-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="61409-107">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61409-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="61409-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="61409-108">See Also</span></span>  
 [<span data-ttu-id="61409-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61409-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="61409-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="61409-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="61409-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61409-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="61409-112">break – příkaz</span><span class="sxs-lookup"><span data-stu-id="61409-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
 [<span data-ttu-id="61409-113">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="61409-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
