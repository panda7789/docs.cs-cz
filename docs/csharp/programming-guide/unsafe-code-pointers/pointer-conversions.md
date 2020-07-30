---
title: Převody ukazatelů – Průvodce programováním v C#
description: Přečtěte si o převodech ukazatelů. Podívejte se na tabulky implicitních a explicitních převodů ukazatelů, příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: c39be5cb52964abbea5bc5636c6fa74d8411a331
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382084"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="1759b-104">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1759b-104">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="1759b-105">V následující tabulce jsou uvedeny předdefinované implicitní převody ukazatele.</span><span class="sxs-lookup"><span data-stu-id="1759b-105">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="1759b-106">Implicitní převody mohou nastat v mnoha situacích, včetně vyvolání metody a příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1759b-106">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="1759b-107">Implicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="1759b-107">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="1759b-108">Z</span><span class="sxs-lookup"><span data-stu-id="1759b-108">From</span></span>|<span data-ttu-id="1759b-109">Záměr</span><span class="sxs-lookup"><span data-stu-id="1759b-109">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="1759b-110">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="1759b-110">Any pointer type</span></span>|<span data-ttu-id="1759b-111">šekem</span><span class="sxs-lookup"><span data-stu-id="1759b-111">void\*</span></span>|  
|<span data-ttu-id="1759b-112">null</span><span class="sxs-lookup"><span data-stu-id="1759b-112">null</span></span>|<span data-ttu-id="1759b-113">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="1759b-113">Any pointer type</span></span>|  
  
 <span data-ttu-id="1759b-114">Pro provedení převodů, pro které neexistuje implicitní převod, je použit explicitní převod ukazatele pomocí výrazu přetypování.</span><span class="sxs-lookup"><span data-stu-id="1759b-114">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="1759b-115">Tyto převody jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1759b-115">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="1759b-116">Explicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="1759b-116">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="1759b-117">Z</span><span class="sxs-lookup"><span data-stu-id="1759b-117">From</span></span>|<span data-ttu-id="1759b-118">Záměr</span><span class="sxs-lookup"><span data-stu-id="1759b-118">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="1759b-119">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="1759b-119">Any pointer type</span></span>|<span data-ttu-id="1759b-120">Jakýkoli jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="1759b-120">Any other pointer type</span></span>|  
|<span data-ttu-id="1759b-121">SByte, Byte, Short, UShort, int, uint, Long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="1759b-121">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="1759b-122">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="1759b-122">Any pointer type</span></span>|  
|<span data-ttu-id="1759b-123">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="1759b-123">Any pointer type</span></span>|<span data-ttu-id="1759b-124">SByte, Byte, Short, UShort, int, uint, Long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="1759b-124">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1759b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="1759b-125">Example</span></span>  
 <span data-ttu-id="1759b-126">V následujícím příkladu je ukazatel na `int` převedený na ukazatel na `byte` .</span><span class="sxs-lookup"><span data-stu-id="1759b-126">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="1759b-127">Všimněte si, že ukazatel ukazuje na nejnižší adresovaný bajt proměnné.</span><span class="sxs-lookup"><span data-stu-id="1759b-127">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="1759b-128">Po úspěšném zvýšení výsledku až do velikosti `int` (4 bajty) můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="1759b-128">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1759b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1759b-129">See also</span></span>

- [<span data-ttu-id="1759b-130">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1759b-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1759b-131">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="1759b-131">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="1759b-132">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="1759b-132">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="1759b-133">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="1759b-133">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="1759b-134">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="1759b-134">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="1759b-135">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="1759b-135">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="1759b-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="1759b-136">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
