---
title: Klíčová slova C# dotazu – reference
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 3c08c2b6ecdaa4b875f118531e7e77f7164dd784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713154"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="1b5df-102">Klíčová slovaC# dotazu (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="1b5df-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="1b5df-103">Tato část obsahuje kontextová klíčová slova používaná ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="1b5df-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1b5df-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1b5df-104">In this section</span></span>

|<span data-ttu-id="1b5df-105">Klauzule</span><span class="sxs-lookup"><span data-stu-id="1b5df-105">Clause</span></span>|<span data-ttu-id="1b5df-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1b5df-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="1b5df-107">from</span><span class="sxs-lookup"><span data-stu-id="1b5df-107">from</span></span>](from-clause.md)|<span data-ttu-id="1b5df-108">Určuje zdroj dat a proměnnou rozsahu (podobně jako proměnná iterace).</span><span class="sxs-lookup"><span data-stu-id="1b5df-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="1b5df-109">,</span><span class="sxs-lookup"><span data-stu-id="1b5df-109">where</span></span>](where-clause.md)|<span data-ttu-id="1b5df-110">Filtruje zdrojové prvky založené na jednom nebo více logických výrazech oddělených logickými operátory AND a OR (`&&` nebo <code>&#124;&#124;</code>).</span><span class="sxs-lookup"><span data-stu-id="1b5df-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="1b5df-111">vybrali</span><span class="sxs-lookup"><span data-stu-id="1b5df-111">select</span></span>](select-clause.md)|<span data-ttu-id="1b5df-112">Určuje typ a tvar, který budou mít elementy v vrácené sekvenci při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="1b5df-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="1b5df-113">skupiny</span><span class="sxs-lookup"><span data-stu-id="1b5df-113">group</span></span>](group-clause.md)|<span data-ttu-id="1b5df-114">Seskupí výsledky dotazu podle zadané hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="1b5df-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="1b5df-115">into</span><span class="sxs-lookup"><span data-stu-id="1b5df-115">into</span></span>](into.md)|<span data-ttu-id="1b5df-116">Poskytuje identifikátor, který může sloužit jako odkaz na výsledky klauzule JOIN, Group nebo Select.</span><span class="sxs-lookup"><span data-stu-id="1b5df-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="1b5df-117">OrderBy</span><span class="sxs-lookup"><span data-stu-id="1b5df-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="1b5df-118">Seřadí výsledky dotazu ve vzestupném nebo sestupném pořadí podle výchozí porovnávací metody pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="1b5df-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="1b5df-119">join</span><span class="sxs-lookup"><span data-stu-id="1b5df-119">join</span></span>](join-clause.md)|<span data-ttu-id="1b5df-120">Spojí dva zdroje dat na základě porovnání rovnosti mezi dvěma zadanými kritérii porovnávání.</span><span class="sxs-lookup"><span data-stu-id="1b5df-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="1b5df-121">aplikaci</span><span class="sxs-lookup"><span data-stu-id="1b5df-121">let</span></span>](let-clause.md)|<span data-ttu-id="1b5df-122">Zavádí proměnnou rozsahu pro uložení výsledků dílčího výrazu ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="1b5df-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="1b5df-123">in</span><span class="sxs-lookup"><span data-stu-id="1b5df-123">in</span></span>](in.md)|<span data-ttu-id="1b5df-124">Kontextové klíčové slovo v klauzuli [Join](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="1b5df-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="1b5df-125">on</span><span class="sxs-lookup"><span data-stu-id="1b5df-125">on</span></span>](on.md)|<span data-ttu-id="1b5df-126">Kontextové klíčové slovo v klauzuli [Join](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="1b5df-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="1b5df-127">equals</span><span class="sxs-lookup"><span data-stu-id="1b5df-127">equals</span></span>](equals.md)|<span data-ttu-id="1b5df-128">Kontextové klíčové slovo v klauzuli [Join](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="1b5df-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="1b5df-129">by</span><span class="sxs-lookup"><span data-stu-id="1b5df-129">by</span></span>](by.md)|<span data-ttu-id="1b5df-130">Kontextové klíčové slovo v klauzuli [Group](group-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="1b5df-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="1b5df-131">ascending</span><span class="sxs-lookup"><span data-stu-id="1b5df-131">ascending</span></span>](ascending.md)|<span data-ttu-id="1b5df-132">Kontextové klíčové slovo v klauzuli [OrderBy](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="1b5df-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="1b5df-133">descending</span><span class="sxs-lookup"><span data-stu-id="1b5df-133">descending</span></span>](descending.md)|<span data-ttu-id="1b5df-134">Kontextové klíčové slovo v klauzuli [OrderBy](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="1b5df-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1b5df-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b5df-135">See also</span></span>

- [<span data-ttu-id="1b5df-136">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1b5df-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1b5df-137">LINQ (jazykově integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="1b5df-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="1b5df-138">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1b5df-138">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="1b5df-139">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1b5df-139">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
