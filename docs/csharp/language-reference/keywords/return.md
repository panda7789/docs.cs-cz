---
title: return (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266107"
---
# <a name="return-c-reference"></a><span data-ttu-id="94f8e-102">return (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="94f8e-102">return (C# Reference)</span></span>
<span data-ttu-id="94f8e-103">`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí prvek volání metody.</span><span class="sxs-lookup"><span data-stu-id="94f8e-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="94f8e-104">Také se může vrátit Volitelná hodnota.</span><span class="sxs-lookup"><span data-stu-id="94f8e-104">It can also return an optional value.</span></span> <span data-ttu-id="94f8e-105">Pokud je metoda `void` typu, `return` příkaz lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="94f8e-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="94f8e-106">Pokud je příkaz return uvnitř `try` bloku, `finally` bloku, pokud existuje, bude proveden před voláním metody vrátí ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="94f8e-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94f8e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="94f8e-107">Example</span></span>  
 <span data-ttu-id="94f8e-108">V následujícím příkladu metoda `CalculateArea()` vrátí místní proměnné `area` jako [dvojité](../../../csharp/language-reference/keywords/double.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="94f8e-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="94f8e-109">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="94f8e-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94f8e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="94f8e-110">See Also</span></span>  
 [<span data-ttu-id="94f8e-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="94f8e-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="94f8e-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="94f8e-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="94f8e-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="94f8e-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="94f8e-114">return – příkaz</span><span class="sxs-lookup"><span data-stu-id="94f8e-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="94f8e-115">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="94f8e-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
