---
title: Výrazy logických hodnot (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 065df7d6217dd6f817dee1d11dd0fd4a68b6323c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965537"
---
# <a name="boolean-expressions-visual-basic"></a>Výrazy logických hodnot (Visual Basic)
A *logický výraz* je výraz, který se vyhodnotí na hodnotu [datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` nebo `False`. `Boolean` Výrazy lze provést několika způsoby. Nejjednodušší je přímé porovnání hodnoty `Boolean` proměnné `Boolean` literál, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>Dva význam = – operátor  
 Všimněte si, že přiřazovací příkaz `newCustomer = True` vypadá stejně jako v předchozím příkladu výraz, ale provádí různé funkce a je použit jiným způsobem. V předchozím příkladu výraz `newCustomer = True` představuje logickou hodnotu a `=` znak je interpretován jako operátor porovnání. V samostatné prohlášení `=` znak je interpretován jako operátor přiřazení a přiřadí hodnotu na pravé straně proměnné na levé straně. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Další informace najdete v tématu [porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) a [příkazy](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operátory porovnání  
 Operátory porovnání, jako například `=`, `<`, `>`, `<>`, `<=`, a `>=` vytvoření logických výrazů porovnáním výraz na levé straně výrazu na pravé straně operátoru operátor a vyhodnocení výsledek v podobě `True` nebo `False`. Toto dokládá následující příklad.  
  
 `42 < 81`  
  
 Protože 42 je menší než 81, logický výraz v předchozím příkladu je vyhodnocen jako `True`. Další informace o tento typ výrazu, naleznete v tématu [porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operátory porovnání v kombinaci s logickými operátory  
 Výrazy porovnání lze kombinovat pomocí logické operátory k vytvoření složitějších logických výrazů. Následující příklad ukazuje použití operátorů porovnání společně s logickým operátorem.  
  
 `x > y And x < 1000`  
  
 V předchozím příkladu, hodnota celkové výrazu závisí na hodnotách výrazů na obou stranách `And` operátor. Pokud jsou oba výrazy `True`, pak celkové výraz je vyhodnocen jako `True`. Pokud je buď výraz `False`, pak celý výraz vyhodnocen `False`.  
  
## <a name="short-circuiting-operators"></a>Krátký cyklus operátory  
 Logické operátory `AndAlso` a `OrElse` chovat říká *zkrácenou*. Levý operand vyhodnotí short-circuiting operátor nejprve. Pokud levý operand stanoví hodnotu tohoto celý výraz, provádění programu pokračuje bez vyhodnocení pravý výraz. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 V předchozím příkladu, operátor, který se vyhodnotí jako levý výraz `45 < 12`. Protože levý výraz je vyhodnocen jako `False`, musí být celé logický výraz vyhodnocen `False`. Spuštění programu tedy přeskočí provádění kódu v rámci `If` blok bez vyhodnocení pravý výraz `testFunction(3)`. Tento příklad nevolá `testFunction()` protože levý výraz falsifies celý výraz.  
  
 Podobně pokud levý výraz logický výraz, který pomocí `OrElse` vyhodnotí jako `True`, provádění pokračuje na další řádek kódu bez vyhodnocení pravý výraz, protože levý výraz už ověřila celý výraz.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Porovnání s bez Short Circuiting operátory  
 Oproti tomu vyhodnocují obě strany od logického operátoru při logické operátory `And` a `Or` se používají. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 Předchozí příklad volá `testFunction()` i v případě, že je levý výraz vyhodnocen `False`.  
  
## <a name="parenthetical-expressions"></a>Výrazy se závorkami  
 Závorky můžete řídit pořadí vyhodnocování logických výrazů. Nejprve vyhodnotit výrazy uzavřených v uvozovkách. Pro více úrovní vnoření přednost před udělením k nejhlouběji vnořených výrazů. Mezi kulaté závorky vyhodnocování pokračuje dle pravidel priority operátorů. Další informace najdete v tématu [priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Viz také:
- [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Příkazy](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Operátory porovnání](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
