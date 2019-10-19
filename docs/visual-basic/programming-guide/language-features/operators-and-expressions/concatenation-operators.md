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
ms.openlocfilehash: 789478cafc4ed7506d34fb4198531d437683075d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583297"
---
# <a name="concatenation-operators-in-visual-basic"></a>Operátory řetězení v jazyce Visual Basic

Operátory zřetězení spojí více řetězců do jednoho řetězce. Existují dva operátory zřetězení, `+` a `&`. Obojí provede základní operaci zřetězení, jak ukazuje následující příklad.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

Tyto operátory mohou také zřetězit `String` proměnné, jak ukazuje následující příklad.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>Rozdíly mezi dvěma operátory zřetězení

[Operátor +](../../../../visual-basic/language-reference/operators/addition-operator.md) má primární účel přidání dvou čísel. Může však také zřetězit číselné operandy pomocí řetězcových operandů. Operátor `+` má komplexní sadu pravidel, která určuje, zda se má přidat, zřetězit, signalizovat chybu kompilátoru nebo vyvolat výjimku za běhu <xref:System.InvalidCastException>.

[Operátor &](../../../../visual-basic/language-reference/operators/concatenation-operator.md) je definován pouze pro `String` operandy a vždy rozšiřuje jeho operandy na `String`, bez ohledu na nastavení `Option Strict`. Operátor `&` je doporučen pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje pravděpodobnost vygenerování nezamýšlené konverze.

## <a name="performance-string-and-stringbuilder"></a>Výkon: String a StringBuilder

Pokud provedete velký počet manipulace s řetězcem, jako jsou zřetězení, odstranění a náhrady, váš výkon může být ziskem z <xref:System.Text.StringBuilder> třídy v oboru názvů <xref:System.Text>. Vytvoření a inicializace objektu <xref:System.Text.StringBuilder> a další instrukce pro převod konečné hodnoty na `String`, ale můžete tento čas obnovit, protože <xref:System.Text.StringBuilder> může provádět rychleji.

## <a name="see-also"></a>Viz také:

- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Typy metod manipulace s řetězci v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Aritmetické operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnávání v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Logické a bitové operátory v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
