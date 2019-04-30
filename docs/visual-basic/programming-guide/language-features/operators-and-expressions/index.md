---
title: Operátory a výrazy v jazyce Visual Basic
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
ms.openlocfilehash: b762c3002913cbd925579ef28f2aa01411976c32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864322"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Operátory a výrazy v jazyce Visual Basic
*Operátor* je prvek kódu, který provádí operace na jeden nebo více prvků kódu, které obsahují hodnoty. Například prvky hodnotu proměnné, konstanty, literály, vlastnosti, vrátí z `Function` a `Operator` postupy a výrazy.  
  
 *Výraz* je řady hodnota prvků v kombinaci s operátory, které vrací novou hodnotu. Operátory elementů hodnotu zabývat tím, že provádí výpočty, porovnání nebo jiné operace.  
  
## <a name="types-of-operators"></a>Typy operátorů  
 Visual Basic poskytuje následující typy operátorů:  
  
- [Aritmetické operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) známých výpočtů na číselných hodnot, včetně jejich bitové vzory posunutí.  
  
- [Operátory porovnání](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porovnat dva výrazy a vrátí `Boolean` hodnotu představující výsledek porovnání.  
  
- [Operátory řetězení](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) připojit k více řetězců do jednoho řetězce.  
  
- [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) kombinovat `Boolean` nebo číselné hodnoty a vrátí výsledek stejný datový typ jako hodnoty.  
  
 Hodnota prvků, které jsou spojené s operátorem se nazývají *operandy* tohoto operátoru. Operátory v kombinaci s výrazy formuláře prvky hodnot, s výjimkou operátoru přiřazení, které formuláře *příkaz*. Další informace najdete v tématu [příkazy](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>Vyhodnocování výrazů  
 Představuje hodnotu, která je obvykle známých datový typ jako konečný výsledek výrazu `Boolean`, `String`, nebo číselného typu.  
  
 Následují příklady výrazů.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Několik operátorů můžete provádět akce v jednom výrazu nebo příkazu, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 V předchozím příkladu, Visual Basic provádí operace ve výrazu na pravé straně operátoru přiřazení (`=`), pak přiřadí výslednou hodnotu proměnné `x` na levé straně. Praktické neomezený počet operátorů, které je možné kombinovat do výrazu, ale znalost [priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) je nutné zajistit, že dostanete nezískáte očekávané výsledky.  

## <a name="see-also"></a>Viz také:

- [Operátory](../../../../visual-basic/language-reference/operators/index.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
