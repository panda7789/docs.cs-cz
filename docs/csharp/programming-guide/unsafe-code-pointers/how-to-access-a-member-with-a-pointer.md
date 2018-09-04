---
title: 'Postupy: Přístup ke členu pomocí ukazatele (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 715bc2c493b58757154aa114d1e0527cbad46f46
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511299"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="e5880-102">Postupy: Přístup ke členu pomocí ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e5880-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="e5880-103">Pro přístup ke členu struktury, která je deklarována v nezabezpečeném kontextu, můžete použít operátor přístupu členů, jak je znázorněno v následujícím příkladu, ve kterém `p` je ukazatel [struktura](../../../csharp/language-reference/keywords/struct.md) , který obsahuje člena `x`.</span><span class="sxs-lookup"><span data-stu-id="e5880-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="e5880-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5880-104">Example</span></span>  
 <span data-ttu-id="e5880-105">V tomto příkladu [struktura](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, která obsahuje dvě souřadnice `x` a `y` definována a je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="e5880-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="e5880-106">S použitím operátor přístupu členů `->` a ukazatel na instanci `home`, `x` a `y` jsou přiřazeny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e5880-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5880-107">Všimněte si, že výraz `p->x` je ekvivalentní výraz `(*p).x`, a získáte stejný výsledek jedním ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="e5880-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e5880-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5880-108">See Also</span></span>

- [<span data-ttu-id="e5880-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e5880-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e5880-110">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="e5880-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="e5880-111">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="e5880-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="e5880-112">Typy</span><span class="sxs-lookup"><span data-stu-id="e5880-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="e5880-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="e5880-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="e5880-114">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="e5880-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="e5880-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e5880-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
