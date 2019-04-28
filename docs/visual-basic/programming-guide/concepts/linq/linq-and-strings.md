---
title: LINQ a řetězce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 7e0ebe64494182191dafa033ecbc38bad17180be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663411"
---
# <a name="linq-and-strings-visual-basic"></a>LINQ a řetězce (Visual Basic)
LINQ umožňuje dotazování a transformaci řetězce a kolekce řetězců. Může být obzvlášť užitečné u částečně strukturovaných dat v textových souborech. Dotazy LINQ lze kombinovat s tradiční řetězcové funkce a regulární výrazy. Například můžete použít <xref:System.String.Split%2A> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metodu pro vytvoření pole řetězců, které můžete dotazovat nebo měnit, a to pomocí jazyka LINQ. Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metodu `where` klauzule dotazu LINQ. A je možné použít LINQ dotaz nebo upravit <xref:System.Text.RegularExpressions.MatchCollection> výsledky vrácené modulem regulárních výrazů.  
  
 Technik popsaných v této části můžete použít také k transformaci textových částečně strukturovaných dat do formátu XML. Další informace najdete v tématu [jak: Generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).  
  
 Příklady v této části se dělí do dvou kategorií:  
  
## <a name="querying-a-block-of-text"></a>Dotazování blok textu  
 Můžete dotazovat, analyzovat a upravte textové bloky tak, že jejich rozdělení do dotazovatelné pole menší řetězců s použitím <xref:System.String.Split%2A> metoda nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> metody. Můžete rozdělit zdrojového textu na slova, věty, odstavce, stránky nebo jiných kritérií a pak proveďte další rozdělí potřeby v dotazu.  
  
 [Postupy: Počet výskytů slova v řetězci (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Ukazuje způsob použití LINQ pro jednoduché dotazování přes text.  
  
 [Postupy: Dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Ukazuje, jak rozdělit textové soubory na jakékoli hranice a spouštějte dotazy na jednotlivé části.  
  
 [Postupy: Dotazu na znaky v řetězci (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Ukazuje, že je řetězec řazení dotazovatelného typu.  
  
 [Postupy: Kombinace dotazů LINQ s regulárními výrazy (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Ukazuje, jak používat regulární výrazy v dotazech LINQ pro složité vzorce pro porovnávání na filtrovaných výsledků.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Dotazování na částečně strukturovaná Data ve formátu textu  
 Mnoho různých typů textové soubory se skládají z řady čar často a obsahují podobné formátování, jako jsou soubory kartu nebo čárkou nebo pevnou délkou řádky. Po čtení textového souboru do paměti, můžete použít LINQ na dotazování a/nebo upravuje řádky. Dotazy LINQ také zjednodušit kombinování dat z více zdrojů.  
  
 [Postupy: Hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Ukazuje, jak najít všechny řetězce, které se nacházejí v jednom seznamu, ale nikoli u druhého.  
  
 [Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Ukazuje, jak řadit podle libovolného slova či pole řádků textu.  
  
 [Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Ukazuje, jak změnit pořadí polí v řádku v souboru .csv.  
  
 [Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Ukazuje, jak kombinovat řetězec seznamy různými způsoby.  
  
 [Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Ukazuje, jak vytvořit objekt kolekce s využitím více textových souborů jako zdroje dat.  
  
 [Postupy: Připojte se k obsahu z Nepodobných souborů (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Ukazuje, jak kombinovat řetězce ve dvou seznamů do jednoho řetězce s využitím odpovídajícího klíče.  
  
 [Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Ukazuje, jak vytvořit nové soubory s využitím jednoho souboru jako zdroj dat.  
  
 [Postupy: Výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Ukazuje, jak k provádění matematických výpočtů na datech textu do souborů CSV.  
  
## <a name="see-also"></a>Viz také:

- [Language-Integrated Query (LINQ) (Visual Basic)](index.md)
- [Postupy: Generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md)
