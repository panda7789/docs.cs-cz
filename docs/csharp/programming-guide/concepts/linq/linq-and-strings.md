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
# <a name="linq-and-strings-c"></a>LINQ a řetězce (C#)

LINQ lze použít k dotazování a transformaci řetězců a kolekcí řetězců. Může být obzvláště užitečná pro částečně strukturovaná data v textových souborech. Dotazy LINQ lze kombinovat s tradičními řetězcovými funkcemi a regulárními výrazy. Například můžete použít metodu <xref:System.String.Split%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> k vytvoření pole řetězců, které pak můžete dotazovat nebo upravit pomocí LINQ. Můžete použít metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> v klauzuli `where` dotazu LINQ. A můžete použít LINQ k dotazování nebo úpravám výsledků <xref:System.Text.RegularExpressions.MatchCollection> vrácených regulárním výrazem.

Pomocí technik popsaných v této části můžete také transformovat částečně strukturovaná textová data do formátu XML. Další informace najdete v tématu [Postupy: generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).

Příklady v této části spadají do dvou kategorií:

## <a name="querying-a-block-of-text"></a>Dotazování na blok textu

Můžete zadávat dotazy, analyzovat a upravovat textové bloky rozdělením do pole Queryable menších řetězců pomocí metody <xref:System.String.Split%2A?displayProperty=nameWithType> nebo metody <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>. Zdrojový text můžete rozdělit na slova, věty, odstavce, stránky nebo jakákoli další kritéria a pak provést další rozdělení, pokud jsou v dotazu potřeba.

- [Jak spočítat výskyty slova v řetězci (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Ukazuje, jak použít LINQ pro jednoduché dotazování nad textem.

- [Postupy: vytvoření dotazu na věty obsahující zadanou sadu slov (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Ukazuje, jak rozdělit textové soubory na libovolné hranice a jak provádět dotazy proti každé části.

- [Postupy: dotaz na znaky v řetězci (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Ukazuje, že řetězec je typu Queryable.

- [Jak kombinovat dotazy LINQ s regulárními výrazy (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Ukazuje, jak použít regulární výrazy v dotazech LINQ pro komplexní porovnávání vzorů u filtrovaných výsledků dotazu.

## <a name="querying-semi-structured-data-in-text-format"></a>Dotazování na částečně strukturovaná data ve formátu textu

Mnoho různých typů textových souborů se skládá z řady řádků, často s podobným formátováním, jako jsou například tabulátory nebo soubory oddělené čárkami nebo řádky s pevnou délkou. Po přečtení takového textového souboru do paměti můžete použít LINQ k dotazování a úpravě řádků. Dotazy LINQ také zjednodušují úlohu kombinování dat z více zdrojů.

- [Postupy: Vyhledání rozdílového nastavení mezi dvěma seznamy (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Ukazuje, jak najít všechny řetězce, které jsou k dispozici v jednom seznamu, ale nikoli druhý.

- [Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Ukazuje, jak seřadit řádky textu založené na jakémkoli slově nebo poli.

- [Postupy: Změna pořadí polí souboru s oddělovači (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Ukazuje, jak změnit pořadí polí v řádku v souboru. csv.

- [Postupy: kombinování a porovnávání kolekcí řetězců (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Ukazuje, jak kombinovat seznamy řetězců různými způsoby.

- [Postupy: naplnění kolekcí objektů z více zdrojů (LINQ)C#()](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Ukazuje, jak vytvořit kolekce objektů pomocí více textových souborů jako zdrojů dat.

- [Postupy: spojení obsahu z nepodobných souborů (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Ukazuje, jak kombinovat řetězce ve dvou seznamech do jednoho řetězce pomocí odpovídajícího klíče.

- [Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroje dat.

- [Jak vypočítat hodnoty sloupce v textovém souboru CSV (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Ukazuje, jak provádět matematické výpočty s textovými daty v souborech. csv.

## <a name="see-also"></a>Viz také:

- [Dotaz integrovaný na jazyku (LINQ)C#()](index.md)
- [Postupy: Generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md)
