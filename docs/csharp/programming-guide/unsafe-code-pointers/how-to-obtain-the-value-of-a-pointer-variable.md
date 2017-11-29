---
title: "Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="6938c-102">Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6938c-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="6938c-103">Deferenční operátor ukazatel pomocí můžete získat proměnnou v umístění, na kterou ukazatel odkazuje.</span><span class="sxs-lookup"><span data-stu-id="6938c-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="6938c-104">Výraz má následující podobu, kde `p` je ukazatel typu:</span><span class="sxs-lookup"><span data-stu-id="6938c-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="6938c-105">Deferenční operátor unární nelze použít na výrazy, které jiného typu než je ukazatel typu.</span><span class="sxs-lookup"><span data-stu-id="6938c-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="6938c-106">Navíc nelze použít, aby [void](../../../csharp/language-reference/keywords/void.md) ukazatel.</span><span class="sxs-lookup"><span data-stu-id="6938c-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="6938c-107">Když použijete deferenční operátor k [null](../../../csharp/language-reference/keywords/null.md) ukazatele, výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="6938c-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6938c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6938c-108">Example</span></span>  
 <span data-ttu-id="6938c-109">V následujícím příkladu, proměnné typu `char` přistupuje pomocí ukazatele různých typů.</span><span class="sxs-lookup"><span data-stu-id="6938c-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="6938c-110">Všimněte si, že adresa `theChar` se liší z spustit na spustit, protože fyzické adresy přidělené do proměnné, můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="6938c-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 <span data-ttu-id="6938c-111">**Hodnota theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="6938c-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="6938c-112">**Adresa theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="6938c-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="6938c-113">**Hodnota pChar = Z** </span><span class="sxs-lookup"><span data-stu-id="6938c-113">**Value of pChar = Z** </span></span>  
<span data-ttu-id="6938c-114">**Hodnota pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="6938c-114">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="6938c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6938c-115">See Also</span></span>  
 [<span data-ttu-id="6938c-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6938c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6938c-117">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="6938c-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="6938c-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="6938c-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="6938c-119">Typy</span><span class="sxs-lookup"><span data-stu-id="6938c-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="6938c-120">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="6938c-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="6938c-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="6938c-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="6938c-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="6938c-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
