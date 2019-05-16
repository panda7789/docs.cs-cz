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
ms.openlocfilehash: 9a10bcc809f3ecbc9a0fa9b917940b8e030fab8f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635105"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="4fe36-102">Postupy: získávání hodnoty proměnné ukazatele (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="4fe36-102">How to: obtain the value of a pointer variable (C# Programming Guide)</span></span>

<span data-ttu-id="4fe36-103">Použijte operátor dereference ukazatele k získání proměnnou na umístění, na které odkazuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="4fe36-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="4fe36-104">Výraz používá následující formulář, kde `p` je typ ukazatele:</span><span class="sxs-lookup"><span data-stu-id="4fe36-104">The expression takes the following form, where `p` is a pointer type:</span></span>  

```csharp
*p;  
```

<span data-ttu-id="4fe36-105">Unární operátor dereference nelze použít ve výrazu typu jiného než typu ukazatel.</span><span class="sxs-lookup"><span data-stu-id="4fe36-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="4fe36-106">Navíc na nelze použít [void](../../../csharp/language-reference/keywords/void.md) ukazatele.</span><span class="sxs-lookup"><span data-stu-id="4fe36-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  

<span data-ttu-id="4fe36-107">Při použití operátoru dereference na [null](../../../csharp/language-reference/keywords/null.md) ukazatelem, výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="4fe36-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  

## <a name="example"></a><span data-ttu-id="4fe36-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fe36-108">Example</span></span>

<span data-ttu-id="4fe36-109">V následujícím příkladu se proměnná typu `char` lze přistupovat pomocí ukazatele na různé typy.</span><span class="sxs-lookup"><span data-stu-id="4fe36-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="4fe36-110">Všimněte si, že adresa `theChar` spuštění, se liší, protože fyzická adresa přidělené na proměnnou můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="4fe36-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
<span data-ttu-id="4fe36-111">**Hodnota theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="4fe36-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="4fe36-112">**Adresa theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="4fe36-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="4fe36-113">**Hodnota pChar = Z**</span><span class="sxs-lookup"><span data-stu-id="4fe36-113">**Value of pChar = Z**</span></span>  
<span data-ttu-id="4fe36-114">**Hodnota pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="4fe36-114">**Value of pInt = 90**</span></span>  

## <a name="see-also"></a><span data-ttu-id="4fe36-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fe36-115">See also</span></span>

- [<span data-ttu-id="4fe36-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4fe36-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4fe36-117">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="4fe36-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="4fe36-118">Typy</span><span class="sxs-lookup"><span data-stu-id="4fe36-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="4fe36-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="4fe36-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="4fe36-120">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="4fe36-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="4fe36-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="4fe36-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
