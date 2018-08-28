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
ms.openlocfilehash: 1b6a1ce2a8587c8630fece3d5c9a2186fbbc9c22
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001473"
---
# <a name="return-c-reference"></a><span data-ttu-id="5f39a-102">return (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5f39a-102">return (C# Reference)</span></span>
<span data-ttu-id="5f39a-103">`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí řízení volající metodě.</span><span class="sxs-lookup"><span data-stu-id="5f39a-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="5f39a-104">Také může vrátit nepovinnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5f39a-104">It can also return an optional value.</span></span> <span data-ttu-id="5f39a-105">Pokud je metoda `void` typ, `return` příkaz lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="5f39a-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="5f39a-106">Pokud je příkaz return uvnitř `try` bloku `finally` bloku, pokud existuje, budou spuštěny před ovládací prvek vrátí volajícímu metody.</span><span class="sxs-lookup"><span data-stu-id="5f39a-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f39a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f39a-107">Example</span></span>  
 <span data-ttu-id="5f39a-108">V následujícím příkladu metoda `CalculateArea()` vrátí lokální proměnná `area` jako [double](../../../csharp/language-reference/keywords/double.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5f39a-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5f39a-109">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f39a-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5f39a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f39a-110">See Also</span></span>

- [<span data-ttu-id="5f39a-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f39a-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5f39a-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5f39a-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5f39a-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f39a-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="5f39a-114">return – příkaz</span><span class="sxs-lookup"><span data-stu-id="5f39a-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
- [<span data-ttu-id="5f39a-115">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="5f39a-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
