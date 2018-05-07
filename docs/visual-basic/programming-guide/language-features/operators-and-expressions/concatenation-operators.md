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
ms.openlocfilehash: ab268e513e6f019ed651c94deb5e423cfcca7587
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="concatenation-operators-in-visual-basic"></a>Operátory řetězení v jazyce Visual Basic
Operátory řetězení více řetězců připojení do jednoho řetězce. Existují dva operátory zřetězení `+` a `&`. Jak provádět základní zřetězení operace, jako ukazuje následující příklad.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Můžete také zřetězení těchto operátorů `String` proměnné, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>Rozdíly mezi dva operátory zřetězení  
 [+ – Operátor](../../../../visual-basic/language-reference/operators/addition-operator.md) má primárním účelem přidání dvou čísel. Je však také řetězení číselné operandy s operandy řetězec. `+` Operátor obsahuje komplexní sadu pravidel, které určují, jestli se mají přidat, zřetězení, signál Chyba kompilátoru nebo throw za běhu <xref:System.InvalidCastException> výjimka.  
  
 [& Operátor](../../../../visual-basic/language-reference/operators/concatenation-operator.md) je určená jenom pro `String` operandy a vždy rozšiřuje jejími operandy k `String`, bez ohledu na to, že v nastavení `Option Strict`. `&` Operátor se doporučuje pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje možnost generování nezamýšleným převod.  
  
## <a name="performance-string-and-stringbuilder"></a>Výkon: Řetězec a StringBuilder  
 Pokud tak učiníte velký počet manipulace na řetězec, například zřetězování, odstranění a nahrazení, může výkon zisku z <xref:System.Text.StringBuilder> třídy v <xref:System.Text> oboru názvů. Trvá další instrukce k vytvoření a inicializace <xref:System.Text.StringBuilder> objekt a jiné instrukce převést jeho konečná hodnota k `String`, ale tentokrát může obnovit, protože <xref:System.Text.StringBuilder> může pracovat rychleji.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Typy metod manipulace s řetězci v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
