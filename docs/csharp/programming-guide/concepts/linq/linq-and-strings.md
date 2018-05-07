---
title: LINQ a řetězce (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: a297aec0a33893c643be337c356e304cdcd375ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linq-and-strings-c"></a>LINQ a řetězce (C#)
LINQ lze použít pro dotazování a Transformace řetězců a kolekcí řetězců. Může být obzvláště užitečný v případě částečně strukturovaných dat v textových souborů. Dotazů LINQ lze spojovat pomocí funkce tradiční řetězce a regulární výrazy. Například můžete použít <xref:System.String.Split%2A> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metodu pro vytvoření pole řetězců, které můžete zadat dotaz nebo upravovat pomocí LINQ. Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda v `where` klauzuli jazyka LINQ. A můžete LINQ dotazů nebo upravit <xref:System.Text.RegularExpressions.MatchCollection> výsledků vrácených regulární výraz.  
  
 Technik popsaných v této části můžete použít také k transformaci částečně strukturovaných textových dat do formátu XML. Další informace najdete v tématu [postupy: vygenerování XML ze souborů CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd).  
  
 Příklady v této části lze rozdělit do dvou kategorií:  
  
## <a name="querying-a-block-of-text"></a>Dotazování blok textu  
 Můžete zadat dotaz, analyzovat a upravit text bloky je rozdělením do dotazovatelné pole menší řetězců pomocí <xref:System.String.Split%2A> metoda nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metoda. Můžete zdrojový text rozdělení do slova, vět, odstavců, stránky nebo jiných kritérií a potom proveďte další rozdělení potřeby v dotazu.  
  
 [Postupy: počítání výskytů slova v řetězci (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Ukazuje, jak používat LINQ pro jednoduché dotazování přes text.  
  
 [Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)  
 Ukazuje, jak k rozdělení textové soubory na libovolný hranice a jak provádět dotazy pro každou část.  
  
 [Postupy: dotazu na znaky v řetězci (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-characters-in-a-string-linq.md)  
 Ukazuje, že je řetězec typu dotazovatelné.  
  
 [Postupy: kombinace dotazů LINQ s regulárními výrazy (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)  
 Ukazuje způsob použití regulárních výrazů v dotazech LINQ pro komplexní porovnávání se na výsledky filtrované dotazu.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Dotazování částečně strukturovaných dat v textovém formátu  
 Mnoho různých typů textových souborů se skládá z řady čar, často pomocí podobné formátování, například soubory kartě nebo čárkou nebo pevnou délkou řádky. Po přečtení textového souboru do paměti, můžete k dotazu a/nebo upravuje řádky LINQ. Dotazy LINQ také zjednodušit kombinováním dat z více zdrojů.  
  
 [Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)  
 Ukazuje, jak najít všechny řetězce, které se nacházejí v jeden seznam, ale ne na druhou.  
  
 [Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Ukazuje, jak řadit podle libovolného slova či pole řádků textu.  
  
 [Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-reorder-the-fields-of-a-delimited-file-linq.md)  
 Ukazuje, jak chcete změnit pořadí polí v řádku v souboru CSV.  
  
 [Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 Ukazuje, jak kombinovat seznamy řetězec různými způsoby.  
  
 [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Ukazuje postup vytvoření kolekce objektů s použitím více textových souborů jako zdroje dat.  
  
 [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 Ukazuje, jak kombinovat řetězců v dva seznamy do jednoho řetězce, pomocí odpovídající klíče.  
  
 [Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroj dat.  
  
 [Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Ukazuje, jak provádět matematické výpočty text dat v souborech CSV.  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [Postupy: Generování XML ze souborů CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
