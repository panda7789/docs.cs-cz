---
title: "goto – příkaz (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords: goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa12a7547cfcd4a2076b5b0a308139f8a823f482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="goto-c-reference"></a><span data-ttu-id="e77fb-102">goto – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e77fb-102">goto (C# Reference)</span></span>
<span data-ttu-id="e77fb-103">`goto` Příkaz přenáší prvku aplikace přímo do příkaz s popiskem.</span><span class="sxs-lookup"><span data-stu-id="e77fb-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="e77fb-104">Běžně se používají `goto` je přenos řízení na konkrétní případy switch popisek nebo výchozí štítek v `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e77fb-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="e77fb-105">`goto` Příkaz je také užitečné ze hluboko vložené smyčky.</span><span class="sxs-lookup"><span data-stu-id="e77fb-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77fb-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e77fb-106">Example</span></span>  
 <span data-ttu-id="e77fb-107">Následující příklad ukazuje, jak pomocí `goto` v [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="e77fb-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e77fb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e77fb-108">Example</span></span>  
 <span data-ttu-id="e77fb-109">Následující příklad ukazuje, jak pomocí `goto` pro přerušení z vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="e77fb-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e77fb-110">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e77fb-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e77fb-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e77fb-111">See Also</span></span>  
 [<span data-ttu-id="e77fb-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e77fb-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e77fb-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e77fb-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e77fb-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e77fb-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e77fb-115">goto – příkaz</span><span class="sxs-lookup"><span data-stu-id="e77fb-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="e77fb-116">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="e77fb-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
