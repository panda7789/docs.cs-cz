---
title: Účinná kombinace operátorů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841240"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Účinná kombinace operátorů (Visual Basic)
Složité výrazy mohou obsahovat mnoho různých operátorů. Toto dokládá následující příklad.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Vytváření složitých výrazů, jako je například v předchozím příkladu vyžaduje důkladné pochopení pravidel priority operátorů. Další informace najdete v tématu [priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Výrazy se závorkami  
 Často se má operace pokračovat v jiném pořadí od stanovené prioritou operátorů. Podívejte se na následující příklad.  
  
 `x = z * y + 4`  
  
 Předchozí příklad vynásobí `z` podle `y`, pak přidá výsledek, který má `4`. Ale pokud chcete přidat `y` a `4` před násobením výsledků `z`, priorita operátorů normální můžete přepsat pomocí závorek. Uzavřením výrazu v závorkách vynutit tento výraz, který má být vyhodnocen jako první, bez ohledu na to priorita operátorů. K vynucení předchozí příklad provádět přidání, může přepsat ho jako v následujícím příkladu.  
  
 `x = z * (y + 4)`  
  
 Předchozí příklad přidá `y` a `4`, pak vynásobí tohoto součtu podle `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Vnořené výrazy se závorkami  
 Můžete vnořovat výrazy ve více úrovní závorky k přepsání priority ještě více. Výrazy v závorkách k nejhlouběji vnořené jsou vyčíslen první, za nímž následuje další nejhlouběji vnořená, a tak dále nejméně hluboce vnořený a nakonec výrazů mimo závorky. Toto dokládá následující příklad.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 V předchozím příkladu `z + 2` je Vyhodnocená první a pak kulatých závorek výrazy. Umocnění, což obvykle má vyšší prioritu než sčítání a násobení, se vyhodnocují jako poslední v tomto příkladu protože dalších výrazů jsou uzavřeny v závorkách.  
  
## <a name="see-also"></a>Viz také:

- [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Logické/bitové operátory (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Postupy: Výpočet numerických hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
