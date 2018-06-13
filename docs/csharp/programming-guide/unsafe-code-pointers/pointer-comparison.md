---
title: Porovnání ukazatelů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: af264cd1572faafe25ee170b35cbeb48ed0fb2aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337701"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="64289-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="64289-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="64289-103">Můžete použít následující operátory k porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="64289-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="64289-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="64289-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="64289-105">Relační operátory porovnávání adresy dva operandy jako v případě, že jsou bez znaménka celých čísel.</span><span class="sxs-lookup"><span data-stu-id="64289-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64289-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="64289-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="64289-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="64289-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="64289-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="64289-108">See Also</span></span>  
 [<span data-ttu-id="64289-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="64289-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="64289-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="64289-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="64289-111">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64289-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="64289-112">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="64289-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="64289-113">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="64289-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="64289-114">Typy</span><span class="sxs-lookup"><span data-stu-id="64289-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="64289-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="64289-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="64289-116">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="64289-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="64289-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="64289-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
