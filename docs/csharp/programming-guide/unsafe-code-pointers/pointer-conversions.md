---
title: "Převody ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36589d139c91e04d9e3d8b31281a91c26b85a5d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="a1f55-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a1f55-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="a1f55-103">V následující tabulce jsou uvedeny převody předdefinované implicitní ukazatele.</span><span class="sxs-lookup"><span data-stu-id="a1f55-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="a1f55-104">Implicitní převody může dojít v mnoha situacích, včetně metoda vyvolání a přiřazení příkazy.</span><span class="sxs-lookup"><span data-stu-id="a1f55-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="a1f55-105">Převody implicitní ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="a1f55-106">From</span><span class="sxs-lookup"><span data-stu-id="a1f55-106">From</span></span>|<span data-ttu-id="a1f55-107">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="a1f55-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="a1f55-108">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-108">Any pointer type</span></span>|<span data-ttu-id="a1f55-109">void \*</span><span class="sxs-lookup"><span data-stu-id="a1f55-109">void\*</span></span>|  
|<span data-ttu-id="a1f55-110">null</span><span class="sxs-lookup"><span data-stu-id="a1f55-110">null</span></span>|<span data-ttu-id="a1f55-111">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="a1f55-112">Ukazatel explicitní převod se používá k provádění převody, pro které není žádný implicitní převod pomocí výraz přetypování.</span><span class="sxs-lookup"><span data-stu-id="a1f55-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="a1f55-113">V následující tabulce jsou tyto převody.</span><span class="sxs-lookup"><span data-stu-id="a1f55-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="a1f55-114">Převody explicitní ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="a1f55-115">From</span><span class="sxs-lookup"><span data-stu-id="a1f55-115">From</span></span>|<span data-ttu-id="a1f55-116">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="a1f55-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="a1f55-117">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-117">Any pointer type</span></span>|<span data-ttu-id="a1f55-118">Jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-118">Any other pointer type</span></span>|  
|<span data-ttu-id="a1f55-119">SByte –, bajtů, krátké, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="a1f55-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="a1f55-120">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-120">Any pointer type</span></span>|  
|<span data-ttu-id="a1f55-121">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="a1f55-121">Any pointer type</span></span>|<span data-ttu-id="a1f55-122">SByte –, bajtů, krátké, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="a1f55-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a1f55-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1f55-123">Example</span></span>  
 <span data-ttu-id="a1f55-124">V následujícím příkladu, ukazatel na `int` jsou převedeny na ukazatel na `byte`.</span><span class="sxs-lookup"><span data-stu-id="a1f55-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="a1f55-125">Všimněte si, že ukazatele odkazuje na nejnižší adresovaný bajtů proměnné.</span><span class="sxs-lookup"><span data-stu-id="a1f55-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="a1f55-126">Když postupně zvýší výsledek, až velikost `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="a1f55-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a1f55-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1f55-127">See Also</span></span>  
 [<span data-ttu-id="a1f55-128">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a1f55-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a1f55-129">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="a1f55-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="a1f55-130">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="a1f55-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="a1f55-131">Typy</span><span class="sxs-lookup"><span data-stu-id="a1f55-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="a1f55-132">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="a1f55-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="a1f55-133">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="a1f55-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="a1f55-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="a1f55-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
