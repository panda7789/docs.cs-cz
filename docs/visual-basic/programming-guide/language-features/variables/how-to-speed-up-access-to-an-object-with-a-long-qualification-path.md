---
title: 'Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631096"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací (Visual Basic)

Pokud často přistupujete k objektu, který vyžaduje cestu kvalifikace několika metod a vlastností, můžete kód urychlit tak, že neopakujete cestu kvalifikace.

Existují dva způsoby, jak se vyhnout opakování cesty kvalifikace. Objekt můžete přiřadit proměnné nebo ho můžete použít v `With`... `End With` blok.

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Urychlení přístupu k silně kvalifikovanému objektu přiřazením k proměnné

1. Deklarujte proměnnou typu objektu, ke kterému se často přistupuje. Zadejte cestu kvalifikace v části inicializace deklarace.

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. Pro přístup ke členům objektu použijte proměnnou.

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Chcete-li zrychlit přístup k silně kvalifikovanému objektu pomocí s... Ukončit s blokem

1. Zadejte cestu kvalifikace do `With` příkazu.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. Před příkazem přistoupit k členům objektu `With` uvnitř bloku. `End With`

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Příkaz With...End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
