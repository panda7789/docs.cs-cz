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
ms.openlocfilehash: 46294b68bda8a5d2d21c0e4efea6a78e6a265ffe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403184"
---
# <a name="visual-basic-limitations"></a>Omezení jazyka Visual Basic
Starší verze Visual Basic vynutily hranice v kódu, jako je délka názvů proměnných, počet proměnných povolených v modulech a velikost modulu. V Visual Basic .NET byla tato omezení odlehčena a poskytuje větší volnost v psaní a uspořádávání kódu.  
  
 Fyzické limity jsou více závislé na paměti za běhu než při kompilaci. Pokud použijete obezřetné postupy programování a rozdělíte velké aplikace na více tříd a modulů, je velmi málo pravděpodobné, že zaznamenáte omezení interního Visual Basic.  
  
 Níže jsou uvedena některá omezení, která se mohou vyskytnout v extrémních případech:  
  
- **Délka názvu.** Existuje maximální počet znaků pro název každého deklarovaného programovacího prvku. Toto maximum platí pro celý řetězec kvalifikace, pokud je název elementu kvalifikován. Viz [deklarované názvy elementů](../language-features/declared-elements/declared-element-names.md).  
  
- **Délka řádku.** Ve fyzickém řádku zdrojového kódu je maximálně 65535 znaků. Pokud použijete znaky pro pokračování řádku, může být řádek logického zdrojového kódu delší. Viz [How to: break and kombinovat příkazy v kódu](how-to-break-and-combine-statements-in-code.md).  
  
- **Dimenze pole.** Existuje maximální počet dimenzí, které lze deklarovat pro pole. Tím se omezí počet indexů, které můžete použít k určení prvku pole. Zobrazení [dimenzí pole v Visual Basic](../language-features/arrays/array-dimensions.md).  
  
- **Délka řetězce.** Existuje maximální počet znaků Unicode, které lze uložit v jednom řetězci. Viz [datový typ String](../../language-reference/data-types/string-data-type.md).  
  
- **Délka řetězce prostředí.** Pro libovolný řetězec prostředí použité jako argument příkazového řádku je k dispozici maximálně 32768 znaků. Toto omezení se vztahuje na všechny platformy.  
  
## <a name="see-also"></a>Viz také

- [Struktura programu a konvence kódu](program-structure-and-code-conventions.md)
- [Zásady vytváření názvů jazyka Visual Basic](naming-conventions.md)
