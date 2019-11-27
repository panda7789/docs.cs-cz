---
title: Operátory porovnání
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
ms.openlocfilehash: e1feb08539e47ec6fda64aa1a1f8ec2cc19f7b62
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346070"
---
# <a name="comparison-operators-in-visual-basic"></a>Operátory porovnání v jazyce Visual Basic
Relační operátory porovnávají dva výrazy a vracejí `Boolean`ou hodnotu, která představuje vztah jejich hodnot. Existují operátory pro porovnávání číselných hodnot, operátory pro porovnávání řetězců a operátory pro porovnávání objektů. Všechny tři typy operátorů jsou popsány zde.  
  
## <a name="comparing-numeric-values"></a>Porovnávání číselných hodnot  
 Visual Basic porovnává číselné hodnoty pomocí šesti číselných relačních operátorů. Každý operátor přebírá jako operandy dva výrazy, které jsou vyhodnoceny na číselné hodnoty. Následující tabulka uvádí operátory a ukazuje příklady jednotlivých.  
  
|Operátor|Podmínka otestována|Příklady|  
|--------------|----------------------|--------------|  
|`=` (rovnost)|Je hodnota prvního výrazu rovna hodnotě sekundy?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (nerovnost)|Je hodnota prvního výrazu nerovná hodnotě sekundy?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (méně než)|Je hodnota prvního výrazu menší než hodnota sekundy?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (je větší než)|Je hodnota prvního výrazu většího než hodnota sekundy?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (je menší než nebo rovno)|Je hodnota prvního výrazu menší nebo rovna hodnotě sekundy?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (je větší než nebo rovno)|Je hodnota prvního výrazu větší nebo rovna hodnotě sekundy?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Visual Basic porovnává řetězce pomocí [operátoru LIKE](../../../../visual-basic/language-reference/operators/like-operator.md) a číselných relačních operátorů. Operátor `Like` umožňuje zadat vzor. Řetězec se pak porovná se vzorem a pokud odpovídá, výsledek je `True`. V opačném případě je výsledek `False`. Číselné operátory umožňují porovnat `String` hodnoty podle jejich pořadí řazení, jak ukazuje následující příklad.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Výsledek v předchozím příkladu je `True`, protože první znak v prvním řetězci seřadí před první znak v druhém řetězci. Pokud byly první znaky stejné, porovnání by pokračovalo na dalším znaku v obou řetězcích, a tak dále. Můžete také otestovat rovnost řetězců pomocí operátoru rovnosti, jak ukazuje následující příklad.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Pokud je jeden řetězec předponou jiného, například "AA" a "AAA", delší řetězec je považován za větší než kratší řetězec. Toto dokládá následující příklad.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Pořadí řazení vychází z binárního porovnání nebo z textového porovnání v závislosti na nastavení `Option Compare`. Další informace najdete v tématu [příkaz Option Compare](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Porovnávání objektů  
 Visual Basic porovná dvě proměnné odkazu na objekt s [operátorem is](../../../../visual-basic/language-reference/operators/is-operator.md) a [operátorem IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md). Můžete použít kterýkoli z těchto operátorů k určení, zda dvě referenční proměnné odkazují na stejnou instanci objektu. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 V předchozím příkladu `x Is y` vyhodnocuje jako `True`, protože obě proměnné odkazují na stejnou instanci. Porovnejte tento výsledek s následujícím příkladem.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 V předchozím příkladu `x Is y` vyhodnocena jako `False`, protože i když proměnné odkazují na objekty stejného typu, odkazují na různé instance daného typu.  
  
 Pokud chcete testovat dva objekty, které neukazují na stejnou instanci, operátor `IsNot` umožňuje vyhnout se gramaticky clumsy kombinaci `Not` a `Is`. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 V předchozím příkladu je `If a IsNot b` ekvivalentem `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Porovnání typu objektu  
 Můžete otestovat, zda je objekt určitého typu pomocí výrazu `TypeOf`...`Is`. Syntaxe je následující:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Když `typename` určuje typ rozhraní, pak výraz `TypeOf`...`Is` vrátí `True`, pokud objekt implementuje typ rozhraní. Když `typename` je typ třídy, pak výraz vrátí `True`, pokud je objekt instancí zadané třídy nebo třídy, která je odvozena ze zadané třídy. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 V předchozím příkladu je výraz `TypeOf x Is Control` vyhodnocen jako `True`, protože typ `x` je `Button`, který dědí z `Control`.  
  
 Další informace naleznete v tématu [operátor typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Viz také:

- [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Operátory porovnání](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operátory](../../../../visual-basic/language-reference/operators/index.md)
- [Aritmetické operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory zřetězení v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Logické a bitové operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
