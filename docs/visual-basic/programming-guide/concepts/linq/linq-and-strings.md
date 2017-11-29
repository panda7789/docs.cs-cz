---
title: "LINQ a řetězce (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b615f3dc76d72e7f73146498e0143f88c52278a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="5960e-102">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="5960e-103">LINQ lze použít pro dotazování a Transformace řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="5960e-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="5960e-104">Může být obzvláště užitečný v případě částečně strukturovaných dat v textových souborů.</span><span class="sxs-lookup"><span data-stu-id="5960e-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="5960e-105">Dotazů LINQ lze spojovat pomocí funkce tradiční řetězce a regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="5960e-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="5960e-106">Například můžete použít <xref:System.String.Split%2A> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metodu pro vytvoření pole řetězců, které můžete zadat dotaz nebo upravovat pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="5960e-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="5960e-107">Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda v `where` klauzuli jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="5960e-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="5960e-108">A můžete LINQ dotazů nebo upravit <xref:System.Text.RegularExpressions.MatchCollection> výsledků vrácených regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="5960e-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="5960e-109">Technik popsaných v této části můžete použít také k transformaci částečně strukturovaných textových dat do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="5960e-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="5960e-110">Další informace najdete v tématu [postupy: vygenerování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="5960e-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="5960e-111">Příklady v této části lze rozdělit do dvou kategorií:</span><span class="sxs-lookup"><span data-stu-id="5960e-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="5960e-112">Dotazování blok textu</span><span class="sxs-lookup"><span data-stu-id="5960e-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="5960e-113">Můžete zadat dotaz, analyzovat a upravit text bloky je rozdělením do dotazovatelné pole menší řetězců pomocí <xref:System.String.Split%2A> metoda nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5960e-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="5960e-114">Můžete zdrojový text rozdělení do slova, vět, odstavců, stránky nebo jiných kritérií a potom proveďte další rozdělení potřeby v dotazu.</span><span class="sxs-lookup"><span data-stu-id="5960e-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="5960e-115">Postupy: počítání výskytů slova v řetězci (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="5960e-116">Ukazuje, jak používat LINQ pro jednoduché dotazování přes text.</span><span class="sxs-lookup"><span data-stu-id="5960e-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="5960e-117">Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="5960e-118">Ukazuje, jak k rozdělení textové soubory na libovolný hranice a jak provádět dotazy pro každou část.</span><span class="sxs-lookup"><span data-stu-id="5960e-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="5960e-119">Postupy: dotazu na znaky v řetězci (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="5960e-120">Ukazuje, že je řetězec typu dotazovatelné.</span><span class="sxs-lookup"><span data-stu-id="5960e-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="5960e-121">Postupy: kombinace dotazů LINQ s regulárními výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="5960e-122">Ukazuje způsob použití regulárních výrazů v dotazech LINQ pro komplexní porovnávání se na výsledky filtrované dotazu.</span><span class="sxs-lookup"><span data-stu-id="5960e-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="5960e-123">Dotazování částečně strukturovaných dat v textovém formátu</span><span class="sxs-lookup"><span data-stu-id="5960e-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="5960e-124">Mnoho různých typů textových souborů se skládá z řady čar, často pomocí podobné formátování, například soubory kartě nebo čárkou nebo pevnou délkou řádky.</span><span class="sxs-lookup"><span data-stu-id="5960e-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="5960e-125">Po přečtení textového souboru do paměti, můžete k dotazu a/nebo upravuje řádky LINQ.</span><span class="sxs-lookup"><span data-stu-id="5960e-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="5960e-126">Dotazy LINQ také zjednodušit kombinováním dat z více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="5960e-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="5960e-127">Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="5960e-128">Ukazuje, jak najít všechny řetězce, které se nacházejí v jeden seznam, ale ne na druhou.</span><span class="sxs-lookup"><span data-stu-id="5960e-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="5960e-129">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="5960e-130">Ukazuje, jak řadit podle libovolného slova či pole řádků textu.</span><span class="sxs-lookup"><span data-stu-id="5960e-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="5960e-131">Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="5960e-132">Ukazuje, jak chcete změnit pořadí polí v řádku v souboru CSV.</span><span class="sxs-lookup"><span data-stu-id="5960e-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="5960e-133">Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="5960e-134">Ukazuje, jak kombinovat seznamy řetězec různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="5960e-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="5960e-135">Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="5960e-136">Ukazuje postup vytvoření kolekce objektů s použitím více textových souborů jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="5960e-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="5960e-137">Postupy: spojení obsahu z Nepodobných souborů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="5960e-138">Ukazuje, jak kombinovat řetězců v dva seznamy do jednoho řetězce, pomocí odpovídající klíče.</span><span class="sxs-lookup"><span data-stu-id="5960e-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="5960e-139">Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="5960e-140">Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="5960e-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="5960e-141">Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="5960e-142">Ukazuje, jak provádět matematické výpočty text dat v souborech CSV.</span><span class="sxs-lookup"><span data-stu-id="5960e-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5960e-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="5960e-143">See Also</span></span>  
 [<span data-ttu-id="5960e-144">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5960e-144">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 [<span data-ttu-id="5960e-145">Postupy: vygenerování XML ze souborů CSV</span><span class="sxs-lookup"><span data-stu-id="5960e-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
