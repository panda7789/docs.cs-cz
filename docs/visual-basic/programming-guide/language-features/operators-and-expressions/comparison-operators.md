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
ms.openlocfilehash: db9eef215b16c95a40dfc622bb29443dd1736943
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552031"
---
# <a name="comparison-operators-in-visual-basic"></a>Operátory porovnání v jazyce Visual Basic
Operátory porovnání porovnat dva výrazy a vrátí `Boolean` hodnotu, která představuje vztah jejich hodnoty. Existují operátory pro porovnání číselných hodnot, operátorů pro porovnávání řetězců a operátory porovnání objektů. Všechny tři typy operátorů jsou popsány zde.  
  
## <a name="comparing-numeric-values"></a>Porovnání číselných hodnot  
 Visual Basic porovnává číselných hodnot pomocí šesti číselné porovnání operátorů. Každý operátor používá jako operandy dvou výrazů, která se vyhodnotí na číselné hodnoty. V následující tabulce jsou uvedeny operátory a jsou uvedeny příklady každého.  
  
|Operátor|Podmínky testování|Příklady|  
|--------------|----------------------|--------------|  
|`=` (Rovnost)|Hodnota první výraz rovnosti má hodnotu druhého?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (Nerovnost)|Hodnota první výraz, který nerovnost hodnotu druhého?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (Méně než)|Je hodnota první výraz menší než hodnota druhého?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (Větší než)|Hodnota první výraz, který je větší než hodnota druhého?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (Menší než nebo rovno)|Je hodnota první výraz menší než nebo rovna hodnotě druhého?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (Větší než nebo rovno)|Hodnotu prvního výrazu je větší než nebo rovna hodnotě druhého?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Porovná řetězce pomocí jazyka Visual Basic [operátor Like](../../../../visual-basic/language-reference/operators/like-operator.md) i operátory číselné porovnání. `Like` Operátor můžete zadat vzor. Řetězec se následně porovnává vzorem, a pokud se nenajde, výsledkem je `True`. V opačném případě je výsledek `False`. Číselné operátory umožňuje porovnat `String` hodnoty podle jejich pořadí, jak ukazuje následující příklad.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Výsledek v předchozím příkladu je `True` vzhledem k tomu, že první znak v řetězci první řadí před první znak v druhý řetězec. Kdyby rovná prvních znaků, porovnání by pokračovat na další znak v obou řetězců a tak dále. Můžete také testovat rovnost řetězců pomocí operátoru rovnosti, jak ukazuje následující příklad.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Pokud předponu jiné, jako je například "aa" a "aaa", je jeden řetězec delší řetězce, se považuje za větší než kratší řetězec. Toto dokládá následující příklad.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Pořadí řazení je podle binární porovnání nebo textové porovnání. v závislosti na nastavení `Option Compare`. Další informace najdete v části [možnost porovnat příkaz](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Porovnávání objektů  
 Porovná dvě proměnné odkazu na objekt pomocí jazyka Visual Basic [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) a [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md). Určete, jestli dvě referenční proměnné odkazovat na stejnou instanci objektu můžete použít některý z těchto operátorů. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 V předchozím příkladu `x Is y` vyhodnotí jako `True`, protože obě proměnné odkazovat na stejnou instanci. Kontrast tento výsledek v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 V předchozím příkladu `x Is y` vyhodnotí jako `False`, protože i když proměnné odkazovat na objekty stejného typu, odkazují na různé instance daného typu.  
  
 Pokud chcete otestovat pro dva objekty nejsou odkazuje na stejnou instanci `IsNot` operátor vyhnete gramaticky clumsy kombinaci `Not` a `Is`. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 V předchozím příkladu `If a IsNot b` je ekvivalentní `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Porovnávání typu objektu  
 Můžete zkontrolovat, jestli je objekt s určitého typu `TypeOf`... `Is` výrazu. Syntaxe vypadá takto:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Když `typename` Určuje typ rozhraní, pak bude `TypeOf`... `Is` výraz vrátí `True` Pokud objekt implementuje typ rozhraní. Když `typename` je typ třídy, pak výraz vrací `True` Pokud je objekt instancí zadané třídy nebo třídy, která je odvozena z dané třídy. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 V předchozím příkladu `TypeOf x Is Control` výraz vyhodnocen jako `True` protože typu `x` je `Button`, který dědí z `Control`.  
  
 Další informace najdete v tématu [TypeOf operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Viz také:
- [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Operátory porovnání](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operátory](../../../../visual-basic/language-reference/operators/index.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory řetězení v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
