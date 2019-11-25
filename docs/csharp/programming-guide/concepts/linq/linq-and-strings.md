---
title: LINQ a řetězce (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: fb1714c54331ead80cd28435cf3ed1c4c54a704e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140898"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="ef383-102">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="ef383-103">LINQ lze použít k dotazování a transformaci řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="ef383-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="ef383-104">Může být obzvláště užitečná pro částečně strukturovaná data v textových souborech.</span><span class="sxs-lookup"><span data-stu-id="ef383-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="ef383-105">Dotazy LINQ lze kombinovat s tradičními řetězcovými funkcemi a regulárními výrazy.</span><span class="sxs-lookup"><span data-stu-id="ef383-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="ef383-106">Například můžete použít metodu <xref:System.String.Split%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> k vytvoření pole řetězců, které pak můžete dotazovat nebo upravit pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="ef383-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="ef383-107">Můžete použít metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> v klauzuli `where` dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="ef383-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="ef383-108">A můžete použít LINQ k dotazování nebo úpravám výsledků <xref:System.Text.RegularExpressions.MatchCollection> vrácených regulárním výrazem.</span><span class="sxs-lookup"><span data-stu-id="ef383-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="ef383-109">Pomocí technik popsaných v této části můžete také transformovat částečně strukturovaná textová data do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="ef383-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="ef383-110">Další informace najdete v tématu [Postupy: generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="ef383-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="ef383-111">Příklady v této části spadají do dvou kategorií:</span><span class="sxs-lookup"><span data-stu-id="ef383-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="ef383-112">Dotazování na blok textu</span><span class="sxs-lookup"><span data-stu-id="ef383-112">Querying a block of text</span></span>

<span data-ttu-id="ef383-113">Můžete zadávat dotazy, analyzovat a upravovat textové bloky rozdělením do pole Queryable menších řetězců pomocí metody <xref:System.String.Split%2A?displayProperty=nameWithType> nebo metody <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef383-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ef383-114">Zdrojový text můžete rozdělit na slova, věty, odstavce, stránky nebo jakákoli další kritéria a pak provést další rozdělení, pokud jsou v dotazu potřeba.</span><span class="sxs-lookup"><span data-stu-id="ef383-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="ef383-115">Jak spočítat výskyty slova v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="ef383-116">Ukazuje, jak použít LINQ pro jednoduché dotazování nad textem.</span><span class="sxs-lookup"><span data-stu-id="ef383-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="ef383-117">Postupy: vytvoření dotazu na věty obsahující zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="ef383-118">Ukazuje, jak rozdělit textové soubory na libovolné hranice a jak provádět dotazy proti každé části.</span><span class="sxs-lookup"><span data-stu-id="ef383-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="ef383-119">Postupy: dotaz na znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="ef383-120">Ukazuje, že řetězec je typu Queryable.</span><span class="sxs-lookup"><span data-stu-id="ef383-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="ef383-121">Jak kombinovat dotazy LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="ef383-122">Ukazuje, jak použít regulární výrazy v dotazech LINQ pro komplexní porovnávání vzorů u filtrovaných výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="ef383-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="ef383-123">Dotazování na částečně strukturovaná data ve formátu textu</span><span class="sxs-lookup"><span data-stu-id="ef383-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="ef383-124">Mnoho různých typů textových souborů se skládá z řady řádků, často s podobným formátováním, jako jsou například tabulátory nebo soubory oddělené čárkami nebo řádky s pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="ef383-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="ef383-125">Po přečtení takového textového souboru do paměti můžete použít LINQ k dotazování a úpravě řádků.</span><span class="sxs-lookup"><span data-stu-id="ef383-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="ef383-126">Dotazy LINQ také zjednodušují úlohu kombinování dat z více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="ef383-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="ef383-127">Postupy: Vyhledání rozdílového nastavení mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="ef383-128">Ukazuje, jak najít všechny řetězce, které jsou k dispozici v jednom seznamu, ale nikoli druhý.</span><span class="sxs-lookup"><span data-stu-id="ef383-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="ef383-129">Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="ef383-130">Ukazuje, jak seřadit řádky textu založené na jakémkoli slově nebo poli.</span><span class="sxs-lookup"><span data-stu-id="ef383-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="ef383-131">Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="ef383-132">Ukazuje, jak změnit pořadí polí v řádku v souboru. csv.</span><span class="sxs-lookup"><span data-stu-id="ef383-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="ef383-133">Postupy: kombinování a porovnávání kolekcí řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-133">How to: combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="ef383-134">Ukazuje, jak kombinovat seznamy řetězců různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ef383-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="ef383-135">Postupy: naplnění kolekcí objektů z více zdrojů (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="ef383-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="ef383-136">Ukazuje, jak vytvořit kolekce objektů pomocí více textových souborů jako zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="ef383-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="ef383-137">Postupy: spojení obsahu z nepodobných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="ef383-138">Ukazuje, jak kombinovat řetězce ve dvou seznamech do jednoho řetězce pomocí odpovídajícího klíče.</span><span class="sxs-lookup"><span data-stu-id="ef383-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="ef383-139">Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="ef383-140">Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ef383-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="ef383-141">Jak vypočítat hodnoty sloupce v textovém souboru CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef383-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="ef383-142">Ukazuje, jak provádět matematické výpočty s textovými daty v souborech. csv.</span><span class="sxs-lookup"><span data-stu-id="ef383-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef383-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef383-143">See also</span></span>

- [<span data-ttu-id="ef383-144">Dotaz integrovaný na jazyku (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="ef383-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="ef383-145">Postupy: Generování XML ze souborů CSV</span><span class="sxs-lookup"><span data-stu-id="ef383-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
