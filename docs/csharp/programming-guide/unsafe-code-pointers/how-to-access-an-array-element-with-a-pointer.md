---
title: Jak přistupovat k elementu pole pomocí ukazatele - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 4f5d82e0ccdffcb694e3030aabe58b8da687a5e1
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084794"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="145d2-102">Jak přistupovat k elementu pole pomocí ukazatele (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="145d2-102">How to access an array element with a pointer (C# Programming Guide)</span></span>

<span data-ttu-id="145d2-103">V nezabezpečeném kontextu můžete přístup k prvku v paměti pomocí přístup k prvkům ukazatele, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="145d2-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

<span data-ttu-id="145d2-104">Výraz v hranatých závorkách musí být implicitně převeditelný na `int`, `uint`, `long`, nebo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="145d2-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="145d2-105">Operace `p[e]` je ekvivalentní `*(p+e)`.</span><span class="sxs-lookup"><span data-stu-id="145d2-105">The operation `p[e]` is equivalent to `*(p+e)`.</span></span> <span data-ttu-id="145d2-106">Podobně jako C a C++, přístup k prvkům ukazatel nekontroluje celočíselných chyby.</span><span class="sxs-lookup"><span data-stu-id="145d2-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>

## <a name="example"></a><span data-ttu-id="145d2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="145d2-107">Example</span></span>

<span data-ttu-id="145d2-108">V tomto příkladu jsou 123 umístění v paměti přidělené na pole znaků `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="145d2-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="145d2-109">Pole se používá k zobrazení písmena malá a velká písmena ve dvou [pro](../../../csharp/language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="145d2-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>

<span data-ttu-id="145d2-110">Všimněte si, že výraz `charPointer[i]` je ekvivalentní výraz `*(charPointer + i)`, a získáte stejný výsledek jedním ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="145d2-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

<span data-ttu-id="145d2-111">**Velká písmena:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**malá písmena:**
**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="145d2-111">**Uppercase letters:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**Lowercase letters:**
**abcdefghijklmnopqrstuvwxyz**</span></span>

## <a name="see-also"></a><span data-ttu-id="145d2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="145d2-112">See also</span></span>

- [<span data-ttu-id="145d2-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="145d2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="145d2-114">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="145d2-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="145d2-115">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="145d2-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="145d2-116">Typy</span><span class="sxs-lookup"><span data-stu-id="145d2-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="145d2-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="145d2-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="145d2-118">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="145d2-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="145d2-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="145d2-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
