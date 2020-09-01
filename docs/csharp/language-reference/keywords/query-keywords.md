---
description: Klíčová slova dotazu – reference jazyka C#
title: Klíčová slova dotazu – reference jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 0beea8634d13222aa18f14d79fdbd95a35cc832e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137133"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="aa887-103">Klíčová slova dotazu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aa887-103">Query keywords (C# Reference)</span></span>

<span data-ttu-id="aa887-104">Tato část obsahuje kontextová klíčová slova používaná ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="aa887-104">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="aa887-105">V této části</span><span class="sxs-lookup"><span data-stu-id="aa887-105">In this section</span></span>

|<span data-ttu-id="aa887-106">Klauzule</span><span class="sxs-lookup"><span data-stu-id="aa887-106">Clause</span></span>|<span data-ttu-id="aa887-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aa887-107">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="aa887-108">Výsledkem</span><span class="sxs-lookup"><span data-stu-id="aa887-108">from</span></span>](from-clause.md)|<span data-ttu-id="aa887-109">Určuje zdroj dat a proměnnou rozsahu (podobně jako proměnná iterace).</span><span class="sxs-lookup"><span data-stu-id="aa887-109">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="aa887-110">,</span><span class="sxs-lookup"><span data-stu-id="aa887-110">where</span></span>](where-clause.md)|<span data-ttu-id="aa887-111">Filtruje zdrojové prvky na základě jednoho nebo více logických výrazů oddělených logickými operátory AND a OR ( `&&` nebo <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="aa887-111">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="aa887-112">vybrali</span><span class="sxs-lookup"><span data-stu-id="aa887-112">select</span></span>](select-clause.md)|<span data-ttu-id="aa887-113">Určuje typ a tvar, který budou mít elementy v vrácené sekvenci při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="aa887-113">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="aa887-114">skupina</span><span class="sxs-lookup"><span data-stu-id="aa887-114">group</span></span>](group-clause.md)|<span data-ttu-id="aa887-115">Seskupí výsledky dotazu podle zadané hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="aa887-115">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="aa887-116">uskladněn</span><span class="sxs-lookup"><span data-stu-id="aa887-116">into</span></span>](into.md)|<span data-ttu-id="aa887-117">Poskytuje identifikátor, který může sloužit jako odkaz na výsledky klauzule JOIN, Group nebo Select.</span><span class="sxs-lookup"><span data-stu-id="aa887-117">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="aa887-118">OrderBy</span><span class="sxs-lookup"><span data-stu-id="aa887-118">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="aa887-119">Seřadí výsledky dotazu ve vzestupném nebo sestupném pořadí podle výchozí porovnávací metody pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="aa887-119">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="aa887-120">zúčastnit</span><span class="sxs-lookup"><span data-stu-id="aa887-120">join</span></span>](join-clause.md)|<span data-ttu-id="aa887-121">Spojí dva zdroje dat na základě porovnání rovnosti mezi dvěma zadanými kritérii porovnávání.</span><span class="sxs-lookup"><span data-stu-id="aa887-121">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="aa887-122">aplikaci</span><span class="sxs-lookup"><span data-stu-id="aa887-122">let</span></span>](let-clause.md)|<span data-ttu-id="aa887-123">Zavádí proměnnou rozsahu pro uložení výsledků dílčího výrazu ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="aa887-123">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="aa887-124">pro</span><span class="sxs-lookup"><span data-stu-id="aa887-124">in</span></span>](in.md)|<span data-ttu-id="aa887-125">Kontextové klíčové slovo v klauzuli [Join](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="aa887-125">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="aa887-126">pnete</span><span class="sxs-lookup"><span data-stu-id="aa887-126">on</span></span>](on.md)|<span data-ttu-id="aa887-127">Kontextové klíčové slovo v klauzuli [Join](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="aa887-127">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="aa887-128">equals</span><span class="sxs-lookup"><span data-stu-id="aa887-128">equals</span></span>](equals.md)|<span data-ttu-id="aa887-129">Kontextové klíčové slovo v klauzuli [Join](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="aa887-129">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="aa887-130">by</span><span class="sxs-lookup"><span data-stu-id="aa887-130">by</span></span>](by.md)|<span data-ttu-id="aa887-131">Kontextové klíčové slovo v klauzuli [Group](group-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="aa887-131">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="aa887-132">ascending</span><span class="sxs-lookup"><span data-stu-id="aa887-132">ascending</span></span>](ascending.md)|<span data-ttu-id="aa887-133">Kontextové klíčové slovo v klauzuli [OrderBy](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="aa887-133">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="aa887-134">descending</span><span class="sxs-lookup"><span data-stu-id="aa887-134">descending</span></span>](descending.md)|<span data-ttu-id="aa887-135">Kontextové klíčové slovo v klauzuli [OrderBy](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="aa887-135">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="aa887-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa887-136">See also</span></span>

- [<span data-ttu-id="aa887-137">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aa887-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="aa887-138">LINQ (jazykově integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="aa887-138">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="aa887-139">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="aa887-139">LINQ in C#</span></span>](../../linq/index.md)
