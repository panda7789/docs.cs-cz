---
title: Porovnání ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 5185bd5e1686858452efcc7c89e2c1977e094386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61677552"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="8236a-102">Porovnání ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8236a-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="8236a-103">Můžete použít následující operátory porovnání ukazatelů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="8236a-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="8236a-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="8236a-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="8236a-105">Porovnání operátory porovnávají adresy dva operandy, jako by šlo celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="8236a-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8236a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8236a-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a><span data-ttu-id="8236a-107">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="8236a-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="8236a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8236a-108">See also</span></span>

- [<span data-ttu-id="8236a-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8236a-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8236a-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="8236a-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="8236a-111">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8236a-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="8236a-112">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="8236a-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="8236a-113">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="8236a-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="8236a-114">Typy</span><span class="sxs-lookup"><span data-stu-id="8236a-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="8236a-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="8236a-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="8236a-116">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="8236a-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="8236a-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="8236a-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
