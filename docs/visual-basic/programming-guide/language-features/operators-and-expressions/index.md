---
title: Operátory a výrazy
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: fa410a739be2da8802e76a35068448263ddec1fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343613"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Operátory a výrazy v jazyce Visual Basic
*Operátor* je prvek kódu, který provádí operaci na jednom nebo více prvcích kódu, které uchovávají hodnoty. Prvky hodnoty zahrnují proměnné, konstanty, literály, vlastnosti, návrat z `Function` a `Operator` a výrazy.  
  
 *Výraz* je řada prvků hodnot, které jsou kombinovány s operátory, což má za důsledek novou hodnotu. Operátory působí na prvky hodnoty provedením výpočtů, porovnávání nebo jiných operací.  
  
## <a name="types-of-operators"></a>Typy operátorů  
 Visual Basic poskytuje následující typy operátorů:  
  
- [Aritmetické operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) provádějí známé výpočty číselných hodnot, včetně posunování jejich bitových vzorů.  
  
- [Relační operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porovnávají dva výrazy a vracejí hodnotu `Boolean` reprezentující výsledek porovnání.  
  
- [Operátory zřetězení](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) spojí více řetězců do jednoho řetězce.  
  
- [Logické a bitové operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) kombinovat `Boolean` nebo číselné hodnoty a vracet výsledek stejného datového typu jako hodnoty.  
  
 Prvky hodnoty, které jsou kombinovány s operátorem, se nazývají *operandy* daného operátoru. Operátory kombinované s prvky hodnoty formuláře s výjimkou operátoru přiřazení, který tvoří *příkaz*. Další informace najdete v tématu [příkazy](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>Vyhodnocení výrazů  
 Konečný výsledek výrazu představuje hodnotu, což je obvykle známý datový typ, například `Boolean`, `String`nebo číselný typ.  
  
 Následují příklady výrazů.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Několik operátorů může provádět akce v jednom výrazu nebo příkazu, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 V předchozím příkladu Visual Basic provádí operace ve výrazu na pravé straně operátoru přiřazení (`=`) a následně přiřadí výslednou hodnotu k proměnné `x` vlevo. Neexistuje žádné praktické omezení počtu operátorů, které je možné zkombinovat do výrazu, ale porozumění [prioritě operátorů v Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) je nezbytné k zajištění toho, abyste dosáhli očekávaných výsledků.  

## <a name="see-also"></a>Viz také:

- [Operátory](../../../../visual-basic/language-reference/operators/index.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
