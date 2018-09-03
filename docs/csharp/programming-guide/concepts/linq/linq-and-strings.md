---
title: LINQ a řetězce (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c7a1b86cc611d5f38ceab814b4594f5ad953fbc4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480636"
---
# <a name="linq-and-strings-c"></a>LINQ a řetězce (C#)

LINQ umožňuje dotazování a transformaci řetězce a kolekce řetězců. Může být obzvlášť užitečné u částečně strukturovaných dat v textových souborech. Dotazy LINQ lze kombinovat s tradiční řetězcové funkce a regulární výrazy. Například můžete použít <xref:System.String.Split%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metodu pro vytvoření pole řetězců, které můžete dotazovat nebo měnit, a to pomocí jazyka LINQ. Můžete použít <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metodu `where` klauzule dotazu LINQ. A je možné použít LINQ dotaz nebo upravit <xref:System.Text.RegularExpressions.MatchCollection> výsledky vrácené modulem regulárních výrazů.

Technik popsaných v této části můžete použít také k transformaci textových částečně strukturovaných dat do formátu XML. Další informace najdete v tématu [postupy: Generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).

Příklady v této části se dělí do dvou kategorií:

## <a name="querying-a-block-of-text"></a>Dotazování blok textu

Můžete dotazovat, analyzovat a upravte textové bloky tak, že jejich rozdělení do dotazovatelné pole menší řetězců s použitím <xref:System.String.Split%2A?displayProperty=nameWithType> metoda nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metody. Můžete rozdělit zdrojového textu na slova, věty, odstavce, stránky nebo jiných kritérií a pak proveďte další rozdělí potřeby v dotazu.

- [Postupy: počítání výskytů slova v řetězci (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Ukazuje způsob použití LINQ pro jednoduché dotazování přes text.

- [Postupy: dotaz na věty obsahující zadanou množinu slov (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Ukazuje, jak rozdělit textové soubory na jakékoli hranice a spouštějte dotazy na jednotlivé části.

- [Postupy: dotazu na znaky v řetězci (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Ukazuje, že je řetězec řazení dotazovatelného typu.

- [Postupy: kombinace dotazů LINQ s regulárními výrazy (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Ukazuje, jak používat regulární výrazy v dotazech LINQ pro složité vzorce pro porovnávání na filtrovaných výsledků.

## <a name="querying-semi-structured-data-in-text-format"></a>Dotazování na částečně strukturovaná data ve formátu textu

Mnoho různých typů textové soubory se skládají z řady čar často a obsahují podobné formátování, jako jsou soubory kartu nebo čárkou nebo pevnou délkou řádky. Po čtení textového souboru do paměti, můžete použít LINQ na dotazování a/nebo upravuje řádky. Dotazy LINQ také zjednodušit kombinování dat z více zdrojů.

- [Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Ukazuje, jak najít všechny řetězce, které se nacházejí v jednom seznamu, ale nikoli u druhého.

- [Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Ukazuje, jak řadit podle libovolného slova či pole řádků textu.

- [Postupy: Změna pořadí polí v souboru s oddělovači (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Ukazuje, jak změnit pořadí polí v řádku v souboru .csv.

- [Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Ukazuje, jak kombinovat řetězec seznamy různými způsoby.

- [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Ukazuje, jak vytvořit objekt kolekce s využitím více textových souborů jako zdroje dat.

- [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Ukazuje, jak kombinovat řetězce ve dvou seznamů do jednoho řetězce s využitím odpovídajícího klíče.

- [Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Ukazuje, jak vytvořit nové soubory s využitím jednoho souboru jako zdroj dat.

- [Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Ukazuje, jak k provádění matematických výpočtů na datech textu do souborů CSV.

## <a name="see-also"></a>Viz také:

- [Language-Integrated Query (LINQ) (C#)](index.md)
- [Postupy: Generování XML ze souborů CSV](how-to-generate-xml-from-csv-files.md)
