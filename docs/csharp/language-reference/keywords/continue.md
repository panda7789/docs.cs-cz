---
title: "continue (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1ace2c90d03593b51b9ea461a47e122c5da1ab81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="continue-c-reference"></a><span data-ttu-id="f683a-102">continue (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f683a-102">continue (C# Reference)</span></span>
<span data-ttu-id="f683a-103">`continue` Příkaz předá řízení do další iterace uzavření [při](../../../csharp/language-reference/keywords/while.md), [provést](../../../csharp/language-reference/keywords/do.md), [pro](../../../csharp/language-reference/keywords/for.md), nebo [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="f683a-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f683a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f683a-104">Example</span></span>  
 <span data-ttu-id="f683a-105">V tomto příkladu je inicializovat čítače počítat od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="f683a-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="f683a-106">Pomocí `continue` příkaz ve spojení s výraz `(i < 9)`, příkazy mezi `continue` a na konci `for` body jsou přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="f683a-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f683a-107">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f683a-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f683a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f683a-108">See Also</span></span>  
 [<span data-ttu-id="f683a-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f683a-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f683a-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f683a-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f683a-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f683a-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f683a-112">Příkaz BREAK</span><span class="sxs-lookup"><span data-stu-id="f683a-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
 [<span data-ttu-id="f683a-113">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="f683a-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
