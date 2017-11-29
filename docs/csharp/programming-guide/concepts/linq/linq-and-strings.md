---
title: "LINQ a řetězce (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7219c3b968f68d9a6c280749ffa6e8a1cb6938d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="e9e2f-102">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-102">LINQ and Strings (C#)</span></span>
<span data-ttu-id="e9e2f-103">LINQ lze použít pro dotazování a Transformace řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="e9e2f-104">Může být obzvláště užitečný v případě částečně strukturovaných dat v textových souborů.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="e9e2f-105">Dotazů LINQ lze spojovat pomocí funkce tradiční řetězce a regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="e9e2f-106">Například můžete použít <xref:System.String.Split%2A> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metodu pro vytvoření pole řetězců, které můžete zadat dotaz nebo upravovat pomocí LINQ.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="e9e2f-107">Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda v `where` klauzuli jazyka LINQ.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="e9e2f-108">A můžete LINQ dotazů nebo upravit <xref:System.Text.RegularExpressions.MatchCollection> výsledků vrácených regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="e9e2f-109">Technik popsaných v této části můžete použít také k transformaci částečně strukturovaných textových dat do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="e9e2f-110">Další informace najdete v tématu [postupy: vygenerování XML ze souborů CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd).</span><span class="sxs-lookup"><span data-stu-id="e9e2f-110">For more information, see [How to: Generate XML from CSV Files](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd).</span></span>  
  
 <span data-ttu-id="e9e2f-111">Příklady v této části lze rozdělit do dvou kategorií:</span><span class="sxs-lookup"><span data-stu-id="e9e2f-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="e9e2f-112">Dotazování blok textu</span><span class="sxs-lookup"><span data-stu-id="e9e2f-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="e9e2f-113">Můžete zadat dotaz, analyzovat a upravit text bloky je rozdělením do dotazovatelné pole menší řetězců pomocí <xref:System.String.Split%2A> metoda nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="e9e2f-114">Můžete zdrojový text rozdělení do slova, vět, odstavců, stránky nebo jiných kritérií a potom proveďte další rozdělení potřeby v dotazu.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="e9e2f-115">Postupy: počítání výskytů slova v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-115">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="e9e2f-116">Ukazuje, jak používat LINQ pro jednoduché dotazování přes text.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="e9e2f-117">Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)  
 <span data-ttu-id="e9e2f-118">Ukazuje, jak k rozdělení textové soubory na libovolný hranice a jak provádět dotazy pro každou část.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="e9e2f-119">Postupy: dotazu na znaky v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="e9e2f-120">Ukazuje, že je řetězec typu dotazovatelné.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="e9e2f-121">Postupy: kombinace dotazů LINQ s regulárními výrazy (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-121">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="e9e2f-122">Ukazuje způsob použití regulárních výrazů v dotazech LINQ pro komplexní porovnávání se na výsledky filtrované dotazu.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="e9e2f-123">Dotazování částečně strukturovaných dat v textovém formátu</span><span class="sxs-lookup"><span data-stu-id="e9e2f-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="e9e2f-124">Mnoho různých typů textových souborů se skládá z řady čar, často pomocí podobné formátování, například soubory kartě nebo čárkou nebo pevnou délkou řádky.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="e9e2f-125">Po přečtení textového souboru do paměti, můžete k dotazu a/nebo upravuje řádky LINQ.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="e9e2f-126">Dotazy LINQ také zjednodušit kombinováním dat z více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="e9e2f-127">Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="e9e2f-128">Ukazuje, jak najít všechny řetězce, které se nacházejí v jeden seznam, ale ne na druhou.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="e9e2f-129">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="e9e2f-130">Ukazuje, jak řadit podle libovolného slova či pole řádků textu.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="e9e2f-131">Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-reorder-the-fields-of-a-delimited-file-linq.md)  
 <span data-ttu-id="e9e2f-132">Ukazuje, jak chcete změnit pořadí polí v řádku v souboru CSV.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="e9e2f-133">Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-133">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="e9e2f-134">Ukazuje, jak kombinovat seznamy řetězec různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="e9e2f-135">Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="e9e2f-136">Ukazuje postup vytvoření kolekce objektů s použitím více textových souborů jako zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="e9e2f-137">Postupy: spojení obsahu z Nepodobných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="e9e2f-138">Ukazuje, jak kombinovat řetězců v dva seznamy do jednoho řetězce, pomocí odpovídající klíče.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="e9e2f-139">Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="e9e2f-140">Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="e9e2f-141">Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-141">How to: Compute Column Values in a CSV Text File (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="e9e2f-142">Ukazuje, jak provádět matematické výpočty text dat v souborech CSV.</span><span class="sxs-lookup"><span data-stu-id="e9e2f-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e2f-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9e2f-143">See Also</span></span>  
 [<span data-ttu-id="e9e2f-144">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9e2f-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="e9e2f-145">Postupy: vygenerování XML ze souborů CSV</span><span class="sxs-lookup"><span data-stu-id="e9e2f-145">How to: Generate XML from CSV Files</span></span>](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
