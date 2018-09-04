---
title: Převody ukazatele (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: db809fa9e086351184adcac43d67f53e9456894c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554132"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="6e479-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6e479-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="6e479-103">V následující tabulce jsou předdefinované ukazatel implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="6e479-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="6e479-104">Implicitní převod může dojít v mnoha situacích, včetně příkazů metody vyvolání a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="6e479-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="6e479-105">Implicitní ukazatel převody</span><span class="sxs-lookup"><span data-stu-id="6e479-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="6e479-106">From</span><span class="sxs-lookup"><span data-stu-id="6e479-106">From</span></span>|<span data-ttu-id="6e479-107">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="6e479-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="6e479-108">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="6e479-108">Any pointer type</span></span>|<span data-ttu-id="6e479-109">typ void \*</span><span class="sxs-lookup"><span data-stu-id="6e479-109">void\*</span></span>|  
|<span data-ttu-id="6e479-110">null</span><span class="sxs-lookup"><span data-stu-id="6e479-110">null</span></span>|<span data-ttu-id="6e479-111">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="6e479-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="6e479-112">Převod ukazatele explicitní slouží k provádění převodů, pro které neexistuje žádný implicitní převod, pomocí výrazu přetypování.</span><span class="sxs-lookup"><span data-stu-id="6e479-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="6e479-113">V následující tabulce jsou uvedeny tyto převody.</span><span class="sxs-lookup"><span data-stu-id="6e479-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="6e479-114">Převody ukazatele explicitní</span><span class="sxs-lookup"><span data-stu-id="6e479-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="6e479-115">From</span><span class="sxs-lookup"><span data-stu-id="6e479-115">From</span></span>|<span data-ttu-id="6e479-116">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="6e479-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="6e479-117">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="6e479-117">Any pointer type</span></span>|<span data-ttu-id="6e479-118">Jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="6e479-118">Any other pointer type</span></span>|  
|<span data-ttu-id="6e479-119">SByte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="6e479-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="6e479-120">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="6e479-120">Any pointer type</span></span>|  
|<span data-ttu-id="6e479-121">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="6e479-121">Any pointer type</span></span>|<span data-ttu-id="6e479-122">SByte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="6e479-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6e479-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e479-123">Example</span></span>  
 <span data-ttu-id="6e479-124">V následujícím příkladu, ukazatel na `int` je převeden na ukazatel na `byte`.</span><span class="sxs-lookup"><span data-stu-id="6e479-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="6e479-125">Všimněte si, že ukazatel odkazuje na nejnižší adresovaný bajtů proměnné.</span><span class="sxs-lookup"><span data-stu-id="6e479-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="6e479-126">Když postupně zvyšovat výsledek, až do velikosti `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="6e479-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6e479-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e479-127">See Also</span></span>

- [<span data-ttu-id="6e479-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6e479-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6e479-129">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="6e479-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="6e479-130">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="6e479-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="6e479-131">Typy</span><span class="sxs-lookup"><span data-stu-id="6e479-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="6e479-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="6e479-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="6e479-133">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="6e479-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="6e479-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="6e479-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
