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
ms.openlocfilehash: 57378c3aa18a5cc108c10e8654e55803f3cf9052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649926"
---
# <a name="visual-basic-limitations"></a>Omezení jazyka Visual Basic
Starší verze jazyka Visual Basic vynutit hranice v kódu, jako je délka názvy proměnných, počet proměnných v moduly a velikost modulu povoleny. V jazyce Visual Basic .NET tato omezení mít byla zmírnit, která poskytuje větší svobodu v psaní a uspořádání kódu.  
  
 Fyzické omezení jsou závislé více běhové paměti než v době kompilace aspekty. Pokud používáte doporučeno programovací postupy a velké aplikace rozdělte do více tříd a moduly, je velmi malé pravděpodobnost vzniku k interní omezení jazyka Visual Basic.  
  
 Tady jsou některá omezení, které se mohou vyskytnout ve výjimečných případech:  
  
-   **Délka názvu.** Maximální počet znaků pro název každé deklarované programovací element není k dispozici. Tento maximální platí pro řetězec celý kvalifikace v případě, že je kvalifikovaný název elementu. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Délka řádku.** Je delší než 65 535 znaků na fyzické řádku zdrojového kódu. Řádek kódu logické zdroj může být delší, pokud používáte znaky pokračování řádku. V tématu [postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Rozměry pole.** Je maximální počet dimenzí, které můžou deklarovat pro pole. Toto nastavení omezuje počet indexů, můžete použít k určení k elementu pole. V tématu [pole dimenzí v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Délka řetězce.** Je maximální počet znaků Unicode, kam můžete ukládat v jednom řetězci. V tématu [řetězcový datový typ](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Délka řetězce prostředí.** Je delší než 32768 znaků pro libovolný řetězec prostředí použít jako argument příkazového řádku. Jedná se o omezení na všech platformách.  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
