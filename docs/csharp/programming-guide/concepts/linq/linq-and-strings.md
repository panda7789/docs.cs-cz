---
title: LINQ a řetězce (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: b805bc7318b8c5fe70ab1c060d1058a6bbc4f177
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635532"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="7ad02-102">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="7ad02-103">LINQ lze použít k dotazování a transformaci řetězce a kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="7ad02-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="7ad02-104">To může být užitečné zejména u polostrukturovaných dat v textových souborech.</span><span class="sxs-lookup"><span data-stu-id="7ad02-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="7ad02-105">Linq dotazy lze kombinovat s tradičními řetězcovými funkcemi a regulárními výrazy.</span><span class="sxs-lookup"><span data-stu-id="7ad02-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="7ad02-106">Metodu <xref:System.String.Split%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> můžete například použít k vytvoření pole řetězců, které pak můžete zadat dotazem nebo upravit pomocí linq.</span><span class="sxs-lookup"><span data-stu-id="7ad02-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="7ad02-107">Metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> můžete použít `where` v klauzuli dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="7ad02-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="7ad02-108">A můžete použít LINQ k <xref:System.Text.RegularExpressions.MatchCollection> dotazování nebo úpravě výsledků vrácených regulárním výrazem.</span><span class="sxs-lookup"><span data-stu-id="7ad02-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="7ad02-109">Můžete také použít techniky popsané v této části k transformaci polostrukturovaných textových dat do xml.</span><span class="sxs-lookup"><span data-stu-id="7ad02-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="7ad02-110">Další informace naleznete v tématu [Jak generovat XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="7ad02-110">For more information, see [How to generate XML from CSV files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="7ad02-111">Příklady v této části spadají do dvou kategorií:</span><span class="sxs-lookup"><span data-stu-id="7ad02-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="7ad02-112">Dotazování na blok textu</span><span class="sxs-lookup"><span data-stu-id="7ad02-112">Querying a block of text</span></span>

<span data-ttu-id="7ad02-113">Textové bloky můžete dotazovat, analyzovat a upravovat jejich rozdělením do dotazovatelného pole menších řetězců pomocí <xref:System.String.Split%2A?displayProperty=nameWithType> metody nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7ad02-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7ad02-114">Zdrojový text můžete rozdělit na slova, věty, odstavce, stránky nebo jiná kritéria a potom provést další rozdělení, pokud jsou v dotazu požadována.</span><span class="sxs-lookup"><span data-stu-id="7ad02-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="7ad02-115">Jak počítat výskyty slova v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="7ad02-116">Ukazuje, jak používat LINQ pro jednoduché dotazování na text.</span><span class="sxs-lookup"><span data-stu-id="7ad02-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="7ad02-117">Jak dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-117">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="7ad02-118">Ukazuje, jak rozdělit textové soubory na libovolné hranice a jak provádět dotazy na jednotlivé části.</span><span class="sxs-lookup"><span data-stu-id="7ad02-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="7ad02-119">Jak dotaz ovat znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-119">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="7ad02-120">Ukazuje, že řetězec je dotazovatelný typ.</span><span class="sxs-lookup"><span data-stu-id="7ad02-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="7ad02-121">Jak kombinovat dotazy LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="7ad02-122">Ukazuje, jak používat regulární výrazy v linq dotazech pro komplexní porovnávání vzorů ve filtrovaných výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="7ad02-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="7ad02-123">Dotazování polostrukturovaných dat v textovém formátu</span><span class="sxs-lookup"><span data-stu-id="7ad02-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="7ad02-124">Mnoho různých typů textových souborů se skládá z řady řádků, často s podobným formátováním, jako jsou soubory oddělené tabulátory nebo čárkami nebo řádky s pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="7ad02-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="7ad02-125">Po přečtení takového textového souboru do paměti můžete použít LINQ k dotazování nebo úpravě řádků.</span><span class="sxs-lookup"><span data-stu-id="7ad02-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="7ad02-126">Dotazy LINQ také zjednodušují úlohu kombinování dat z více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="7ad02-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="7ad02-127">Jak najít nastavený rozdíl mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-127">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="7ad02-128">Ukazuje, jak najít všechny řetězce, které jsou k dispozici v jednom seznamu, ale ne druhý.</span><span class="sxs-lookup"><span data-stu-id="7ad02-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="7ad02-129">Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="7ad02-130">Ukazuje, jak řadit řádky textu na základě libovolného slova nebo pole.</span><span class="sxs-lookup"><span data-stu-id="7ad02-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="7ad02-131">Jak uřadit pole odděleného souboru (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-131">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="7ad02-132">Ukazuje, jak ustavit pořadí polí v řádku v souboru CSV.</span><span class="sxs-lookup"><span data-stu-id="7ad02-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="7ad02-133">Jak kombinovat a porovnávat kolekce řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-133">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="7ad02-134">Ukazuje, jak kombinovat seznamy řetězců různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="7ad02-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="7ad02-135">Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-135">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="7ad02-136">Ukazuje, jak vytvořit kolekce objektů pomocí více textových souborů jako zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="7ad02-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="7ad02-137">Jak se připojit k obsahu z odlišných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-137">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="7ad02-138">Ukazuje, jak kombinovat řetězce ve dvou seznamech do jednoho řetězce pomocí odpovídajícího klíče.</span><span class="sxs-lookup"><span data-stu-id="7ad02-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="7ad02-139">Jak rozdělit soubor do mnoha souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-139">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="7ad02-140">Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="7ad02-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="7ad02-141">Jak vypočítat hodnoty sloupců v textovém souboru CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="7ad02-142">Ukazuje, jak provádět matematické výpočty na textová data v souborech .csv.</span><span class="sxs-lookup"><span data-stu-id="7ad02-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ad02-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ad02-143">See also</span></span>

- [<span data-ttu-id="7ad02-144">Dotaz integrovaný jazykem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad02-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="7ad02-145">Jak generovat XML ze souborů CSV</span><span class="sxs-lookup"><span data-stu-id="7ad02-145">How to generate XML from CSV files</span></span>](how-to-generate-xml-from-csv-files.md)
