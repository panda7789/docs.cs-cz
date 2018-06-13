---
title: 'Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: c53026149837681235c6d1001707a25b9c8b40b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322949"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="87b40-102">Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="87b40-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="87b40-103">Deferenční operátor ukazatel pomocí můžete získat proměnnou v umístění, na kterou ukazatel odkazuje.</span><span class="sxs-lookup"><span data-stu-id="87b40-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="87b40-104">Výraz má následující podobu, kde `p` je ukazatel typu:</span><span class="sxs-lookup"><span data-stu-id="87b40-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="87b40-105">Deferenční operátor unární nelze použít na výrazy, které jiného typu než je ukazatel typu.</span><span class="sxs-lookup"><span data-stu-id="87b40-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="87b40-106">Navíc nelze použít, aby [void](../../../csharp/language-reference/keywords/void.md) ukazatel.</span><span class="sxs-lookup"><span data-stu-id="87b40-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="87b40-107">Když použijete deferenční operátor k [null](../../../csharp/language-reference/keywords/null.md) ukazatele, výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="87b40-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87b40-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="87b40-108">Example</span></span>  
 <span data-ttu-id="87b40-109">V následujícím příkladu, proměnné typu `char` přistupuje pomocí ukazatele různých typů.</span><span class="sxs-lookup"><span data-stu-id="87b40-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="87b40-110">Všimněte si, že adresa `theChar` se liší z spustit na spustit, protože fyzické adresy přidělené do proměnné, můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="87b40-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 <span data-ttu-id="87b40-111">**Hodnota theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="87b40-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="87b40-112">**Adresa theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="87b40-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="87b40-113">**Hodnota pChar = Z** </span><span class="sxs-lookup"><span data-stu-id="87b40-113">**Value of pChar = Z** </span></span>  
<span data-ttu-id="87b40-114">**Hodnota pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="87b40-114">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="87b40-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="87b40-115">See Also</span></span>  
 [<span data-ttu-id="87b40-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="87b40-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="87b40-117">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="87b40-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="87b40-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="87b40-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="87b40-119">Typy</span><span class="sxs-lookup"><span data-stu-id="87b40-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="87b40-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="87b40-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="87b40-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="87b40-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="87b40-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="87b40-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
