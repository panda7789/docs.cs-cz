---
title: Operátory porovnání v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: 873ee31bf9c2ab195d66337d52e4a1bb7075ac76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="comparison-operators-in-visual-basic"></a>Operátory porovnání v jazyce Visual Basic
Relační operátory porovnání dvou výrazů a vrátí `Boolean` hodnotu, která představuje vztah jejich hodnot. Pro porovnání číselných hodnot, operátory porovnávání řetězců a operátory porovnání objektů existují operátory. Všechny tři typy operátory jsou popsané v tomto dokumentu.  
  
## <a name="comparing-numeric-values"></a>Porovnání číselných hodnot  
 Visual Basic porovná číselných hodnot pomocí šesti číselné relační operátory. Každý operátor má jako operandy dvou výrazů, která se vyhodnotí jako číselné hodnoty. V následující tabulce jsou uvedeny operátory a zobrazuje příklady jednotlivých.  
  
|Operátor|Stav testování|Příklady|  
|--------------|----------------------|--------------|  
|`=` (Rovnosti)|Je hodnota první výraz rovná hodnotě druhý?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (Nerovnost)|Je hodnota první výraz nerovné na hodnotu druhý?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (Méně než)|Je hodnota první výraz menší než hodnota druhého?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (Větší než)|Je větší než hodnota druhá hodnota první výraz?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (Je menší než nebo rovno)|Je hodnota první výraz menší než nebo rovna hodnotě druhý?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (Je větší než nebo rovno)|Hodnota první výraz, který je větší než nebo rovna hodnotě druhý?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Porovnání řetězců pomocí jazyka Visual Basic [jako operátor](../../../../visual-basic/language-reference/operators/like-operator.md) i číselné relační operátory. `Like` Operátor umožňuje určit vzor. Řetězec se pak porovná vzor, a pokud odpovídá, výsledkem je `True`. Jinak, výsledkem je `False`. Číselné operátory umožňují porovnat `String` hodnoty podle jejich pořadí, jak ukazuje následující příklad.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Výsledek v předchozím příkladu je `True` vzhledem k tomu, že první znak v řetězci první seřadí před první znak argumentu k druhému řetězci. Kdyby stejná prvních znaků porovnání bude pokračovat na další znak v oba řetězce a tak dále. Můžete také otestovat rovnosti řetězců pomocí operátoru rovnosti, jak ukazuje následující příklad.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Pokud jeden řetězec předpona jiné, jako je například "aa" a "aaa", považuje za delší řetězec být větší než kratší řetězec. Toto dokládá následující příklad.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Pořadí řazení je založena na binární porovnání nebo textové porovnání v závislosti na nastavení `Option Compare`. Další informace najdete v části [Option Compare – příkaz](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Porovnávání objektů  
 Visual Basic porovná dvě proměnné objektových referencí s [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) a [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md). Můžete použít některý z těchto operátorů k určení, zda dva referenční proměnné odkazují na stejnou instanci objektu. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 V předchozím příkladu `x Is y` vyhodnotí jako `True`, protože obě proměnné odkazují na stejnou instanci. Protějšek tímto výsledkem na následující příklad.  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 V předchozím příkladu `x Is y` vyhodnotí jako `False`, protože i když proměnné odkazují na objekty stejného typu, odkazují jiné instance daného typu.  
  
 Pokud chcete otestovat dva objekty není odkazující na stejnou instanci `IsNot` operátor umožňuje vyhnout gramaticky clumsy kombinaci `Not` a `Is`. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 V předchozím příkladu `If a IsNot b` je ekvivalentní `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Porovnání typ objektu  
 Můžete zkontrolovat, zda je objekt určitého typu se `TypeOf`... `Is` výraz. Syntaxe vypadá takto:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Když `typename` Určuje typ rozhraní, pak se `TypeOf`... `Is` výraz vrátí `True` Pokud objekt implementuje typ rozhraní. Když `typename` je typu třídy, pak vrátí výraz `True` Pokud instanci zadané třídy nebo třídy, která je odvozena ze třídy zadaný objekt. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 V předchozím příkladu `TypeOf x Is Control` výraz vyhodnocen jako `True` protože typ `x` je `Button`, který dědí z `Control`.  
  
 Další informace najdete v tématu [typeof – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Viz také  
 [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Operátory porovnání](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Operátory](../../../../visual-basic/language-reference/operators/index.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operátory řetězení v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
