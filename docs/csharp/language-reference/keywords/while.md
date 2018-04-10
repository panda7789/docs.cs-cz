---
title: while (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a><span data-ttu-id="92dd2-102">while (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="92dd2-102">while (C# Reference)</span></span>
<span data-ttu-id="92dd2-103">`while` Příkaz spustí příkaz nebo blok příkazy, dokud vyhodnotí zadaný výraz pro `false`.</span><span class="sxs-lookup"><span data-stu-id="92dd2-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92dd2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="92dd2-104">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="92dd2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="92dd2-105">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="92dd2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="92dd2-106">Example</span></span>  
 <span data-ttu-id="92dd2-107">Protože test `while` výraz probíhá před každou provádění smyčky, `while` smyčky spustí vícekrát nebo.</span><span class="sxs-lookup"><span data-stu-id="92dd2-107">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="92dd2-108">Tím se liší od [provést](../../../csharp/language-reference/keywords/do.md) smyčky, které provede jeden či více krát.</span><span class="sxs-lookup"><span data-stu-id="92dd2-108">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="92dd2-109">A `while` můžete ukončit smyčky, kdy [zalomení](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkaz předá řízení mimo smyčky.</span><span class="sxs-lookup"><span data-stu-id="92dd2-109">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="92dd2-110">Chcete-li předat řízení do další iterace bez ukončení opakování, použijte [pokračovat](../../../csharp/language-reference/keywords/continue.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="92dd2-110">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="92dd2-111">Všimněte si rozdíl ve výstupu v předchozí tři příklady, v závislosti na tom, kde `int n` se zvýší.</span><span class="sxs-lookup"><span data-stu-id="92dd2-111">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="92dd2-112">V příkladu níže žádný výstup se generuje.</span><span class="sxs-lookup"><span data-stu-id="92dd2-112">In the example below no output is generated.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="92dd2-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="92dd2-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92dd2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="92dd2-114">See Also</span></span>  
 [<span data-ttu-id="92dd2-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="92dd2-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="92dd2-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="92dd2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="92dd2-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="92dd2-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="92dd2-118">while – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="92dd2-118">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="92dd2-119">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="92dd2-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
