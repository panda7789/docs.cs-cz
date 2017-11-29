---
title: "Postupy: Přístup k elementu pole pomocí ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 737c1d7fc0bc0a739de5c0a6cbc5dc09f813133e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="f41d7-102">Postupy: Přístup k elementu pole pomocí ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f41d7-102">How to: Access an Array Element with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="f41d7-103">V kontextu unsafe mohly přistupovat k elementu v paměti pomocí přístupu k elementu ukazatele, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f41d7-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 <span data-ttu-id="f41d7-104">Výraz v hranatých závorkách musí být implicitně převést na `int`, `uint`, `long`, nebo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f41d7-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="f41d7-105">Operaci p [e] je ekvivalentní *(p+e).</span><span class="sxs-lookup"><span data-stu-id="f41d7-105">The operation p[e] is equivalent to *(p+e).</span></span> <span data-ttu-id="f41d7-106">Jako C a C++, přístup k elementu ukazatel nekontroluje out-of-bounds chyby.</span><span class="sxs-lookup"><span data-stu-id="f41d7-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f41d7-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f41d7-107">Example</span></span>  
 <span data-ttu-id="f41d7-108">V tomto příkladu 123 umístění v paměti přidělovány do pole znaků, `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="f41d7-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="f41d7-109">Pole se používá k zobrazení písmena malá a velká písmena vede ke dvěma [pro](../../../csharp/language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="f41d7-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>  
  
 <span data-ttu-id="f41d7-110">Všimněte si, že výraz `charPointer[i]` je ekvivalentní výrazu `*(charPointer + i)`, a získáte stejný výsledek pomocí některé z dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f41d7-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 <span data-ttu-id="f41d7-111">**Velká písmena:**</span><span class="sxs-lookup"><span data-stu-id="f41d7-111">**Uppercase letters:**</span></span>  
<span data-ttu-id="f41d7-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="f41d7-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="f41d7-113">**Malá písmena:**</span><span class="sxs-lookup"><span data-stu-id="f41d7-113">**Lowercase letters:**</span></span>  
<span data-ttu-id="f41d7-114">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="f41d7-114">**abcdefghijklmnopqrstuvwxyz**</span></span>   
## <a name="see-also"></a><span data-ttu-id="f41d7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f41d7-115">See Also</span></span>  
 [<span data-ttu-id="f41d7-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f41d7-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f41d7-117">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f41d7-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="f41d7-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f41d7-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="f41d7-119">Typy</span><span class="sxs-lookup"><span data-stu-id="f41d7-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="f41d7-120">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="f41d7-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="f41d7-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f41d7-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="f41d7-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f41d7-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
