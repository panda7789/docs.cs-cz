---
title: Převody ukazatele - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 3cef2f2d2af2d285504daea14aa57c55b9e9a21b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833463"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="71162-102">Převody ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="71162-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="71162-103">V následující tabulce jsou předdefinované ukazatel implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="71162-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="71162-104">Implicitní převod může dojít v mnoha situacích, včetně příkazů metody vyvolání a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="71162-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="71162-105">Implicitní ukazatel převody</span><span class="sxs-lookup"><span data-stu-id="71162-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="71162-106">From</span><span class="sxs-lookup"><span data-stu-id="71162-106">From</span></span>|<span data-ttu-id="71162-107">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="71162-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="71162-108">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="71162-108">Any pointer type</span></span>|<span data-ttu-id="71162-109">typ void \*</span><span class="sxs-lookup"><span data-stu-id="71162-109">void\*</span></span>|  
|<span data-ttu-id="71162-110">null</span><span class="sxs-lookup"><span data-stu-id="71162-110">null</span></span>|<span data-ttu-id="71162-111">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="71162-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="71162-112">Převod ukazatele explicitní slouží k provádění převodů, pro které neexistuje žádný implicitní převod, pomocí výrazu přetypování.</span><span class="sxs-lookup"><span data-stu-id="71162-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="71162-113">V následující tabulce jsou uvedeny tyto převody.</span><span class="sxs-lookup"><span data-stu-id="71162-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="71162-114">Převody ukazatele explicitní</span><span class="sxs-lookup"><span data-stu-id="71162-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="71162-115">From</span><span class="sxs-lookup"><span data-stu-id="71162-115">From</span></span>|<span data-ttu-id="71162-116">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="71162-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="71162-117">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="71162-117">Any pointer type</span></span>|<span data-ttu-id="71162-118">Jiný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="71162-118">Any other pointer type</span></span>|  
|<span data-ttu-id="71162-119">SByte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="71162-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="71162-120">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="71162-120">Any pointer type</span></span>|  
|<span data-ttu-id="71162-121">Libovolný typ ukazatele</span><span class="sxs-lookup"><span data-stu-id="71162-121">Any pointer type</span></span>|<span data-ttu-id="71162-122">SByte, byte, short, ushort, int, uint, long nebo ulong</span><span class="sxs-lookup"><span data-stu-id="71162-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="71162-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="71162-123">Example</span></span>  
 <span data-ttu-id="71162-124">V následujícím příkladu, ukazatel na `int` je převeden na ukazatel na `byte`.</span><span class="sxs-lookup"><span data-stu-id="71162-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="71162-125">Všimněte si, že ukazatel odkazuje na nejnižší adresovaný bajtů proměnné.</span><span class="sxs-lookup"><span data-stu-id="71162-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="71162-126">Když postupně zvyšovat výsledek, až do velikosti `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.</span><span class="sxs-lookup"><span data-stu-id="71162-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="71162-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71162-127">See also</span></span>

- [<span data-ttu-id="71162-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="71162-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="71162-129">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="71162-129">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="71162-130">Typy</span><span class="sxs-lookup"><span data-stu-id="71162-130">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="71162-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="71162-131">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="71162-132">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="71162-132">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="71162-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="71162-133">stackalloc</span></span>](../../../csharp/language-reference/operators/stackalloc.md)
