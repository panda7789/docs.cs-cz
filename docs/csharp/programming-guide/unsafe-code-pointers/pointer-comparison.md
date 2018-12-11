---
title: Porovnání ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 72d9017064959c801bd2702ff585ee16b1592da6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236788"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="069ab-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="069ab-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="069ab-103">Můžete použít následující operátory porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="069ab-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="069ab-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="069ab-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="069ab-105">Porovnání operátory porovnávají adresy dva operandy, jako by šlo celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="069ab-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="069ab-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="069ab-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="069ab-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="069ab-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="069ab-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="069ab-108">See Also</span></span>

- [<span data-ttu-id="069ab-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="069ab-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="069ab-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="069ab-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="069ab-111">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="069ab-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="069ab-112">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="069ab-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="069ab-113">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="069ab-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="069ab-114">Typy</span><span class="sxs-lookup"><span data-stu-id="069ab-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="069ab-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="069ab-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="069ab-116">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="069ab-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="069ab-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="069ab-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
