---
title: 'Postupy: deklarace objektové proměnné a přiřazení objektu k němu'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: eaaeda2a986584e6e1a2e0d2cda3890fb6187598
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344238"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic

Proměnnou [datového typu objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) deklarujete zadáním `As Object` v [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Objektu této proměnné přiřadíte umístěním objektu za znaménko rovná se (`=`) v příkazu přiřazení nebo v klauzuli inicializace.

## <a name="example"></a>Příklad

Následující příklad deklaruje `Object` proměnnou a přiřadí k ní aktuální instanci.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

Můžete zkombinovat deklaraci a přiřazení inicializací proměnné jako součást její deklarace. Následující příklad je ekvivalentní k předchozímu příkladu.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a>Kompilace kódu

Tento příklad vyžaduje:

- Odkaz na obor názvů <xref:System>.

- Třída, struktura nebo modul, do kterého se má vložit příkaz `Dim`.

- Postup pro vložení příkazu přiřazení.

## <a name="see-also"></a>Viz také:

- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
