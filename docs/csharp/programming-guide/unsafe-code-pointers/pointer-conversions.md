---
title: Převody ukazatele (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: db809fa9e086351184adcac43d67f53e9456894c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777381"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="b43d0-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b43d0-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="b43d0-103">V následující tabulce jsou předdefinované ukazatel implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="b43d0-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="b43d0-104">Implicitní převod může dojít v mnoha situacích, včetně příkazů metody vyvolání a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b43d0-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="b43d0-105">Implicitní ukazatel převody</span><span class="sxs-lookup"><span data-stu-id="b43d0-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="b43d0-106">From</span><span class="sxs-lookup"><span data-stu-id="b43d0-106">From</span></span>|<span data-ttu-id="b43d0-107">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="b43d0-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b43d0-108">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="b43d0-108">Any pointer type</span></span>|<span data-ttu-id="b43d0-109">typ void \*</span><span class="sxs-lookup"><span data-stu-id="b43d0-109">void\*</span></span>|  
|<span data-ttu-id="b43d0-110">null</span><span class="sxs-lookup"><span data-stu-id="b43d0-110">null</span></span>|<span data-ttu-id="b43d0-111">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="b43d0-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="b43d0-112">Převod ukazatele explicitní slouží k provádění převodů, pro které neexistuje žádný implicitní převod, pomocí výrazu přetypování.</span><span class="sxs-lookup"><span data-stu-id="b43d0-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="b43d0-113">V následující tabulce jsou uvedeny tyto převody.</span><span class="sxs-lookup"><span data-stu-id="b43d0-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="b43d0-114">Převody ukazatele explicitní</span><span class="sxs-lookup"><span data-stu-id="b43d0-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="b43d0-115">From</span><span class="sxs-lookup"><span data-stu-id="b43d0-115">From</span></span>|<span data-ttu-id="b43d0-116">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="b43d0-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b43d0-117">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="b43d0-117">Any pointer type</span></span>|<span data-ttu-id="b43d0-118">Jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="b43d0-118">Any other pointer type</span></span>|  
|<span data-ttu-id="b43d0-119">SByte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="b43d0-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="b43d0-120">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="b43d0-120">Any pointer type</span></span>|  
|<span data-ttu-id="b43d0-121">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="b43d0-121">Any pointer type</span></span>|<span data-ttu-id="b43d0-122">SByte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="b43d0-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b43d0-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="b43d0-123">Example</span></span>  
 <span data-ttu-id="b43d0-124">V následujícím příkladu, ukazatel na `int` je převeden na ukazatel na `byte`.</span><span class="sxs-lookup"><span data-stu-id="b43d0-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="b43d0-125">Všimněte si, že ukazatel odkazuje na nejnižší adresovaný bajtů proměnné.</span><span class="sxs-lookup"><span data-stu-id="b43d0-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="b43d0-126">Když postupně zvyšovat výsledek, až do velikosti `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="b43d0-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b43d0-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b43d0-127">See Also</span></span>

- [<span data-ttu-id="b43d0-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b43d0-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b43d0-129">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="b43d0-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="b43d0-130">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="b43d0-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="b43d0-131">Typy</span><span class="sxs-lookup"><span data-stu-id="b43d0-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="b43d0-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="b43d0-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="b43d0-133">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="b43d0-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="b43d0-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b43d0-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
