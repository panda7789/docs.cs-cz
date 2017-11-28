---
title: "Účinná kombinace operátorů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Účinná kombinace operátorů (Visual Basic)
Složité výrazy může obsahovat mnoho různých operátory. Toto dokládá následující příklad.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Vytvoření složité výrazy, jako je třeba v předchozím příkladu vyžaduje důkladné znalosti týkající se pravidla operátorů. Další informace najdete v tématu [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Výrazy se závorkami  
 Často se má operace pokračovat v jiném pořadí od dáno operátorů. Podívejte se na následující příklad.  
  
 `x = z * y + 4`  
  
 V předchozím příkladu vynásobí `z` podle `y`, pak přidá výsledek, který má `4`. Ale pokud chcete přidat `y` a `4` před vynásobením výsledku podle `z`, normální priorita operátorů lze přepsat pomocí závorek. Uzavřením výrazu v závorkách, můžete vynutit tento výraz, který se vyhodnotí nejprve, bez ohledu na to operátorů. Chcete-li vynutit v předchozím příkladu uděláte přidání, může být přepisování jako v následujícím příkladu.  
  
 `x = z * (y + 4)`  
  
 V předchozím příkladu přidá `y` a `4`, pak vynásobí tento součet podle `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Vnořené výrazy se závorkami  
 Výrazy v závorkách přepsat přednost před i další více úrovní vnoření. Výrazy v závorkách nejvíce hluboko vnořené se vyhodnocují jako první, za nímž následuje další nejvíce hluboko vnořené, a tak dále alespoň hluboko vložené a nakonec výrazů mimo závorky. Toto dokládá následující příklad.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 V předchozím příkladu `z + 2` vyhodnotí první, pak je shod výrazy. Exponenciální zápis, což obvykle má vyšší prioritu než přidání nebo násobení, je v tomto příkladu vyhodnotit poslední, protože jiné výrazy jsou uzavřené v závorkách.  
  
## <a name="see-also"></a>Viz také  
 [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Logické/bitové operátory (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Postupy: výpočet numerických hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
