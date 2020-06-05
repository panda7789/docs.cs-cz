---
title: 'Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: fe93e7bac2a21f1060d1f93765eb35e1ad0c7eb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410409"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací (Visual Basic)

Pokud často přistupujete k objektu, který vyžaduje cestu kvalifikace několika metod a vlastností, můžete kód urychlit tak, že neopakujete cestu kvalifikace.

Existují dva způsoby, jak se vyhnout opakování cesty kvalifikace. Objekt můžete přiřadit proměnné nebo ho můžete použít v `With` bloku.... `End With`

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

2. Před příkazem přistoupit k členům objektu uvnitř `With` bloku `End With` .

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Viz také

- [Proměnné objektu](object-variables.md)
- [With...End With – příkaz](../../../language-reference/statements/with-end-with-statement.md)
