---
title: 'Postupy: získávání hodnoty proměnné ukazatele - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 288d8cb2d286f55cc9a162614d45ef7b298f79f1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974481"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="22879-102">Postupy: získávání hodnoty proměnné ukazatele (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="22879-102">How to: obtain the value of a pointer variable (C# Programming Guide)</span></span>

<span data-ttu-id="22879-103">Použijte operátor dereference ukazatele k získání proměnnou na umístění, na které odkazuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="22879-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="22879-104">Výraz používá následující formulář, kde `p` je typ ukazatele:</span><span class="sxs-lookup"><span data-stu-id="22879-104">The expression takes the following form, where `p` is a pointer type:</span></span>  

```csharp
*p;  
```

<span data-ttu-id="22879-105">Unární operátor dereference nelze použít ve výrazu typu jiného než typu ukazatel.</span><span class="sxs-lookup"><span data-stu-id="22879-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="22879-106">Navíc na nelze použít [void](../../../csharp/language-reference/keywords/void.md) ukazatele.</span><span class="sxs-lookup"><span data-stu-id="22879-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  

<span data-ttu-id="22879-107">Při použití operátoru dereference na [null](../../../csharp/language-reference/keywords/null.md) ukazatelem, výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="22879-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  

## <a name="example"></a><span data-ttu-id="22879-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="22879-108">Example</span></span>

<span data-ttu-id="22879-109">V následujícím příkladu se proměnná typu `char` lze přistupovat pomocí ukazatele na různé typy.</span><span class="sxs-lookup"><span data-stu-id="22879-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="22879-110">Všimněte si, že adresa `theChar` spuštění, se liší, protože fyzická adresa přidělené na proměnnou můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="22879-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
<span data-ttu-id="22879-111">**Hodnota theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="22879-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="22879-112">**Adresa theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="22879-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="22879-113">**Hodnota pChar = Z**</span><span class="sxs-lookup"><span data-stu-id="22879-113">**Value of pChar = Z**</span></span>  
<span data-ttu-id="22879-114">**Hodnota pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="22879-114">**Value of pInt = 90**</span></span>  

## <a name="see-also"></a><span data-ttu-id="22879-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22879-115">See also</span></span>

- [<span data-ttu-id="22879-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="22879-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="22879-117">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="22879-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="22879-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="22879-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="22879-119">Typy</span><span class="sxs-lookup"><span data-stu-id="22879-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="22879-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="22879-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="22879-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="22879-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="22879-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="22879-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
