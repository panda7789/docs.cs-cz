---
title: Seskupit výsledky podle sousedících klíčů (LINQ v c#)
description: Jak seskupit výsledky podle sousedících klíčů pomocí LINQ v C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659901"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="de142-103">Seskupení výsledků podle sousedních klíčů</span><span class="sxs-lookup"><span data-stu-id="de142-103">Group results by contiguous keys</span></span>

<span data-ttu-id="de142-104">Následující příklad ukazuje, jak seskupit prvky do bloků, které představují dílčí sekvence souvislých klíčů.</span><span class="sxs-lookup"><span data-stu-id="de142-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="de142-105">Předpokládejme například, že jste dostali následující posloupnost párů klíč-hodnota:</span><span class="sxs-lookup"><span data-stu-id="de142-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="de142-106">Klíč</span><span class="sxs-lookup"><span data-stu-id="de142-106">Key</span></span>|<span data-ttu-id="de142-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="de142-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="de142-108">A</span><span class="sxs-lookup"><span data-stu-id="de142-108">A</span></span>|<span data-ttu-id="de142-109">Jsme</span><span class="sxs-lookup"><span data-stu-id="de142-109">We</span></span>|
|<span data-ttu-id="de142-110">A</span><span class="sxs-lookup"><span data-stu-id="de142-110">A</span></span>|<span data-ttu-id="de142-111">Myslet</span><span class="sxs-lookup"><span data-stu-id="de142-111">think</span></span>|
|<span data-ttu-id="de142-112">A</span><span class="sxs-lookup"><span data-stu-id="de142-112">A</span></span>|<span data-ttu-id="de142-113">Že</span><span class="sxs-lookup"><span data-stu-id="de142-113">that</span></span>|
|<span data-ttu-id="de142-114">B</span><span class="sxs-lookup"><span data-stu-id="de142-114">B</span></span>|<span data-ttu-id="de142-115">Linq</span><span class="sxs-lookup"><span data-stu-id="de142-115">Linq</span></span>|
|<span data-ttu-id="de142-116">C</span><span class="sxs-lookup"><span data-stu-id="de142-116">C</span></span>|<span data-ttu-id="de142-117">is</span><span class="sxs-lookup"><span data-stu-id="de142-117">is</span></span>|
|<span data-ttu-id="de142-118">A</span><span class="sxs-lookup"><span data-stu-id="de142-118">A</span></span>|<span data-ttu-id="de142-119">Vážně</span><span class="sxs-lookup"><span data-stu-id="de142-119">really</span></span>|
|<span data-ttu-id="de142-120">B</span><span class="sxs-lookup"><span data-stu-id="de142-120">B</span></span>|<span data-ttu-id="de142-121">Cool</span><span class="sxs-lookup"><span data-stu-id="de142-121">cool</span></span>|
|<span data-ttu-id="de142-122">B</span><span class="sxs-lookup"><span data-stu-id="de142-122">B</span></span>|<span data-ttu-id="de142-123">!</span><span class="sxs-lookup"><span data-stu-id="de142-123">!</span></span>|

<span data-ttu-id="de142-124">V tomto pořadí budou vytvořeny následující skupiny:</span><span class="sxs-lookup"><span data-stu-id="de142-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="de142-125">My, myslím, že</span><span class="sxs-lookup"><span data-stu-id="de142-125">We, think, that</span></span>

2. <span data-ttu-id="de142-126">Linq</span><span class="sxs-lookup"><span data-stu-id="de142-126">Linq</span></span>

3. <span data-ttu-id="de142-127">is</span><span class="sxs-lookup"><span data-stu-id="de142-127">is</span></span>

4. <span data-ttu-id="de142-128">Vážně</span><span class="sxs-lookup"><span data-stu-id="de142-128">really</span></span>

5. <span data-ttu-id="de142-129">Cool!</span><span class="sxs-lookup"><span data-stu-id="de142-129">cool, !</span></span>

<span data-ttu-id="de142-130">Řešení je implementováno jako metoda rozšíření, která je bezpečná pro přístup z více vláken a která vrací jeho výsledky způsobem streamování.</span><span class="sxs-lookup"><span data-stu-id="de142-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="de142-131">Jinými slovy vytváří své skupiny, když se pohybuje přes zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="de142-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="de142-132">Na `group` rozdíl `orderby` od operátory nebo může začít vracet skupiny volajícímu před všechny sekvence byla přečtena.</span><span class="sxs-lookup"><span data-stu-id="de142-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="de142-133">Bezpečnost podprocesu se provádí vytvořením kopie každé skupiny nebo bloku, protože zdrojová sekvence je iterována, jak je vysvětleno v komentářích zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="de142-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="de142-134">Pokud má zdrojová sekvence velkou posloupnost sousedících položek, může <xref:System.OutOfMemoryException>běžný jazyk vyvolat .</span><span class="sxs-lookup"><span data-stu-id="de142-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="de142-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="de142-135">Example</span></span>

<span data-ttu-id="de142-136">Následující příklad ukazuje metodu rozšíření i kód klienta, který ji používá:</span><span class="sxs-lookup"><span data-stu-id="de142-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="de142-137">Chcete-li použít metodu rozšíření `MyExtensions` v projektu, zkopírujte statickou třídu do nového `using` nebo existujícího souboru zdrojového kódu a pokud je požadováno, přidejte direktivu pro obor názvů, kde je umístěn.</span><span class="sxs-lookup"><span data-stu-id="de142-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="de142-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="de142-138">See also</span></span>

- [<span data-ttu-id="de142-139">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="de142-139">Language Integrated Query (LINQ)</span></span>](index.md)
