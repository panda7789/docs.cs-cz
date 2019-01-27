---
title: Omezení jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 0f356b52304110299ed0af9bbccd5d03893f31a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596355"
---
# <a name="visual-basic-limitations"></a>Omezení jazyka Visual Basic
Starší verze jazyka Visual Basic vynutí hranice v kódu, jako je délka názvy proměnných, počet proměnných v moduly a velikost modulu povoleny. V jazyce Visual Basic .NET tato omezení mají byla zmírnit, získáte tak větší volnost při psaní a organizaci kódu.  
  
 Fyzických omezení jsou závislé další z paměti za běhu, než na důležité informace o kompilaci. Pokud používáte překročené programovací postupy a rozdělení velké aplikace do více tříd a moduly, je velmi malé pravděpodobnost vzniku vnitřní omezení jazyka Visual Basic.  
  
 Toto jsou některá omezení, které můžete narazit v extrémních případech:  
  
-   **Délka názvu.** Maximální počet znaků pro název každé deklarovaný programový prvek je. Toto maximum platí na řetězec, celé kvalifikace, pokud je kvalifikován názvem elementu. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Délka řádku.** Je maximálně 65535 znaků fyzického řádku zdrojového kódu. Řádky logické zdrojového kódu může být déle, pokud používáte znaky pokračování řádku. Zobrazit [jak: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Rozměry pole.** Je maximální počet dimenzí, které je možné deklarovat pro pole. To omezuje počet indexů, můžete použít k určení k elementu pole. Zobrazit [pole dimenze v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Délka řetězce.** Je maximální počet znaků Unicode, které můžete ukládat do jednoho řetězce. Zobrazit [řetězcový datový typ.](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Délka řetězce prostředí.** Je maximálně 32768 znaků pro libovolný řetězec prostředí použít jako argument příkazového řádku. Jedná se o omezení na všech platformách.  
  
## <a name="see-also"></a>Viz také:
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
