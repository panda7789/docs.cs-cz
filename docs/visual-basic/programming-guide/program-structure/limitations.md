---
title: Omezení
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: f7e19977a011565bb4b1536af5cab195f8a01017
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347371"
---
# <a name="visual-basic-limitations"></a>Omezení jazyka Visual Basic
Starší verze Visual Basic vynutily hranice v kódu, jako je délka názvů proměnných, počet proměnných povolených v modulech a velikost modulu. V Visual Basic .NET byla tato omezení odlehčena a poskytuje větší volnost v psaní a uspořádávání kódu.  
  
 Fyzické limity jsou více závislé na paměti za běhu než při kompilaci. Pokud použijete obezřetné postupy programování a rozdělíte velké aplikace na více tříd a modulů, je velmi málo pravděpodobné, že zaznamenáte omezení interního Visual Basic.  
  
 Níže jsou uvedena některá omezení, která se mohou vyskytnout v extrémních případech:  
  
- **Délka názvu.** Existuje maximální počet znaků pro název každého deklarovaného programovacího prvku. Toto maximum platí pro celý řetězec kvalifikace, pokud je název elementu kvalifikován. Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
- **Délka řádku.** Ve fyzickém řádku zdrojového kódu je maximálně 65535 znaků. Pokud použijete znaky pro pokračování řádku, může být řádek logického zdrojového kódu delší. Viz [How to: break and kombinovat příkazy v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
- **Dimenze pole.** Existuje maximální počet dimenzí, které lze deklarovat pro pole. Tím se omezí počet indexů, které můžete použít k určení prvku pole. Zobrazení [dimenzí pole v Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
- **Délka řetězce.** Existuje maximální počet znaků Unicode, které lze uložit v jednom řetězci. Viz [datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
- **Délka řetězce prostředí.** Pro libovolný řetězec prostředí použité jako argument příkazového řádku je k dispozici maximálně 32768 znaků. Toto omezení se vztahuje na všechny platformy.  
  
## <a name="see-also"></a>Viz také:

- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic konvence pojmenování](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
