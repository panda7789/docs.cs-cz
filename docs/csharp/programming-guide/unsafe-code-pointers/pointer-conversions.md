---
title: Převody ukazatelů – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745360"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="84926-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="84926-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="84926-103">V následující tabulce jsou uvedeny předdefinované implicitní převody ukazatele.</span><span class="sxs-lookup"><span data-stu-id="84926-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="84926-104">Implicitní převody mohou nastat v mnoha situacích, včetně vyvolání metody a příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="84926-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="84926-105">Implicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="84926-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="84926-106">Od</span><span class="sxs-lookup"><span data-stu-id="84926-106">From</span></span>|<span data-ttu-id="84926-107">Pro</span><span class="sxs-lookup"><span data-stu-id="84926-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="84926-108">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="84926-108">Any pointer type</span></span>|<span data-ttu-id="84926-109">šekem</span><span class="sxs-lookup"><span data-stu-id="84926-109">void\*</span></span>|  
|<span data-ttu-id="84926-110">null</span><span class="sxs-lookup"><span data-stu-id="84926-110">null</span></span>|<span data-ttu-id="84926-111">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="84926-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="84926-112">Pro provedení převodů, pro které neexistuje implicitní převod, je použit explicitní převod ukazatele pomocí výrazu přetypování.</span><span class="sxs-lookup"><span data-stu-id="84926-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="84926-113">Tyto převody jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="84926-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="84926-114">Explicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="84926-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="84926-115">Od</span><span class="sxs-lookup"><span data-stu-id="84926-115">From</span></span>|<span data-ttu-id="84926-116">Pro</span><span class="sxs-lookup"><span data-stu-id="84926-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="84926-117">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="84926-117">Any pointer type</span></span>|<span data-ttu-id="84926-118">Jakýkoli jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="84926-118">Any other pointer type</span></span>|  
|<span data-ttu-id="84926-119">SByte, Byte, Short, UShort, int, uint, Long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="84926-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="84926-120">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="84926-120">Any pointer type</span></span>|  
|<span data-ttu-id="84926-121">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="84926-121">Any pointer type</span></span>|<span data-ttu-id="84926-122">SByte, Byte, Short, UShort, int, uint, Long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="84926-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="84926-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="84926-123">Example</span></span>  
 <span data-ttu-id="84926-124">V následujícím příkladu je ukazatel na `int` převeden na ukazatel na `byte`.</span><span class="sxs-lookup"><span data-stu-id="84926-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="84926-125">Všimněte si, že ukazatel ukazuje na nejnižší adresovaný bajt proměnné.</span><span class="sxs-lookup"><span data-stu-id="84926-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="84926-126">Po úspěšném zvýšení výsledku až do velikosti `int` (4 bajty) můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="84926-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="84926-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84926-127">See also</span></span>

- [<span data-ttu-id="84926-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="84926-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="84926-129">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="84926-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="84926-130">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="84926-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="84926-131">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="84926-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="84926-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="84926-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="84926-133">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="84926-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="84926-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="84926-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
