---
title: LINQ a řetězce (C#)
description: LINQ může zadávat dotazy a transformovat řetězce a kolekce řetězců. Dotazy LINQ můžete kombinovat s řetězcovými funkcemi C# a regulárními výrazy.
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c515a0c56ad6473f93c6339540e4ed0245bb5bd2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165618"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="2a043-104">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-104">LINQ and strings (C#)</span></span>

<span data-ttu-id="2a043-105">LINQ lze použít k dotazování a transformaci řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="2a043-105">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="2a043-106">Může být obzvláště užitečná pro částečně strukturovaná data v textových souborech.</span><span class="sxs-lookup"><span data-stu-id="2a043-106">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="2a043-107">Dotazy LINQ lze kombinovat s tradičními řetězcovými funkcemi a regulárními výrazy.</span><span class="sxs-lookup"><span data-stu-id="2a043-107">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="2a043-108">Například můžete použít <xref:System.String.Split%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metodu nebo k vytvoření pole řetězců, které můžete následně dotazovat nebo upravit pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="2a043-108">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="2a043-109">Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metodu v `where` klauzuli dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="2a043-109">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="2a043-110">A můžete použít LINQ k dotazování nebo úpravám <xref:System.Text.RegularExpressions.MatchCollection> výsledků vrácených regulárním výrazem.</span><span class="sxs-lookup"><span data-stu-id="2a043-110">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="2a043-111">Pomocí technik popsaných v této části můžete také transformovat částečně strukturovaná textová data do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="2a043-111">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="2a043-112">Další informace najdete v tématu [generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="2a043-112">For more information, see [How to generate XML from CSV files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="2a043-113">Příklady v této části spadají do dvou kategorií:</span><span class="sxs-lookup"><span data-stu-id="2a043-113">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="2a043-114">Dotazování na blok textu</span><span class="sxs-lookup"><span data-stu-id="2a043-114">Querying a block of text</span></span>

<span data-ttu-id="2a043-115">Můžete zadávat dotazy, analyzovat a upravovat textové bloky jejich rozdělením do pole Queryable menších řetězců pomocí <xref:System.String.Split%2A?displayProperty=nameWithType> metody nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2a043-115">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2a043-116">Zdrojový text můžete rozdělit na slova, věty, odstavce, stránky nebo jakákoli další kritéria a pak provést další rozdělení, pokud jsou v dotazu potřeba.</span><span class="sxs-lookup"><span data-stu-id="2a043-116">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="2a043-117">Jak spočítat výskyty slova v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-117">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="2a043-118">Ukazuje, jak použít LINQ pro jednoduché dotazování nad textem.</span><span class="sxs-lookup"><span data-stu-id="2a043-118">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="2a043-119">Dotazování na věty, které obsahují zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-119">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="2a043-120">Ukazuje, jak rozdělit textové soubory na libovolné hranice a jak provádět dotazy proti každé části.</span><span class="sxs-lookup"><span data-stu-id="2a043-120">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="2a043-121">Dotazování na znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-121">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="2a043-122">Ukazuje, že řetězec je typu Queryable.</span><span class="sxs-lookup"><span data-stu-id="2a043-122">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="2a043-123">Jak kombinovat dotazy LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-123">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="2a043-124">Ukazuje, jak použít regulární výrazy v dotazech LINQ pro komplexní porovnávání vzorů u filtrovaných výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="2a043-124">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="2a043-125">Dotazování na částečně strukturovaná data ve formátu textu</span><span class="sxs-lookup"><span data-stu-id="2a043-125">Querying semi-structured data in text format</span></span>

<span data-ttu-id="2a043-126">Mnoho různých typů textových souborů se skládá z řady řádků, často s podobným formátováním, jako jsou například tabulátory nebo soubory oddělené čárkami nebo řádky s pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="2a043-126">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="2a043-127">Po přečtení takového textového souboru do paměti můžete použít LINQ k dotazování a úpravě řádků.</span><span class="sxs-lookup"><span data-stu-id="2a043-127">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="2a043-128">Dotazy LINQ také zjednodušují úlohu kombinování dat z více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="2a043-128">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="2a043-129">Jak najít množinu rozdílů mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-129">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="2a043-130">Ukazuje, jak najít všechny řetězce, které jsou k dispozici v jednom seznamu, ale nikoli druhý.</span><span class="sxs-lookup"><span data-stu-id="2a043-130">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="2a043-131">Postup řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-131">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="2a043-132">Ukazuje, jak seřadit řádky textu založené na jakémkoli slově nebo poli.</span><span class="sxs-lookup"><span data-stu-id="2a043-132">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="2a043-133">Změna pořadí polí souboru s oddělovači (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-133">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="2a043-134">Ukazuje, jak změnit pořadí polí v řádku v souboru. csv.</span><span class="sxs-lookup"><span data-stu-id="2a043-134">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="2a043-135">Postup kombinování a porovnávání kolekcí řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-135">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="2a043-136">Ukazuje, jak kombinovat seznamy řetězců různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="2a043-136">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="2a043-137">Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="2a043-138">Ukazuje, jak vytvořit kolekce objektů pomocí více textových souborů jako zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="2a043-138">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="2a043-139">Postup připojení obsahu z nepodobných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-139">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="2a043-140">Ukazuje, jak kombinovat řetězce ve dvou seznamech do jednoho řetězce pomocí odpovídajícího klíče.</span><span class="sxs-lookup"><span data-stu-id="2a043-140">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="2a043-141">Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-141">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="2a043-142">Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2a043-142">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="2a043-143">Jak vypočítat hodnoty sloupce v textovém souboru CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-143">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="2a043-144">Ukazuje, jak provádět matematické výpočty s textovými daty v souborech. csv.</span><span class="sxs-lookup"><span data-stu-id="2a043-144">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a043-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a043-145">See also</span></span>

- [<span data-ttu-id="2a043-146">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a043-146">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="2a043-147">Jak generovat XML ze souborů CSV</span><span class="sxs-lookup"><span data-stu-id="2a043-147">How to generate XML from CSV files</span></span>](how-to-generate-xml-from-csv-files.md)
