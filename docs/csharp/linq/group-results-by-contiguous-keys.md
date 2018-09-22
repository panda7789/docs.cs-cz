---
title: Seskupení výsledků podle sousedních klíčů (LINQ v JAZYKU C#)
description: Jak seskupení výsledků podle sousedních klíčů pomocí jazyka LINQ v jazyce C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696950"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="b2f3b-103">Seskupení výsledků podle sousedních klíčů</span><span class="sxs-lookup"><span data-stu-id="b2f3b-103">Group results by contiguous keys</span></span>

<span data-ttu-id="b2f3b-104">Následující příklad ukazuje, jak seskupit elementy do bloků dat, které představují dílčích sekvencí, které ze sousedních klíčů.</span><span class="sxs-lookup"><span data-stu-id="b2f3b-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="b2f3b-105">Předpokládejme například, že budete mít k následujícímu pořadí páry klíč hodnota:</span><span class="sxs-lookup"><span data-stu-id="b2f3b-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="b2f3b-106">Key</span><span class="sxs-lookup"><span data-stu-id="b2f3b-106">Key</span></span>|<span data-ttu-id="b2f3b-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b2f3b-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="b2f3b-108">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="b2f3b-108">A</span></span>|<span data-ttu-id="b2f3b-109">Jsme</span><span class="sxs-lookup"><span data-stu-id="b2f3b-109">We</span></span>|
|<span data-ttu-id="b2f3b-110">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="b2f3b-110">A</span></span>|<span data-ttu-id="b2f3b-111">přemýšlení</span><span class="sxs-lookup"><span data-stu-id="b2f3b-111">think</span></span>|
|<span data-ttu-id="b2f3b-112">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="b2f3b-112">A</span></span>|<span data-ttu-id="b2f3b-113">který</span><span class="sxs-lookup"><span data-stu-id="b2f3b-113">that</span></span>|
|<span data-ttu-id="b2f3b-114">B</span><span class="sxs-lookup"><span data-stu-id="b2f3b-114">B</span></span>|<span data-ttu-id="b2f3b-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="b2f3b-115">Linq</span></span>|
|<span data-ttu-id="b2f3b-116">C</span><span class="sxs-lookup"><span data-stu-id="b2f3b-116">C</span></span>|<span data-ttu-id="b2f3b-117">is</span><span class="sxs-lookup"><span data-stu-id="b2f3b-117">is</span></span>|
|<span data-ttu-id="b2f3b-118">OBJEKT</span><span class="sxs-lookup"><span data-stu-id="b2f3b-118">A</span></span>|<span data-ttu-id="b2f3b-119">Vážně</span><span class="sxs-lookup"><span data-stu-id="b2f3b-119">really</span></span>|
|<span data-ttu-id="b2f3b-120">B</span><span class="sxs-lookup"><span data-stu-id="b2f3b-120">B</span></span>|<span data-ttu-id="b2f3b-121">Cool</span><span class="sxs-lookup"><span data-stu-id="b2f3b-121">cool</span></span>|
|<span data-ttu-id="b2f3b-122">B</span><span class="sxs-lookup"><span data-stu-id="b2f3b-122">B</span></span>|<span data-ttu-id="b2f3b-123">!</span><span class="sxs-lookup"><span data-stu-id="b2f3b-123">!</span></span>|

<span data-ttu-id="b2f3b-124">Tyto skupiny se vytvoří v tomto pořadí:</span><span class="sxs-lookup"><span data-stu-id="b2f3b-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="b2f3b-125">Myslíme si, že</span><span class="sxs-lookup"><span data-stu-id="b2f3b-125">We, think, that</span></span>

2. <span data-ttu-id="b2f3b-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="b2f3b-126">Linq</span></span>

3. <span data-ttu-id="b2f3b-127">is</span><span class="sxs-lookup"><span data-stu-id="b2f3b-127">is</span></span>

4. <span data-ttu-id="b2f3b-128">Vážně</span><span class="sxs-lookup"><span data-stu-id="b2f3b-128">really</span></span>

5. <span data-ttu-id="b2f3b-129">studené!</span><span class="sxs-lookup"><span data-stu-id="b2f3b-129">cool, !</span></span>

<span data-ttu-id="b2f3b-130">Toto řešení je implementované jako metodu rozšíření, které je bezpečné pro vlákna a, který vrátí výsledky v podobě datových proudů.</span><span class="sxs-lookup"><span data-stu-id="b2f3b-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="b2f3b-131">Jinými slovy vytvoří jeho skupiny při jejich přesunu přes zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="b2f3b-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="b2f3b-132">Na rozdíl od `group` nebo `orderby` operátory, ji můžete začít vracet skupiny volajícímu před všechny pořadí čtení.</span><span class="sxs-lookup"><span data-stu-id="b2f3b-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="b2f3b-133">Zabezpečení vlákna je možné díky kopii každého bloku nebo skupiny jako zdrojové sekvence je provést iteraci, jak je vysvětleno v komentářích zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="b2f3b-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="b2f3b-134">Pokud zdrojové sekvence má velký posloupnost položek souvislé, modul common language runtime může vyvolat <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="b2f3b-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="b2f3b-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2f3b-135">Example</span></span>

<span data-ttu-id="b2f3b-136">Následující příklad ukazuje metodu rozšíření a klientský kód, který se používá:</span><span class="sxs-lookup"><span data-stu-id="b2f3b-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="b2f3b-137">Chcete-li použít metodu rozšíření ve vašem projektu, zkopírujte `MyExtensions` statická třída pro nové nebo existující zdrojový soubor kódu a je-li vyžadován, přidejte `using` direktivu pro obor názvů, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="b2f3b-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2f3b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2f3b-138">See also</span></span>

- [<span data-ttu-id="b2f3b-139">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="b2f3b-139">Language Integrated Query (LINQ)</span></span>](index.md)
