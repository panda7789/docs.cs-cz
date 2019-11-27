---
title: LINQ a řetězce
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 73ce4bf5586f1f9ff4995ea6f425b90744b7e333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353284"
---
# <a name="linq-and-strings-visual-basic"></a>LINQ a řetězce (Visual Basic)
LINQ lze použít k dotazování a transformaci řetězců a kolekcí řetězců. Může být obzvláště užitečná pro částečně strukturovaná data v textových souborech. Dotazy LINQ lze kombinovat s tradičními řetězcovými funkcemi a regulárními výrazy. Například můžete použít metodu <xref:System.String.Split%2A> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A> k vytvoření pole řetězců, které pak můžete dotazovat nebo upravit pomocí LINQ. Můžete použít metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> v klauzuli `where` dotazu LINQ. A můžete použít LINQ k dotazování nebo úpravám výsledků <xref:System.Text.RegularExpressions.MatchCollection> vrácených regulárním výrazem.  
  
 Pomocí technik popsaných v této části můžete také transformovat částečně strukturovaná textová data do formátu XML. Další informace najdete v tématu [Postupy: generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).  
  
 Příklady v této části spadají do dvou kategorií:  
  
## <a name="querying-a-block-of-text"></a>Dotazování na blok textu  
 Můžete zadávat dotazy, analyzovat a upravovat textové bloky rozdělením do pole Queryable menších řetězců pomocí metody <xref:System.String.Split%2A> nebo metody <xref:System.Text.RegularExpressions.Regex.Split%2A>. Zdrojový text můžete rozdělit na slova, věty, odstavce, stránky nebo jakákoli další kritéria a pak provést další rozdělení, pokud jsou v dotazu potřeba.  
  
 [Postupy: počítání výskytů slova v řetězci (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Ukazuje, jak použít LINQ pro jednoduché dotazování nad textem.  
  
 [Postupy: vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Ukazuje, jak rozdělit textové soubory na libovolné hranice a jak provádět dotazy proti každé části.  
  
 [Postupy: dotaz na znaky v řetězci (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Ukazuje, že řetězec je typu Queryable.  
  
 [Jak kombinovat dotazy LINQ s regulárními výrazy (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Ukazuje, jak použít regulární výrazy v dotazech LINQ pro komplexní porovnávání vzorů u filtrovaných výsledků dotazu.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Dotazování na částečně strukturovaná data ve formátu textu  
 Mnoho různých typů textových souborů se skládá z řady řádků, často s podobným formátováním, jako jsou například tabulátory nebo soubory oddělené čárkami nebo řádky s pevnou délkou. Po přečtení takového textového souboru do paměti můžete použít LINQ k dotazování a úpravě řádků. Dotazy LINQ také zjednodušují úlohu kombinování dat z více zdrojů.  
  
 [Postupy: Vyhledání nastaveného rozdílu mezi dvěma seznamy (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Ukazuje, jak najít všechny řetězce, které jsou k dispozici v jednom seznamu, ale nikoli druhý.  
  
 [Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Ukazuje, jak seřadit řádky textu založené na jakémkoli slově nebo poli.  
  
 [Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Ukazuje, jak změnit pořadí polí v řádku v souboru. csv.  
  
 [Postupy: kombinování a porovnávání kolekcí řetězců (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Ukazuje, jak kombinovat seznamy řetězců různými způsoby.  
  
 [Postupy: naplnění kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Ukazuje, jak vytvořit kolekce objektů pomocí více textových souborů jako zdrojů dat.  
  
 [Postupy: spojení obsahu z nepodobných souborů (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Ukazuje, jak kombinovat řetězce ve dvou seznamech do jednoho řetězce pomocí odpovídajícího klíče.  
  
 [Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroje dat.  
  
 [Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Ukazuje, jak provádět matematické výpočty s textovými daty v souborech. csv.  
  
## <a name="see-also"></a>Viz také:

- [LINQ (Language-Integrated Query) (Visual Basic)](index.md)
- [Postupy: Generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md)
