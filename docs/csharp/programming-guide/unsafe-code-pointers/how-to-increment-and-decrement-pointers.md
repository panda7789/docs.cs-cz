---
title: 'Postupy: Přírůstek a úbytek ukazatelů (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 39cefc5dcebf1331a5e0ac0fadb8284e9041eb27
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138237"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="49735-102">Postupy: Přírůstek a úbytek ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="49735-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="49735-103">Použít přírůstek a snížení operátory `++` a `--`, chcete-li změnit umístění ukazatele podle [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) pro ukazatele typu ukazatele – typ \*.</span><span class="sxs-lookup"><span data-stu-id="49735-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type\*.</span></span> <span data-ttu-id="49735-104">Výrazy Inkrementace a dekrementace následující podobu:</span><span class="sxs-lookup"><span data-stu-id="49735-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="49735-105">Operátory přírůstku a snížení lze použít u libovolného typu s výjimkou typu ukazatele `void*`.</span><span class="sxs-lookup"><span data-stu-id="49735-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="49735-106">Efekt použití operátoru Inkrementace na ukazatel typu `pointer-type` je přidání [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) na adresu, která je obsažena v proměnné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="49735-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="49735-107">Efekt použití operátoru dekrementace na ukazatel typu `pointer-type` se má odečíst `sizeof` (`pointer-type`) z adresy, které jsou obsaženy v proměnné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="49735-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="49735-108">Nejsou generovány žádné výjimky, když došlo k přetečení domény ukazatele a výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="49735-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49735-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="49735-109">Example</span></span>  
 <span data-ttu-id="49735-110">V tomto příkladu můžete projít pole zvýšením ukazatel velikostí `int`.</span><span class="sxs-lookup"><span data-stu-id="49735-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="49735-111">U každého kroku si prohlédnout adresu a obsah elementu pole.</span><span class="sxs-lookup"><span data-stu-id="49735-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="49735-112">**Hodnota: 0 @ adresa: 12860272**
**hodnota: 1 @ adresa: 12860276**
**hodnota: 2 @ adresa: 12860280**
**hodnota: 3 @ adresa : 12860284**
**hodnota: 4 @ adresa: 12860288**</span><span class="sxs-lookup"><span data-stu-id="49735-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="49735-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="49735-113">See Also</span></span>

- [<span data-ttu-id="49735-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="49735-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="49735-115">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="49735-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="49735-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="49735-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="49735-117">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="49735-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="49735-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="49735-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="49735-119">Typy</span><span class="sxs-lookup"><span data-stu-id="49735-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="49735-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="49735-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="49735-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="49735-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="49735-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="49735-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
