---
title: Operátory a výrazy v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dae47988e27ed4b1a714943ce1fbffe3b815066b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="operators-and-expressions-in-visual-basic"></a>Operátory a výrazy v jazyce Visual Basic
*Operátor* je element kódu, který provede operaci na jeden nebo více elementy kódu, které mají hodnoty. Například prvky hodnotu proměnné, konstanty, literály, vlastnosti, vrátí z `Function` a `Operator` procedury a výrazy.  
  
 *Výraz* je řada hodnota elementy v kombinaci s operátory, která dává novou hodnotu. Operátory fungují na elementy hodnota provedením výpočtů, porovnání nebo jiné operace.  
  
## <a name="types-of-operators"></a>Typy operátorů  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]poskytuje následující typy operátory:  
  
-   [Aritmetické operátory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) provádět výpočty obeznámeni s číselných hodnot, včetně jejich bit vzory s posunem.  
  
-   [Operátory porovnání](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porovnání dvou výrazů a vrátí `Boolean` hodnotu představující výsledku porovnání.  
  
-   [Operátory zřetězení](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) připojení více řetězce do jednoho řetězce.  
  
-   [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) kombinovat `Boolean` nebo číselné hodnoty a vrátit výsledek stejný datový typ jako hodnoty.  
  
 Hodnota elementy, které jsou spojené s operátor se nazývají *operandy* tohoto operátoru. Operátory v kombinaci s výrazy formuláře prvky hodnot, s výjimkou operátoru přiřazení, které formuláře *příkaz*. Další informace najdete v tématu [příkazy](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>Vyhodnocení výrazu  
 Konečný výsledek výrazu představuje hodnotu, která je obvykle známé datového typu, jako `Boolean`, `String`, nebo číselného typu.  
  
 Následují příklady výrazů.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Několik operátorů můžete provádět akce v jeden výraz nebo příkaz, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 V předchozím příkladu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provádí operace ve výrazu na pravé straně operátoru přiřazení (`=`), potom přiřadí výsledná hodnota proměnné `x` na levé straně. Neexistuje žádné praktické omezení počtu operátory, které lze spojit do výrazu, ale k pochopení [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) je nutné zajistit, že dostanete očekáváte, že výsledky.  
  
 Další informace a příklady naleznete v tématu [operátor přetížení Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Viz také  
 [Operátory](../../../../visual-basic/language-reference/operators/index.md)  
 [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
