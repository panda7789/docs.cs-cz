---
title: 'Postupy: Přístup k elementu pole pomocí ukazatele (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 92eb7a79c0e7522d1474537aeefbfdb083a11dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332036"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="d225e-102">Postupy: Přístup k elementu pole pomocí ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d225e-102">How to: Access an Array Element with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="d225e-103">V kontextu unsafe mohly přistupovat k elementu v paměti pomocí přístupu k elementu ukazatele, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d225e-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 <span data-ttu-id="d225e-104">Výraz v hranatých závorkách musí být implicitně převést na `int`, `uint`, `long`, nebo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d225e-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="d225e-105">Operaci p [e] je ekvivalentní \*(p+e).</span><span class="sxs-lookup"><span data-stu-id="d225e-105">The operation p[e] is equivalent to \*(p+e).</span></span> <span data-ttu-id="d225e-106">Jako C a C++, přístup k elementu ukazatel nekontroluje out-of-bounds chyby.</span><span class="sxs-lookup"><span data-stu-id="d225e-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d225e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d225e-107">Example</span></span>  
 <span data-ttu-id="d225e-108">V tomto příkladu 123 umístění v paměti přidělovány do pole znaků, `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="d225e-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="d225e-109">Pole se používá k zobrazení písmena malá a velká písmena vede ke dvěma [pro](../../../csharp/language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="d225e-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>  
  
 <span data-ttu-id="d225e-110">Všimněte si, že výraz `charPointer[i]` je ekvivalentní výrazu `*(charPointer + i)`, a získáte stejný výsledek pomocí některé z dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="d225e-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 <span data-ttu-id="d225e-111">**Velká písmena:**</span><span class="sxs-lookup"><span data-stu-id="d225e-111">**Uppercase letters:**</span></span>  
<span data-ttu-id="d225e-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="d225e-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="d225e-113">**Malá písmena:**</span><span class="sxs-lookup"><span data-stu-id="d225e-113">**Lowercase letters:**</span></span>  
<span data-ttu-id="d225e-114">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="d225e-114">**abcdefghijklmnopqrstuvwxyz**</span></span>   
## <a name="see-also"></a><span data-ttu-id="d225e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d225e-115">See Also</span></span>  
 [<span data-ttu-id="d225e-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d225e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d225e-117">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d225e-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="d225e-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d225e-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="d225e-119">Typy</span><span class="sxs-lookup"><span data-stu-id="d225e-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="d225e-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="d225e-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="d225e-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="d225e-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="d225e-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="d225e-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
