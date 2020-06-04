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
ms.openlocfilehash: dcf52c6200193f81070f323c8037ad82d747942d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403431"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Operátory a výrazy v jazyce Visual Basic
*Operátor* je prvek kódu, který provádí operaci na jednom nebo více prvcích kódu, které uchovávají hodnoty. Mezi prvky hodnoty patří proměnné, konstanty, literály, vlastnosti, návratové `Function` `Operator` procedury a a výrazy.  
  
 *Výraz* je řada prvků hodnot, které jsou kombinovány s operátory, což má za důsledek novou hodnotu. Operátory působí na prvky hodnoty provedením výpočtů, porovnávání nebo jiných operací.  
  
## <a name="types-of-operators"></a>Typy operátorů  
 Visual Basic poskytuje následující typy operátorů:  
  
- [Aritmetické operátory](arithmetic-operators.md) provádějí známé výpočty číselných hodnot, včetně posunování jejich bitových vzorů.  
  
- [Relační operátory](comparison-operators.md) porovnávají dva výrazy a vrátí `Boolean` hodnotu představující výsledek porovnání.  
  
- [Operátory zřetězení](concatenation-operators.md) spojí více řetězců do jednoho řetězce.  
  
- [Logické a bitové operátory v Visual Basic](logical-and-bitwise-operators.md) slučují `Boolean` nebo číslují hodnoty a vracejí výsledek stejného datového typu jako hodnoty.  
  
 Prvky hodnoty, které jsou kombinovány s operátorem, se nazývají *operandy* daného operátoru. Operátory kombinované s prvky hodnoty formuláře s výjimkou operátoru přiřazení, který tvoří *příkaz*. Další informace najdete v tématu [příkazy](../statements.md).  
  
## <a name="evaluation-of-expressions"></a>Vyhodnocení výrazů  
 Konečný výsledek výrazu představuje hodnotu, což je obvykle známý datový typ `Boolean` , například, `String` nebo číselný typ.  
  
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
  
 V předchozím příkladu Visual Basic provádí operace ve výrazu na pravé straně operátoru přiřazení ( `=` ) a potom přiřadí výslednou hodnotu k proměnné `x` na levé straně. Neexistuje žádné praktické omezení počtu operátorů, které je možné zkombinovat do výrazu, ale porozumění [prioritě operátorů v Visual Basic](../../../language-reference/operators/operator-precedence.md) je nezbytné k zajištění toho, abyste dosáhli očekávaných výsledků.  

## <a name="see-also"></a>Viz také

- [Operátory](../../../language-reference/operators/index.md)
- [Účinná kombinace operátorů](efficient-combination-of-operators.md)
- [Příkazy](../../../language-reference/statements/index.md)
