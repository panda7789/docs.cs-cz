---
title: Porovnání ukazatelů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: fa980c944159c477c333762ffad569332fba9402
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869518"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="0471e-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0471e-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="0471e-103">Můžete použít následující operátory porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="0471e-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="0471e-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="0471e-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="0471e-105">Porovnání operátory porovnávají adresy dva operandy, jako by šlo celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="0471e-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0471e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0471e-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="0471e-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="0471e-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="0471e-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="0471e-108">See Also</span></span>

- [<span data-ttu-id="0471e-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0471e-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0471e-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="0471e-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="0471e-111">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0471e-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="0471e-112">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="0471e-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="0471e-113">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="0471e-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="0471e-114">Typy</span><span class="sxs-lookup"><span data-stu-id="0471e-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="0471e-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="0471e-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="0471e-116">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="0471e-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="0471e-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="0471e-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
