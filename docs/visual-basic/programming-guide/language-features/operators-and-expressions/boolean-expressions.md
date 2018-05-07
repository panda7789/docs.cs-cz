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
ms.openlocfilehash: ff5843c815658468ac69fe5d62a9ea4cac2be830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="boolean-expressions-visual-basic"></a>Výrazy logických hodnot (Visual Basic)
A *logický výraz* je výraz, který se vyhodnotí na hodnotu [datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` nebo `False`. `Boolean` Výrazy lze provést několika způsoby. Nejjednodušší je přímé porovnání hodnoty `Boolean` proměnnou `Boolean` literál, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>Dva význam = – operátor  
 Všimněte si, že příkaz přiřazení `newCustomer = True` vypadá stejně jako výraz v předchozím příkladu, ale provádí různé funkce a se používá jiným způsobem. V předchozím příkladu výraz `newCustomer = True` představuje logickou hodnotu a `=` přihlašovací interpretována jako operátor porovnání. V samostatné příkazu `=` přihlašovací interpretována jako operátor přiřazení a přiřadí hodnota na pravé straně proměnnou na levé straně. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Další informace najdete v tématu [porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) a [příkazy](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operátory porovnání  
 Operátory porovnání jako `=`, `<`, `>`, `<>`, `<=`, a `>=` vytvořit tak, že porovnáte výraz na levé straně operátoru výrazu na pravé straně logické výrazy operátor a vyhodnocení výsledek v podobě `True` nebo `False`. Toto dokládá následující příklad.  
  
 `42 < 81`  
  
 Protože 42 je menší než 81, logický výraz v předchozím příkladu se vyhodnocuje `True`. Další informace o tento druh výraz najdete v tématu [porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operátory porovnání v kombinaci s logické operátory  
 Výrazy porovnání lze spojovat pomocí logických operátorů k vytvoření složitějších výrazy logických hodnot. Následující příklad ukazuje použití operátory porovnání ve spojení s logický operátor.  
  
 `x > y And x < 1000`  
  
 V předchozím příkladu hodnotu celkové výrazu závisí na hodnotách výrazů na každé straně `And` operátor. Pokud jsou oba výrazy `True`, pak celkové výraz vyhodnocen jako `True`. Pokud je buď výraz `False`, pak celý výraz vyhodnocen `False`.  
  
## <a name="short-circuiting-operators"></a>Krátká smyčka operátory  
 Logické operátory `AndAlso` a `OrElse` vykazovat chování známé jako *krátká smyčka*. Levý operand vyhodnotí short-circuiting operátor nejdřív. Pokud levý operand Určuje hodnotu celého výrazu, spuštění programu pokračuje bez vyhodnocení pravý výraz. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 V předchozím příkladu operátor vyhodnotí levý výraz `45 < 12`. Protože levý výraz vyhodnocen jako `False`, se musí vyhodnotit celý logický výraz `False`. Spuštění programu proto přeskočí spuštění kódu v rámci `If` bloku bez vyhodnocení pravý výraz `testFunction(3)`. Tento příklad nevyvolá `testFunction()` protože levý výraz falsifies celý výraz.  
  
 Podobně pokud levý výraz logický výraz pomocí `OrElse` vyhodnotí jako `True`, provádění pokračuje bez vyhodnocení pravý výraz dalším řádku kódu, protože levý výraz už ověřila celý výraz.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Porovnání s bez krátké Circuiting operátory  
 Oproti tomu vyhodnocují obou stranách logický operátor při logické operátory `And` a `Or` se používají. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 Předchozí příklad volání `testFunction()` Přestože levý výraz vyhodnocen jako `False`.  
  
## <a name="parenthetical-expressions"></a>Výrazy se závorkami  
 Závorky můžete použít k řízení pořadí vyhodnocování výrazy logických hodnot. Nejprve vyhodnotit výrazy uzavřena v závorkách. Pro více úrovní vnoření přednost před udělena nejvíce hluboko vložené výrazy. V uvozovkách vyhodnocení pokračuje podle pravidel objektů operátorů. Další informace najdete v tématu [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Viz také  
 [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Příkazy](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operátory porovnání](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
