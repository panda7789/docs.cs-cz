---
title: Porovnání ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: a2cbbabdad1d79c82bb5b3ec02a391727e552c98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718634"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="cd821-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cd821-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="cd821-103">Můžete použít následující operátory porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="cd821-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="cd821-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="cd821-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="cd821-105">Porovnání operátory porovnávají adresy dva operandy, jako by šlo celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="cd821-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd821-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd821-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="cd821-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="cd821-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="cd821-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd821-108">See also</span></span>

- [<span data-ttu-id="cd821-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cd821-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cd821-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="cd821-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="cd821-111">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd821-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="cd821-112">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="cd821-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="cd821-113">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="cd821-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="cd821-114">Typy</span><span class="sxs-lookup"><span data-stu-id="cd821-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="cd821-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="cd821-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="cd821-116">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="cd821-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="cd821-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="cd821-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
