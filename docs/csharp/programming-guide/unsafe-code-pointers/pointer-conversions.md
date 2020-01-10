---
title: Převody ukazatelů – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 308d5e0646eeb94012dbe18d46d6d33f67dfeaf5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698362"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="3b219-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3b219-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="3b219-103">V následující tabulce jsou uvedeny předdefinované implicitní převody ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3b219-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="3b219-104">Implicitní převody mohou nastat v mnoha situacích, včetně vyvolání metody a příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3b219-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="3b219-105">Implicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="3b219-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="3b219-106">Od</span><span class="sxs-lookup"><span data-stu-id="3b219-106">From</span></span>|<span data-ttu-id="3b219-107">Pro</span><span class="sxs-lookup"><span data-stu-id="3b219-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="3b219-108">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="3b219-108">Any pointer type</span></span>|<span data-ttu-id="3b219-109">šekem</span><span class="sxs-lookup"><span data-stu-id="3b219-109">void\*</span></span>|  
|<span data-ttu-id="3b219-110">null</span><span class="sxs-lookup"><span data-stu-id="3b219-110">null</span></span>|<span data-ttu-id="3b219-111">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="3b219-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="3b219-112">Pro provedení převodů, pro které neexistuje implicitní převod, je použit explicitní převod ukazatele pomocí výrazu přetypování.</span><span class="sxs-lookup"><span data-stu-id="3b219-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="3b219-113">Tyto převody jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="3b219-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="3b219-114">Explicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="3b219-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="3b219-115">Od</span><span class="sxs-lookup"><span data-stu-id="3b219-115">From</span></span>|<span data-ttu-id="3b219-116">Pro</span><span class="sxs-lookup"><span data-stu-id="3b219-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="3b219-117">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="3b219-117">Any pointer type</span></span>|<span data-ttu-id="3b219-118">Jakýkoli jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="3b219-118">Any other pointer type</span></span>|  
|<span data-ttu-id="3b219-119">SByte, Byte, Short, UShort, int, uint, Long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="3b219-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="3b219-120">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="3b219-120">Any pointer type</span></span>|  
|<span data-ttu-id="3b219-121">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="3b219-121">Any pointer type</span></span>|<span data-ttu-id="3b219-122">SByte, Byte, Short, UShort, int, uint, Long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="3b219-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3b219-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b219-123">Example</span></span>  
 <span data-ttu-id="3b219-124">V následujícím příkladu je ukazatel na `int` převeden na ukazatel na `byte`.</span><span class="sxs-lookup"><span data-stu-id="3b219-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="3b219-125">Všimněte si, že ukazatel ukazuje na nejnižší adresovaný bajt proměnné.</span><span class="sxs-lookup"><span data-stu-id="3b219-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="3b219-126">Po úspěšném zvýšení výsledku až do velikosti `int` (4 bajty) můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="3b219-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3b219-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b219-127">See also</span></span>

- [<span data-ttu-id="3b219-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3b219-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b219-129">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="3b219-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="3b219-130">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="3b219-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="3b219-131">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="3b219-131">Value types</span></span>](../../language-reference/keywords/value-types.md)
- [<span data-ttu-id="3b219-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="3b219-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="3b219-133">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="3b219-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="3b219-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="3b219-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
