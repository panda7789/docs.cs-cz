---
title: 'Postupy: přístup k elementu pole pomocí ukazatele - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 7b2991776ca032aa53111187a061835725cfe223
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965602"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="f9d2b-102">Postupy: přístup k elementu pole pomocí ukazatele (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f9d2b-102">How to: access an array element with a pointer (C# Programming Guide)</span></span>

<span data-ttu-id="f9d2b-103">V nezabezpečeném kontextu můžete přístup k prvku v paměti pomocí přístup k prvkům ukazatele, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f9d2b-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

<span data-ttu-id="f9d2b-104">Výraz v hranatých závorkách musí být implicitně převeditelný na `int`, `uint`, `long`, nebo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f9d2b-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="f9d2b-105">Operace `p[e]` je ekvivalentní `*(p+e)`.</span><span class="sxs-lookup"><span data-stu-id="f9d2b-105">The operation `p[e]` is equivalent to `*(p+e)`.</span></span> <span data-ttu-id="f9d2b-106">Podobně jako C a C++, přístup k prvkům ukazatel nekontroluje celočíselných chyby.</span><span class="sxs-lookup"><span data-stu-id="f9d2b-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>

## <a name="example"></a><span data-ttu-id="f9d2b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9d2b-107">Example</span></span>

<span data-ttu-id="f9d2b-108">V tomto příkladu jsou 123 umístění v paměti přidělené na pole znaků `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="f9d2b-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="f9d2b-109">Pole se používá k zobrazení písmena malá a velká písmena ve dvou [pro](../../../csharp/language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="f9d2b-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>

<span data-ttu-id="f9d2b-110">Všimněte si, že výraz `charPointer[i]` je ekvivalentní výraz `*(charPointer + i)`, a získáte stejný výsledek jedním ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f9d2b-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>

 [!code-csharp[csProgGuidePointers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#11)]

 [!code-csharp[csProgGuidePointers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#12)]

<span data-ttu-id="f9d2b-111">**Velká písmena:**</span><span class="sxs-lookup"><span data-stu-id="f9d2b-111">**Uppercase letters:**</span></span>  
<span data-ttu-id="f9d2b-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="f9d2b-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="f9d2b-113">**Malá písmena:**</span><span class="sxs-lookup"><span data-stu-id="f9d2b-113">**Lowercase letters:**</span></span>  
<span data-ttu-id="f9d2b-114">**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="f9d2b-114">**abcdefghijklmnopqrstuvwxyz**</span></span>  

## <a name="see-also"></a><span data-ttu-id="f9d2b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9d2b-115">See also</span></span>

- [<span data-ttu-id="f9d2b-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f9d2b-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f9d2b-117">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f9d2b-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="f9d2b-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f9d2b-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f9d2b-119">Typy</span><span class="sxs-lookup"><span data-stu-id="f9d2b-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="f9d2b-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="f9d2b-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="f9d2b-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f9d2b-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="f9d2b-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f9d2b-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
