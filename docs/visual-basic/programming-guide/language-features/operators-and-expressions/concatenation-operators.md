---
title: Operátory řetězení v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: 5151265235868c2a7991bee61b26a4a0da09f901
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978095"
---
# <a name="concatenation-operators-in-visual-basic"></a>Operátory řetězení v jazyce Visual Basic
Operátory řetězení více řetězců připojení do jednoho řetězce. Existují dva operátory zřetězení `+` a `&`. Obě provedení operace základní zřetězení, jak ukazuje následující příklad.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Tyto operátory lze také zřetězit `String` proměnné, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>Rozdíly mezi dva operátory zřetězení  
 [+ – Operátor](../../../../visual-basic/language-reference/operators/addition-operator.md) je hlavním účelem sečtení dvou čísel. Nicméně lze zřetězit také číselné operandů s operandy řetězec. `+` Operátor nemá komplexní sadu pravidel, které určují, jestli se má přidat, zřetězit, signalizuje, že chyba kompilátoru nebo výjimku za běhu <xref:System.InvalidCastException> výjimky.  
  
 [& – Operátor](../../../../visual-basic/language-reference/operators/concatenation-operator.md) je určená jenom pro `String` operandy a to vždy rozšiřuje jeho operandy `String`bez ohledu na nastavení `Option Strict`. `&` Operátor se doporučuje pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje pravděpodobnost generování neúmyslnému převodu.  
  
## <a name="performance-string-and-stringbuilder"></a>Výkon: String a StringBuilder  
 Pokud tak učiníte velký počet manipulace na řetězec, například zřetězení, odstranění a nahrazení, může být z zisku výkonu <xref:System.Text.StringBuilder> třídy v <xref:System.Text> oboru názvů. Přijímá další instrukce k vytváření a inicializace <xref:System.Text.StringBuilder> objektu a další pokyny, jak převést na jeho poslední hodnotu `String`, ale tentokrát může obnovit, protože <xref:System.Text.StringBuilder> může pracovat rychleji.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Typy metod manipulace s řetězci v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
