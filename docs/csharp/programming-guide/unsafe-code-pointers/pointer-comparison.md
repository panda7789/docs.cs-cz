---
title: Porovnání ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 5185bd5e1686858452efcc7c89e2c1977e094386
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969203"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="b059e-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b059e-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="b059e-103">Můžete použít následující operátory porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="b059e-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="b059e-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="b059e-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="b059e-105">Porovnání operátory porovnávají adresy dva operandy, jako by šlo celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="b059e-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b059e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b059e-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a><span data-ttu-id="b059e-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="b059e-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="b059e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b059e-108">See also</span></span>

- [<span data-ttu-id="b059e-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b059e-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b059e-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="b059e-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="b059e-111">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b059e-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="b059e-112">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="b059e-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="b059e-113">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="b059e-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="b059e-114">Typy</span><span class="sxs-lookup"><span data-stu-id="b059e-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="b059e-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="b059e-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="b059e-116">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="b059e-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="b059e-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b059e-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
