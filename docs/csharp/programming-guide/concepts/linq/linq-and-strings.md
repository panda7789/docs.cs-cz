---
title: LINQ a řetězce (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c7a1b86cc611d5f38ceab814b4594f5ad953fbc4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667402"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="48113-102">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="48113-103">LINQ umožňuje dotazování a transformaci řetězce a kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="48113-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="48113-104">Může být obzvlášť užitečné u částečně strukturovaných dat v textových souborech.</span><span class="sxs-lookup"><span data-stu-id="48113-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="48113-105">Dotazy LINQ lze kombinovat s tradiční řetězcové funkce a regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="48113-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="48113-106">Například můžete použít <xref:System.String.Split%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metodu pro vytvoření pole řetězců, které můžete dotazovat nebo měnit, a to pomocí jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="48113-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="48113-107">Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metodu `where` klauzule dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="48113-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="48113-108">A je možné použít LINQ dotaz nebo upravit <xref:System.Text.RegularExpressions.MatchCollection> výsledky vrácené modulem regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="48113-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="48113-109">Technik popsaných v této části můžete použít také k transformaci textových částečně strukturovaných dat do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="48113-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="48113-110">Další informace najdete v tématu [jak: Generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="48113-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="48113-111">Příklady v této části se dělí do dvou kategorií:</span><span class="sxs-lookup"><span data-stu-id="48113-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="48113-112">Dotazování blok textu</span><span class="sxs-lookup"><span data-stu-id="48113-112">Querying a block of text</span></span>

<span data-ttu-id="48113-113">Můžete dotazovat, analyzovat a upravte textové bloky tak, že jejich rozdělení do dotazovatelné pole menší řetězců s použitím <xref:System.String.Split%2A?displayProperty=nameWithType> metoda nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="48113-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="48113-114">Můžete rozdělit zdrojového textu na slova, věty, odstavce, stránky nebo jiných kritérií a pak proveďte další rozdělí potřeby v dotazu.</span><span class="sxs-lookup"><span data-stu-id="48113-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="48113-115">Postupy: Počítání výskytů slova v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-115">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="48113-116">Ukazuje způsob použití LINQ pro jednoduché dotazování přes text.</span><span class="sxs-lookup"><span data-stu-id="48113-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="48113-117">Postupy: Dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="48113-118">Ukazuje, jak rozdělit textové soubory na jakékoli hranice a spouštějte dotazy na jednotlivé části.</span><span class="sxs-lookup"><span data-stu-id="48113-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="48113-119">Postupy: Dotazu na znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="48113-120">Ukazuje, že je řetězec řazení dotazovatelného typu.</span><span class="sxs-lookup"><span data-stu-id="48113-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="48113-121">Postupy: Kombinace dotazů LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-121">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="48113-122">Ukazuje, jak používat regulární výrazy v dotazech LINQ pro složité vzorce pro porovnávání na filtrovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="48113-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="48113-123">Dotazování na částečně strukturovaná data ve formátu textu</span><span class="sxs-lookup"><span data-stu-id="48113-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="48113-124">Mnoho různých typů textové soubory se skládají z řady čar často a obsahují podobné formátování, jako jsou soubory kartu nebo čárkou nebo pevnou délkou řádky.</span><span class="sxs-lookup"><span data-stu-id="48113-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="48113-125">Po čtení textového souboru do paměti, můžete použít LINQ na dotazování a/nebo upravuje řádky.</span><span class="sxs-lookup"><span data-stu-id="48113-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="48113-126">Dotazy LINQ také zjednodušit kombinování dat z více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="48113-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="48113-127">Postupy: Hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="48113-128">Ukazuje, jak najít všechny řetězce, které se nacházejí v jednom seznamu, ale nikoli u druhého.</span><span class="sxs-lookup"><span data-stu-id="48113-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="48113-129">Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="48113-130">Ukazuje, jak řadit podle libovolného slova či pole řádků textu.</span><span class="sxs-lookup"><span data-stu-id="48113-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="48113-131">Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="48113-132">Ukazuje, jak změnit pořadí polí v řádku v souboru .csv.</span><span class="sxs-lookup"><span data-stu-id="48113-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="48113-133">Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-133">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="48113-134">Ukazuje, jak kombinovat řetězec seznamy různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="48113-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="48113-135">Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="48113-136">Ukazuje, jak vytvořit objekt kolekce s využitím více textových souborů jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="48113-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="48113-137">Postupy: Připojte se k obsahu z Nepodobných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="48113-138">Ukazuje, jak kombinovat řetězce ve dvou seznamů do jednoho řetězce s využitím odpovídajícího klíče.</span><span class="sxs-lookup"><span data-stu-id="48113-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="48113-139">Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="48113-140">Ukazuje, jak vytvořit nové soubory s využitím jednoho souboru jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="48113-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="48113-141">Postupy: Výpočet hodnot sloupce v textovém souboru CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-141">How to: Compute Column Values in a CSV Text File (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="48113-142">Ukazuje, jak k provádění matematických výpočtů na datech textu do souborů CSV.</span><span class="sxs-lookup"><span data-stu-id="48113-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="48113-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48113-143">See also</span></span>

- [<span data-ttu-id="48113-144">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="48113-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="48113-145">Postupy: Generování XML ze souborů CSV</span><span class="sxs-lookup"><span data-stu-id="48113-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
