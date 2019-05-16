---
title: Porovnání ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 25bc1c7b701c36d2daf1918986eb6a8e56980990
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635137"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="f2cc3-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f2cc3-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="f2cc3-103">Můžete použít následující operátory porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="f2cc3-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="f2cc3-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="f2cc3-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="f2cc3-105">Porovnání operátory porovnávají adresy dva operandy, jako by šlo celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="f2cc3-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2cc3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2cc3-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a><span data-ttu-id="f2cc3-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="f2cc3-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="f2cc3-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2cc3-108">See also</span></span>

- [<span data-ttu-id="f2cc3-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f2cc3-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f2cc3-110">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2cc3-110">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="f2cc3-111">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="f2cc3-111">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [<span data-ttu-id="f2cc3-112">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f2cc3-112">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f2cc3-113">Typy</span><span class="sxs-lookup"><span data-stu-id="f2cc3-113">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="f2cc3-114">unsafe</span><span class="sxs-lookup"><span data-stu-id="f2cc3-114">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="f2cc3-115">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f2cc3-115">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="f2cc3-116">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f2cc3-116">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
