---
title: Účinná kombinace operátorů
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
ms.openlocfilehash: 3088072646278dac13e4d483cb4f99297eaad9ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403469"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Účinná kombinace operátorů (Visual Basic)
Složité výrazy mohou obsahovat mnoho různých operátorů. Toto dokládá následující příklad.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Vytváření složitých výrazů, jako je například v předchozím příkladu, vyžaduje důkladné porozumění pravidlům s prioritou operátorů. Další informace najdete v tématu [Priorita operátorů v Visual Basic](../../../language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Výrazy kulatého závorky  
 Často chcete, aby operace pokračovaly v jiném pořadí, než je určeno podle priority operátora. Představte si následující příklad.  
  
 `x = z * y + 4`  
  
 Předchozí příklad vynásobí `z` `y` a poté přidá výsledek do `4` . Pokud ale chcete přidat `y` a `4` před vynásobením výsledku hodnotou `z` , můžete přepsat normální prioritu operátoru pomocí závorek. Uzavřením výrazu do závorek vynutíte, aby byl tento výraz vyhodnocen jako první, bez ohledu na přednost operátoru. Chcete-li vynutit předchozí příklad pro přidání prvního, můžete ho přepsat jako v následujícím příkladu.  
  
 `x = z * (y + 4)`  
  
 Předchozí příklad přidá `y` a a `4` pak vynásobí součet hodnotou `z` .  
  
### <a name="nested-parenthetical-expressions"></a>Vnořené výrazy na kulaté závorky  
 Můžete vnořit výrazy do několika úrovní závorek a ještě víc přepsat jejich prioritu. Výrazy, které jsou nejvíce vnořené v závorkách, jsou vyhodnoceny jako první, následované nejbližší vnořenou, a tak dále v nejmenším hluboko vnořeném a nakonec výrazy mimo závorky. Toto dokládá následující příklad.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 V předchozím příkladu `z + 2` je vyhodnocen jako první a pak na ostatní výrazy kulatého závorky. Umocnění, které obvykle má vyšší prioritu než sčítání nebo násobení, je vyhodnoceno jako poslední v tomto příkladu, protože ostatní výrazy jsou uzavřeny v závorkách.  
  
## <a name="see-also"></a>Viz také

- [Aritmetické operátory v jazyce Visual Basic](arithmetic-operators.md)
- [Operátory porovnání v jazyce Visual Basic](comparison-operators.md)
- [Logické a bitové operátory v jazyce Visual Basic](logical-and-bitwise-operators.md)
- [Logické/bitové operátory (Visual Basic)](../../../language-reference/operators/logical-bitwise-operators.md)
- [Logické výrazy](boolean-expressions.md)
- [Porovnání hodnot](value-comparisons.md)
- [Postupy: Výpočet numerických hodnot](how-to-calculate-numeric-values.md)
- [Priorita operátorů v jazyce Visual Basic](../../../language-reference/operators/operator-precedence.md)
