---
title: "Postupy: Přístup ke členu pomocí ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 622d9910b09c9197b7f4ccd5e54e2675fbbbbccb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="f5dd1-102">Postupy: Přístup ke členu pomocí ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f5dd1-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="f5dd1-103">Pro přístup ke členu struktura, který je deklarován v kontextu unsafe, můžete použít operátor přístupu členů, jak je znázorněno v následujícím příkladu, ve kterém `p` je ukazatel na [struktura](../../../csharp/language-reference/keywords/struct.md) obsahující členem `x`.</span><span class="sxs-lookup"><span data-stu-id="f5dd1-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="f5dd1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5dd1-104">Example</span></span>  
 <span data-ttu-id="f5dd1-105">V tomto příkladu [struktura](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, který obsahuje dvě souřadnice `x` a `y` je deklarována a vytvořena.</span><span class="sxs-lookup"><span data-stu-id="f5dd1-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="f5dd1-106">Pomocí operátor přístupu členů `->` a ukazatel na instanci `home`, `x` a `y` přiřazené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f5dd1-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5dd1-107">Všimněte si, že výraz `p->x` je ekvivalentní výrazu `(*p).x`, a získáte stejný výsledek pomocí některé z dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f5dd1-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f5dd1-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5dd1-108">See Also</span></span>  
 [<span data-ttu-id="f5dd1-109">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f5dd1-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f5dd1-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f5dd1-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="f5dd1-111">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f5dd1-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="f5dd1-112">Typy</span><span class="sxs-lookup"><span data-stu-id="f5dd1-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="f5dd1-113">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="f5dd1-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="f5dd1-114">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f5dd1-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="f5dd1-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f5dd1-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
