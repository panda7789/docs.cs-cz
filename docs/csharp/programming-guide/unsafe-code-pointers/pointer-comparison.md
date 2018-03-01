---
title: "Porovnání ukazatelů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0b45b9152272244b9a0c9d0fa3787973f8f8182a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="23b7a-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="23b7a-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="23b7a-103">Můžete použít následující operátory k porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="23b7a-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="23b7a-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="23b7a-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="23b7a-105">Relační operátory porovnávání adresy dva operandy jako v případě, že jsou bez znaménka celých čísel.</span><span class="sxs-lookup"><span data-stu-id="23b7a-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23b7a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="23b7a-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="23b7a-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="23b7a-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="23b7a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="23b7a-108">See Also</span></span>  
 [<span data-ttu-id="23b7a-109">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="23b7a-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="23b7a-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="23b7a-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="23b7a-111">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="23b7a-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="23b7a-112">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="23b7a-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="23b7a-113">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="23b7a-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="23b7a-114">Typy</span><span class="sxs-lookup"><span data-stu-id="23b7a-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="23b7a-115">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="23b7a-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="23b7a-116">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="23b7a-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="23b7a-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="23b7a-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
