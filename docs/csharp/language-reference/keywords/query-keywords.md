---
title: Klíčová slova dotazu – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 01134eda540c5141afbd11b2c89ff779da495a9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173520"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="2ab84-102">Klíčová slova dotazu (odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2ab84-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="2ab84-103">Tato část obsahuje kontextová klíčová slova používaná ve výrazech dotazu.</span><span class="sxs-lookup"><span data-stu-id="2ab84-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2ab84-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2ab84-104">In this section</span></span>

|<span data-ttu-id="2ab84-105">Klauzule</span><span class="sxs-lookup"><span data-stu-id="2ab84-105">Clause</span></span>|<span data-ttu-id="2ab84-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2ab84-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="2ab84-107">Z</span><span class="sxs-lookup"><span data-stu-id="2ab84-107">from</span></span>](from-clause.md)|<span data-ttu-id="2ab84-108">Určuje zdroj dat a proměnnou rozsahu (podobně jako iterace).</span><span class="sxs-lookup"><span data-stu-id="2ab84-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="2ab84-109">Kde</span><span class="sxs-lookup"><span data-stu-id="2ab84-109">where</span></span>](where-clause.md)|<span data-ttu-id="2ab84-110">Filtruje zdrojové prvky založené na jednom nebo více logických výrazech oddělených logickými operátory AND a OR ( `&&` nebo <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="2ab84-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="2ab84-111">Vyberte</span><span class="sxs-lookup"><span data-stu-id="2ab84-111">select</span></span>](select-clause.md)|<span data-ttu-id="2ab84-112">Určuje typ a obrazec, který budou mít prvky ve vrácené sekvenci při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="2ab84-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="2ab84-113">skupina</span><span class="sxs-lookup"><span data-stu-id="2ab84-113">group</span></span>](group-clause.md)|<span data-ttu-id="2ab84-114">Seskupí výsledky dotazu podle zadané hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="2ab84-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="2ab84-115">Do</span><span class="sxs-lookup"><span data-stu-id="2ab84-115">into</span></span>](into.md)|<span data-ttu-id="2ab84-116">Obsahuje identifikátor, který může sloužit jako odkaz na výsledky join, group nebo select klauzule.</span><span class="sxs-lookup"><span data-stu-id="2ab84-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="2ab84-117">Orderby</span><span class="sxs-lookup"><span data-stu-id="2ab84-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="2ab84-118">Seřadí výsledky dotazu vzestupně nebo sestupně na základě výchozího porovnávače pro typ prvku.</span><span class="sxs-lookup"><span data-stu-id="2ab84-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="2ab84-119">Připojit</span><span class="sxs-lookup"><span data-stu-id="2ab84-119">join</span></span>](join-clause.md)|<span data-ttu-id="2ab84-120">Spojuje dva zdroje dat na základě porovnání rovnosti mezi dvěma zadanými kritérii přiřazování.</span><span class="sxs-lookup"><span data-stu-id="2ab84-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="2ab84-121">Nechat</span><span class="sxs-lookup"><span data-stu-id="2ab84-121">let</span></span>](let-clause.md)|<span data-ttu-id="2ab84-122">Zavádí proměnnou rozsahu pro uložení výsledků dílčího výrazu do výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="2ab84-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="2ab84-123">In</span><span class="sxs-lookup"><span data-stu-id="2ab84-123">in</span></span>](in.md)|<span data-ttu-id="2ab84-124">Kontextové klíčové slovo v klauzuli [join.](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="2ab84-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="2ab84-125">Na</span><span class="sxs-lookup"><span data-stu-id="2ab84-125">on</span></span>](on.md)|<span data-ttu-id="2ab84-126">Kontextové klíčové slovo v klauzuli [join.](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="2ab84-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="2ab84-127">equals</span><span class="sxs-lookup"><span data-stu-id="2ab84-127">equals</span></span>](equals.md)|<span data-ttu-id="2ab84-128">Kontextové klíčové slovo v klauzuli [join.](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="2ab84-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="2ab84-129">podle</span><span class="sxs-lookup"><span data-stu-id="2ab84-129">by</span></span>](by.md)|<span data-ttu-id="2ab84-130">Kontextové klíčové slovo ve [skupinové](group-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2ab84-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="2ab84-131">ascending</span><span class="sxs-lookup"><span data-stu-id="2ab84-131">ascending</span></span>](ascending.md)|<span data-ttu-id="2ab84-132">Kontextové klíčové slovo v [klauzuli orderby.](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="2ab84-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="2ab84-133">descending</span><span class="sxs-lookup"><span data-stu-id="2ab84-133">descending</span></span>](descending.md)|<span data-ttu-id="2ab84-134">Kontextové klíčové slovo v [klauzuli orderby.](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="2ab84-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2ab84-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ab84-135">See also</span></span>

- [<span data-ttu-id="2ab84-136">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2ab84-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2ab84-137">LINQ (dotaz integrovaný jazykem)</span><span class="sxs-lookup"><span data-stu-id="2ab84-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="2ab84-138">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2ab84-138">LINQ in C#</span></span>](../../linq/index.md)
