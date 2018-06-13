---
title: Seskupení výsledků podle sousedních klíčů
description: Jak seskupení výsledků podle sousedních klíčů.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281434"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="48556-103">Seskupení výsledků podle sousedních klíčů</span><span class="sxs-lookup"><span data-stu-id="48556-103">Group results by contiguous keys</span></span>

<span data-ttu-id="48556-104">Následující příklad ukazuje, jak k seskupení prvků do bloků, které představují dílčích sekvencí sousedních klíčů.</span><span class="sxs-lookup"><span data-stu-id="48556-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="48556-105">Předpokládejme například, že budete mít k následujícímu pořadí páry klíč hodnota:</span><span class="sxs-lookup"><span data-stu-id="48556-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="48556-106">Key</span><span class="sxs-lookup"><span data-stu-id="48556-106">Key</span></span>|<span data-ttu-id="48556-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="48556-107">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="48556-108">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="48556-108">A</span></span>|<span data-ttu-id="48556-109">Jsme</span><span class="sxs-lookup"><span data-stu-id="48556-109">We</span></span>|  
|<span data-ttu-id="48556-110">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="48556-110">A</span></span>|<span data-ttu-id="48556-111">Vezměte v úvahu</span><span class="sxs-lookup"><span data-stu-id="48556-111">think</span></span>|  
|<span data-ttu-id="48556-112">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="48556-112">A</span></span>|<span data-ttu-id="48556-113">který</span><span class="sxs-lookup"><span data-stu-id="48556-113">that</span></span>|  
|<span data-ttu-id="48556-114">B</span><span class="sxs-lookup"><span data-stu-id="48556-114">B</span></span>|<span data-ttu-id="48556-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="48556-115">Linq</span></span>|  
|<span data-ttu-id="48556-116">C</span><span class="sxs-lookup"><span data-stu-id="48556-116">C</span></span>|<span data-ttu-id="48556-117">is</span><span class="sxs-lookup"><span data-stu-id="48556-117">is</span></span>|  
|<span data-ttu-id="48556-118">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="48556-118">A</span></span>|<span data-ttu-id="48556-119">Vážně</span><span class="sxs-lookup"><span data-stu-id="48556-119">really</span></span>|  
|<span data-ttu-id="48556-120">B</span><span class="sxs-lookup"><span data-stu-id="48556-120">B</span></span>|<span data-ttu-id="48556-121">Cool</span><span class="sxs-lookup"><span data-stu-id="48556-121">cool</span></span>|  
|<span data-ttu-id="48556-122">B</span><span class="sxs-lookup"><span data-stu-id="48556-122">B</span></span>|<span data-ttu-id="48556-123">!</span><span class="sxs-lookup"><span data-stu-id="48556-123">!</span></span>|  
  
 <span data-ttu-id="48556-124">Tyto skupiny se vytvoří v tomto pořadí:</span><span class="sxs-lookup"><span data-stu-id="48556-124">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="48556-125">Myslíme, který</span><span class="sxs-lookup"><span data-stu-id="48556-125">We, think, that</span></span>  
  
2.  <span data-ttu-id="48556-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="48556-126">Linq</span></span>  
  
3.  <span data-ttu-id="48556-127">is</span><span class="sxs-lookup"><span data-stu-id="48556-127">is</span></span>  
  
4.  <span data-ttu-id="48556-128">Vážně</span><span class="sxs-lookup"><span data-stu-id="48556-128">really</span></span>  
  
5.  <span data-ttu-id="48556-129">nástrojů!</span><span class="sxs-lookup"><span data-stu-id="48556-129">cool, !</span></span>  
  
 <span data-ttu-id="48556-130">Řešení je implementovaný jako metody rozšíření, který je bezpečný pro přístup z více vláken a která vrací své výsledky streamování způsobem.</span><span class="sxs-lookup"><span data-stu-id="48556-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="48556-131">Jinými slovy jeho skupiny vyvolá při jejich přesunu prostřednictvím zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="48556-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="48556-132">Na rozdíl od `group` nebo `orderby` operátory, ho můžete začít vracet skupiny volajícímu před všechny pořadí byl načten.</span><span class="sxs-lookup"><span data-stu-id="48556-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="48556-133">Zabezpečení vlákna dosahuje tím, že kopii každého bloku nebo skupiny je vstupní zdroj pořadí, jak je popsáno v komentáře zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="48556-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="48556-134">Pokud zdrojové sekvence velké posloupnost souvislý položek, může vyvolat modul common language runtime <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="48556-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48556-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="48556-135">Example</span></span>  
 <span data-ttu-id="48556-136">Následující příklad ukazuje metodu rozšíření a kód klienta, která jej používá.</span><span class="sxs-lookup"><span data-stu-id="48556-136">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 <span data-ttu-id="48556-137">Chcete-li použít metodu rozšíření v projektu, zkopírujte `MyExtensions` statická třída pro nové nebo existující zdrojový kód soubor a pokud je vyžadována, přidejte `using` direktivy pro obor názvů, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="48556-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48556-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="48556-138">See also</span></span>  
 [<span data-ttu-id="48556-139">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="48556-139">LINQ Query Expressions</span></span>](index.md)  
 
