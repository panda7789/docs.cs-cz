---
title: 'Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410500"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic

Proměnnou [datového typu objektu](../../../language-reference/data-types/object-data-type.md) deklarujete zadáním `As Object` v [příkazu Dim](../../../language-reference/statements/dim-statement.md). Objektu této proměnné přiřadíte umístěním objektu za znaménko rovná se ( `=` ) v příkazu přiřazení nebo v klauzuli inicializace.

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

## <a name="compile-the-code"></a>Kompilovat kód

Tento příklad vyžaduje:

- Odkaz na <xref:System> obor názvů.

- Třída, struktura nebo modul, do kterého se má příkaz Vložit `Dim` .

- Postup pro vložení příkazu přiřazení.

## <a name="see-also"></a>Viz také

- [Deklarace proměnné](variable-declaration.md)
- [Proměnné objektu](object-variables.md)
- [Deklarace proměnné objektu](object-variable-declaration.md)
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
- [Dim – příkaz](../../../language-reference/statements/dim-statement.md)
- [Odvození místního typu](local-type-inference.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
