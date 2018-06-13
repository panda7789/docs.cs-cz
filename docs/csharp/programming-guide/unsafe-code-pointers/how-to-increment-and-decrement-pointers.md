---
title: 'Postupy: Přírůstek a úbytek ukazatelů (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: e1c3ac12a126450781d0ce78e788f39c740b5279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324282"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="2f7ef-102">Postupy: Přírůstek a úbytek ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2f7ef-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="2f7ef-103">Přírůstek a snížení operátory, `++` a `--`, chcete-li změnit umístění ukazatele podle [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) pro ukazatel typu ukazatele – typ \*.</span><span class="sxs-lookup"><span data-stu-id="2f7ef-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type\*.</span></span> <span data-ttu-id="2f7ef-104">Přírůstek a snížení výrazy mít tento tvar:</span><span class="sxs-lookup"><span data-stu-id="2f7ef-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="2f7ef-105">Operátory přírůstku a snížení lze použít na ukazatele libovolného typu, s výjimkou typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="2f7ef-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="2f7ef-106">Účinek použití operátor přírůstku na ukazatel typu `pointer-type` je přidání [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) na adresu, která je součástí proměnné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2f7ef-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="2f7ef-107">Účinek použití operátor snížení na ukazatel typu `pointer-type` je odečtena `sizeof` (`pointer-type`) z adresy, která je součástí proměnné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2f7ef-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="2f7ef-108">Žádné výjimky jsou generovány, pokud došlo k přetečení domény ukazatele a výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="2f7ef-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f7ef-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f7ef-109">Example</span></span>  
 <span data-ttu-id="2f7ef-110">V tomto příkladu jste jednotlivé kroky pole pomocí ukazatele a narůstajících o velikosti `int`.</span><span class="sxs-lookup"><span data-stu-id="2f7ef-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="2f7ef-111">Pro každý krok zobrazit adresu a je obsah pole elementu.</span><span class="sxs-lookup"><span data-stu-id="2f7ef-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 <span data-ttu-id="2f7ef-112">**Hodnota: 0 @ adresa: 12860272**</span><span class="sxs-lookup"><span data-stu-id="2f7ef-112">**Value:0 @ Address:12860272**</span></span>  
<span data-ttu-id="2f7ef-113">**Hodnota: 1 @ adresa: 12860276**</span><span class="sxs-lookup"><span data-stu-id="2f7ef-113">**Value:1 @ Address:12860276**</span></span>  
<span data-ttu-id="2f7ef-114">**Hodnota: 2 @ adresa: 12860280**</span><span class="sxs-lookup"><span data-stu-id="2f7ef-114">**Value:2 @ Address:12860280**</span></span>  
<span data-ttu-id="2f7ef-115">**Hodnota: 3 @ adresa: 12860284**</span><span class="sxs-lookup"><span data-stu-id="2f7ef-115">**Value:3 @ Address:12860284**</span></span>  
<span data-ttu-id="2f7ef-116">**Hodnota: 4 @ adresa: 12860288**</span><span class="sxs-lookup"><span data-stu-id="2f7ef-116">**Value:4 @ Address:12860288**</span></span>   
## <a name="see-also"></a><span data-ttu-id="2f7ef-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f7ef-117">See Also</span></span>  
 [<span data-ttu-id="2f7ef-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2f7ef-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2f7ef-119">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="2f7ef-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="2f7ef-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2f7ef-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="2f7ef-121">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="2f7ef-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="2f7ef-122">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="2f7ef-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="2f7ef-123">Typy</span><span class="sxs-lookup"><span data-stu-id="2f7ef-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="2f7ef-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="2f7ef-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="2f7ef-125">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="2f7ef-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="2f7ef-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="2f7ef-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
