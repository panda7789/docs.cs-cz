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
# <a name="linq-and-strings-visual-basic"></a>LINQ a řetězce (Visual Basic)
LINQ lze použít pro dotazování a Transformace řetězců a kolekcí řetězců. Může být obzvláště užitečný v případě částečně strukturovaných dat v textových souborů. Dotazů LINQ lze spojovat pomocí funkce tradiční řetězce a regulární výrazy. Například můžete použít <xref:System.String.Split%2A> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metodu pro vytvoření pole řetězců, které můžete zadat dotaz nebo upravovat pomocí LINQ. Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda v `where` klauzuli jazyka LINQ. A můžete LINQ dotazů nebo upravit <xref:System.Text.RegularExpressions.MatchCollection> výsledků vrácených regulární výraz.  
  
 Technik popsaných v této části můžete použít také k transformaci částečně strukturovaných textových dat do formátu XML. Další informace najdete v tématu [postupy: vygenerování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).  
  
 Příklady v této části lze rozdělit do dvou kategorií:  
  
## <a name="querying-a-block-of-text"></a>Dotazování blok textu  
 Můžete zadat dotaz, analyzovat a upravit text bloky je rozdělením do dotazovatelné pole menší řetězců pomocí <xref:System.String.Split%2A> metoda nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metoda. Můžete zdrojový text rozdělení do slova, vět, odstavců, stránky nebo jiných kritérií a potom proveďte další rozdělení potřeby v dotazu.  
  
 [Postupy: počítání výskytů slova v řetězci (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Ukazuje, jak používat LINQ pro jednoduché dotazování přes text.  
  
 [Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Ukazuje, jak k rozdělení textové soubory na libovolný hranice a jak provádět dotazy pro každou část.  
  
 [Postupy: dotazu na znaky v řetězci (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Ukazuje, že je řetězec typu dotazovatelné.  
  
 [Postupy: kombinace dotazů LINQ s regulárními výrazy (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Ukazuje způsob použití regulárních výrazů v dotazech LINQ pro komplexní porovnávání se na výsledky filtrované dotazu.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Dotazování částečně strukturovaných dat v textovém formátu  
 Mnoho různých typů textových souborů se skládá z řady čar, často pomocí podobné formátování, například soubory kartě nebo čárkou nebo pevnou délkou řádky. Po přečtení textového souboru do paměti, můžete k dotazu a/nebo upravuje řádky LINQ. Dotazy LINQ také zjednodušit kombinováním dat z více zdrojů.  
  
 [Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Ukazuje, jak najít všechny řetězce, které se nacházejí v jeden seznam, ale ne na druhou.  
  
 [Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Ukazuje, jak řadit podle libovolného slova či pole řádků textu.  
  
 [Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Ukazuje, jak chcete změnit pořadí polí v řádku v souboru CSV.  
  
 [Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Ukazuje, jak kombinovat seznamy řetězec různými způsoby.  
  
 [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Ukazuje postup vytvoření kolekce objektů s použitím více textových souborů jako zdroje dat.  
  
 [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Ukazuje, jak kombinovat řetězců v dva seznamy do jednoho řetězce, pomocí odpovídající klíče.  
  
 [Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroj dat.  
  
 [Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Ukazuje, jak provádět matematické výpočty text dat v souborech CSV.  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (Visual Basic)](index.md)  
 [Postupy: vygenerování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md)
