---
title: Převody ukazatele (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322689"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="f3c5a-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f3c5a-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="f3c5a-103">V následující tabulce jsou uvedeny převody předdefinované implicitní ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f3c5a-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="f3c5a-104">Implicitní převody může dojít v mnoha situacích, včetně metoda vyvolání a přiřazení příkazy.</span><span class="sxs-lookup"><span data-stu-id="f3c5a-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="f3c5a-105">Převody implicitní ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="f3c5a-106">From</span><span class="sxs-lookup"><span data-stu-id="f3c5a-106">From</span></span>|<span data-ttu-id="f3c5a-107">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="f3c5a-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="f3c5a-108">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-108">Any pointer type</span></span>|<span data-ttu-id="f3c5a-109">void \*</span><span class="sxs-lookup"><span data-stu-id="f3c5a-109">void\*</span></span>|  
|<span data-ttu-id="f3c5a-110">null</span><span class="sxs-lookup"><span data-stu-id="f3c5a-110">null</span></span>|<span data-ttu-id="f3c5a-111">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="f3c5a-112">Ukazatel explicitní převod se používá k provádění převody, pro které není žádný implicitní převod pomocí výraz přetypování.</span><span class="sxs-lookup"><span data-stu-id="f3c5a-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="f3c5a-113">V následující tabulce jsou tyto převody.</span><span class="sxs-lookup"><span data-stu-id="f3c5a-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="f3c5a-114">Převody explicitní ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="f3c5a-115">From</span><span class="sxs-lookup"><span data-stu-id="f3c5a-115">From</span></span>|<span data-ttu-id="f3c5a-116">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="f3c5a-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="f3c5a-117">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-117">Any pointer type</span></span>|<span data-ttu-id="f3c5a-118">Jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-118">Any other pointer type</span></span>|  
|<span data-ttu-id="f3c5a-119">SByte –, bajtů, krátké, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="f3c5a-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="f3c5a-120">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-120">Any pointer type</span></span>|  
|<span data-ttu-id="f3c5a-121">Žádný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="f3c5a-121">Any pointer type</span></span>|<span data-ttu-id="f3c5a-122">SByte –, bajtů, krátké, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="f3c5a-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3c5a-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3c5a-123">Example</span></span>  
 <span data-ttu-id="f3c5a-124">V následujícím příkladu, ukazatel na `int` jsou převedeny na ukazatel na `byte`.</span><span class="sxs-lookup"><span data-stu-id="f3c5a-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="f3c5a-125">Všimněte si, že ukazatele odkazuje na nejnižší adresovaný bajtů proměnné.</span><span class="sxs-lookup"><span data-stu-id="f3c5a-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="f3c5a-126">Když postupně zvýší výsledek, až velikost `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="f3c5a-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f3c5a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3c5a-127">See Also</span></span>  
 [<span data-ttu-id="f3c5a-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f3c5a-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f3c5a-129">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f3c5a-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="f3c5a-130">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f3c5a-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="f3c5a-131">Typy</span><span class="sxs-lookup"><span data-stu-id="f3c5a-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="f3c5a-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="f3c5a-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="f3c5a-133">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f3c5a-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="f3c5a-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f3c5a-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
