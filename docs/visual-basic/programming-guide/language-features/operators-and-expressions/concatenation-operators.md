---
title: Operátory řetězení
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388787"
---
# <a name="concatenation-operators-in-visual-basic"></a>Operátory řetězení v jazyce Visual Basic

Operátory zřetězení spojí více řetězců do jednoho řetězce. Existují dva operátory zřetězení `+` a `&` . Obojí provede základní operaci zřetězení, jak ukazuje následující příklad.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

Tyto operátory mohou také zřetězit `String` proměnné, jak ukazuje následující příklad.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>Rozdíly mezi dvěma operátory zřetězení

[Operátor +](../../../language-reference/operators/addition-operator.md) má primární účel přidání dvou čísel. Může však také zřetězit číselné operandy pomocí řetězcových operandů. `+`Operátor má komplexní sadu pravidel, která určuje, zda se má přidat, zřetězit, signalizovat chybu kompilátoru nebo vyvolat výjimku za běhu <xref:System.InvalidCastException> .

[Operátor&](../../../language-reference/operators/concatenation-operator.md) je definován pouze pro `String` operandy a vždy rozšiřuje jeho operandy na `String` , bez ohledu na nastavení `Option Strict` . `&`Operátor je doporučen pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje pravděpodobnost vygenerování nezamýšlené konverze.

## <a name="performance-string-and-stringbuilder"></a>Výkon: String a StringBuilder

Pokud provedete velký počet manipulace s řetězcem, jako jsou zřetězení, odstranění a náhrady, váš výkon může být ziskem z <xref:System.Text.StringBuilder> třídy v <xref:System.Text> oboru názvů. Má navíc pokyn k vytvoření a inicializaci <xref:System.Text.StringBuilder> objektu a další instrukce pro převod konečné hodnoty na `String` , ale můžete tento čas obnovit, protože <xref:System.Text.StringBuilder> může být rychlejší.

## <a name="see-also"></a>Viz také

- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
- [Typy metod manipulace s řetězci v jazyce Visual Basic](../strings/types-of-string-manipulation-methods.md)
- [Aritmetické operátory v jazyce Visual Basic](arithmetic-operators.md)
- [Operátory porovnání v jazyce Visual Basic](comparison-operators.md)
- [Logické a bitové operátory v jazyce Visual Basic](logical-and-bitwise-operators.md)
