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
# <a name="linq-and-strings-c"></a>LINQ a řetězce (C#)

LINQ lze použít k dotazování a transformaci řetězce a kolekce řetězců. To může být užitečné zejména u polostrukturovaných dat v textových souborech. Linq dotazy lze kombinovat s tradičními řetězcovými funkcemi a regulárními výrazy. Metodu <xref:System.String.Split%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> můžete například použít k vytvoření pole řetězců, které pak můžete zadat dotazem nebo upravit pomocí linq. Metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> můžete použít `where` v klauzuli dotazu LINQ. A můžete použít LINQ k <xref:System.Text.RegularExpressions.MatchCollection> dotazování nebo úpravě výsledků vrácených regulárním výrazem.

Můžete také použít techniky popsané v této části k transformaci polostrukturovaných textových dat do xml. Další informace naleznete v tématu [Jak generovat XML ze souborů CSV](how-to-generate-xml-from-csv-files.md).

Příklady v této části spadají do dvou kategorií:

## <a name="querying-a-block-of-text"></a>Dotazování na blok textu

Textové bloky můžete dotazovat, analyzovat a upravovat jejich rozdělením do dotazovatelného pole menších řetězců pomocí <xref:System.String.Split%2A?displayProperty=nameWithType> metody nebo <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metody. Zdrojový text můžete rozdělit na slova, věty, odstavce, stránky nebo jiná kritéria a potom provést další rozdělení, pokud jsou v dotazu požadována.

- [Jak počítat výskyty slova v řetězci (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Ukazuje, jak používat LINQ pro jednoduché dotazování na text.

- [Jak dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Ukazuje, jak rozdělit textové soubory na libovolné hranice a jak provádět dotazy na jednotlivé části.

- [Jak dotaz ovat znaky v řetězci (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Ukazuje, že řetězec je dotazovatelný typ.

- [Jak kombinovat dotazy LINQ s regulárními výrazy (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Ukazuje, jak používat regulární výrazy v linq dotazech pro komplexní porovnávání vzorů ve filtrovaných výsledcích dotazu.

## <a name="querying-semi-structured-data-in-text-format"></a>Dotazování polostrukturovaných dat v textovém formátu

Mnoho různých typů textových souborů se skládá z řady řádků, často s podobným formátováním, jako jsou soubory oddělené tabulátory nebo čárkami nebo řádky s pevnou délkou. Po přečtení takového textového souboru do paměti můžete použít LINQ k dotazování nebo úpravě řádků. Dotazy LINQ také zjednodušují úlohu kombinování dat z více zdrojů.

- [Jak najít nastavený rozdíl mezi dvěma seznamy (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Ukazuje, jak najít všechny řetězce, které jsou k dispozici v jednom seznamu, ale ne druhý.

- [Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Ukazuje, jak řadit řádky textu na základě libovolného slova nebo pole.

- [Jak uřadit pole odděleného souboru (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Ukazuje, jak ustavit pořadí polí v řádku v souboru CSV.

- [Jak kombinovat a porovnávat kolekce řetězců (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Ukazuje, jak kombinovat seznamy řetězců různými způsoby.

- [Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Ukazuje, jak vytvořit kolekce objektů pomocí více textových souborů jako zdrojů dat.

- [Jak se připojit k obsahu z odlišných souborů (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Ukazuje, jak kombinovat řetězce ve dvou seznamech do jednoho řetězce pomocí odpovídajícího klíče.

- [Jak rozdělit soubor do mnoha souborů pomocí skupin (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Ukazuje, jak vytvořit nové soubory pomocí jednoho souboru jako zdroje dat.

- [Jak vypočítat hodnoty sloupců v textovém souboru CSV (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Ukazuje, jak provádět matematické výpočty na textová data v souborech .csv.

## <a name="see-also"></a>Viz také

- [Dotaz integrovaný jazykem (LINQ) (C#)](index.md)
- [Jak generovat XML ze souborů CSV](how-to-generate-xml-from-csv-files.md)
