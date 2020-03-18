---
title: Převody ukazatelů – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745360"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="d609b-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d609b-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="d609b-103">V následující tabulce jsou uvedeny předdefinované implicitní převody ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="d609b-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="d609b-104">Implicitní převody může dojít v mnoha situacích, včetně metody vyvolání a přiřazení příkazy.</span><span class="sxs-lookup"><span data-stu-id="d609b-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="d609b-105">Implicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d609b-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="d609b-106">From</span><span class="sxs-lookup"><span data-stu-id="d609b-106">From</span></span>|<span data-ttu-id="d609b-107">Akce</span><span class="sxs-lookup"><span data-stu-id="d609b-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="d609b-108">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="d609b-108">Any pointer type</span></span>|<span data-ttu-id="d609b-109">void\*</span><span class="sxs-lookup"><span data-stu-id="d609b-109">void\*</span></span>|  
|<span data-ttu-id="d609b-110">null</span><span class="sxs-lookup"><span data-stu-id="d609b-110">null</span></span>|<span data-ttu-id="d609b-111">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="d609b-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="d609b-112">Explicitní převod ukazatele se používá k provádění převodů, pro které neexistuje žádný implicitní převod, pomocí výrazu přetypování.</span><span class="sxs-lookup"><span data-stu-id="d609b-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="d609b-113">Následující tabulka ukazuje tyto převody.</span><span class="sxs-lookup"><span data-stu-id="d609b-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="d609b-114">Explicitní převody ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d609b-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="d609b-115">From</span><span class="sxs-lookup"><span data-stu-id="d609b-115">From</span></span>|<span data-ttu-id="d609b-116">Akce</span><span class="sxs-lookup"><span data-stu-id="d609b-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="d609b-117">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="d609b-117">Any pointer type</span></span>|<span data-ttu-id="d609b-118">Jakýkoli jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="d609b-118">Any other pointer type</span></span>|  
|<span data-ttu-id="d609b-119">sbyte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="d609b-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="d609b-120">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="d609b-120">Any pointer type</span></span>|  
|<span data-ttu-id="d609b-121">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="d609b-121">Any pointer type</span></span>|<span data-ttu-id="d609b-122">sbyte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="d609b-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d609b-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d609b-123">Example</span></span>  
 <span data-ttu-id="d609b-124">V následujícím příkladu je `int` ukazatel na převést `byte`na ukazatel na .</span><span class="sxs-lookup"><span data-stu-id="d609b-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="d609b-125">Všimněte si, že ukazatel odkazuje na nejnižší adresovaný bajt proměnné.</span><span class="sxs-lookup"><span data-stu-id="d609b-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="d609b-126">Když postupně zvětšujete výsledek až `int` do velikosti (4 bajty), můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="d609b-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d609b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d609b-127">See also</span></span>

- [<span data-ttu-id="d609b-128">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d609b-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d609b-129">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d609b-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="d609b-130">Referenční typy</span><span class="sxs-lookup"><span data-stu-id="d609b-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="d609b-131">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="d609b-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="d609b-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="d609b-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="d609b-133">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="d609b-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="d609b-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="d609b-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
