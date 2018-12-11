---
title: 'Postupy: Získávání hodnoty proměnné ukazatele - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: b20642344b34b5426512ef64bde2ab33d55136b9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236632"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="3c4eb-102">Postupy: Získávání hodnoty proměnné ukazatele (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="3c4eb-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="3c4eb-103">Použijte operátor dereference ukazatele k získání proměnnou na umístění, na které odkazuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="3c4eb-104">Výraz používá následující formulář, kde `p` je typ ukazatele:</span><span class="sxs-lookup"><span data-stu-id="3c4eb-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="3c4eb-105">Unární operátor dereference nelze použít ve výrazu typu jiného než typu ukazatel.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="3c4eb-106">Navíc na nelze použít [void](../../../csharp/language-reference/keywords/void.md) ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="3c4eb-107">Při použití operátoru dereference na [null](../../../csharp/language-reference/keywords/null.md) ukazatelem, výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c4eb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c4eb-108">Example</span></span>  
 <span data-ttu-id="3c4eb-109">V následujícím příkladu se proměnná typu `char` lze přistupovat pomocí ukazatele na různé typy.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="3c4eb-110">Všimněte si, že adresa `theChar` spuštění, se liší, protože fyzická adresa přidělené na proměnnou můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
<span data-ttu-id="3c4eb-111">**Hodnota theChar = Z**
**adresu theChar = 12F718**
**hodnotu pChar = Z**
**hodnotu pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="3c4eb-111">**Value of theChar = Z**
**Address of theChar = 12F718**
**Value of pChar = Z**
**Value of pInt = 90**</span></span>

## <a name="see-also"></a><span data-ttu-id="3c4eb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c4eb-112">See Also</span></span>

- [<span data-ttu-id="3c4eb-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3c4eb-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3c4eb-114">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="3c4eb-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="3c4eb-115">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="3c4eb-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="3c4eb-116">Typy</span><span class="sxs-lookup"><span data-stu-id="3c4eb-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="3c4eb-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="3c4eb-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="3c4eb-118">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="3c4eb-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="3c4eb-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="3c4eb-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
