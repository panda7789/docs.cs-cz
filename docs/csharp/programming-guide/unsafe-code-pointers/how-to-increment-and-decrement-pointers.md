---
title: 'Postupy: přírůstek a úbytek ukazatelů (C# Programming Guide)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: c75432d88a1e96742573a6e69a4e035066a387c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128333"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="838d3-102">Postupy: přírůstek a úbytek ukazatelů (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="838d3-102">How to: increment and decrement pointers (C# Programming Guide)</span></span>

<span data-ttu-id="838d3-103">Použít přírůstek a snížení operátory `++` a `--`, chcete-li změnit umístění ukazatele podle `sizeof(pointer-type)` ukazatele typu `pointer-type*`.</span><span class="sxs-lookup"><span data-stu-id="838d3-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by `sizeof(pointer-type)` for a pointer of the type `pointer-type*`.</span></span> <span data-ttu-id="838d3-104">Výrazy Inkrementace a dekrementace následující podobu:</span><span class="sxs-lookup"><span data-stu-id="838d3-104">The increment and decrement expressions take the following form:</span></span>  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="838d3-105">Operátory přírůstku a snížení lze použít u libovolného typu s výjimkou typu ukazatele `void*`.</span><span class="sxs-lookup"><span data-stu-id="838d3-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="838d3-106">Efekt použití operátoru Inkrementace na ukazatel typu `pointer-type*` je přidání `sizeof(pointer-type)` na adresu, která je obsažena v proměnné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="838d3-106">The effect of applying the increment operator to a pointer of the type `pointer-type*` is to add `sizeof(pointer-type)` to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="838d3-107">Efekt použití operátoru dekrementace na ukazatel typu `pointer-type*` se má odečíst `sizeof(pointer-type)` z adresy, které jsou obsaženy v proměnné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="838d3-107">The effect of applying the decrement operator to a pointer of the type `pointer-type*` is to subtract `sizeof(pointer-type)` from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="838d3-108">Nejsou generovány žádné výjimky, když došlo k přetečení domény ukazatele a výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="838d3-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="838d3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="838d3-109">Example</span></span>  
 <span data-ttu-id="838d3-110">V tomto příkladu můžete projít pole zvýšením ukazatel velikostí `int`.</span><span class="sxs-lookup"><span data-stu-id="838d3-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="838d3-111">U každého kroku si prohlédnout adresu a obsah elementu pole.</span><span class="sxs-lookup"><span data-stu-id="838d3-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="838d3-112">**Hodnota: 0 @ adresa: 12860272**
**hodnota: 1 @ adresa: 12860276**
**hodnota: 2 @ adresa: 12860280**
**hodnota: 3 @ adresa : 12860284**
**hodnota: 4 @ adresa: 12860288**</span><span class="sxs-lookup"><span data-stu-id="838d3-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="838d3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="838d3-113">See also</span></span>

- [<span data-ttu-id="838d3-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="838d3-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="838d3-115">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="838d3-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="838d3-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="838d3-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="838d3-117">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="838d3-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="838d3-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="838d3-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="838d3-119">Typy</span><span class="sxs-lookup"><span data-stu-id="838d3-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="838d3-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="838d3-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="838d3-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="838d3-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="838d3-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="838d3-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
- [<span data-ttu-id="838d3-123">sizeof</span><span class="sxs-lookup"><span data-stu-id="838d3-123">sizeof</span></span>](../../../csharp/language-reference/keywords/sizeof.md)
