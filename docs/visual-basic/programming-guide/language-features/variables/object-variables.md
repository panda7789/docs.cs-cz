---
title: Proměnné objektu
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351786"
---
# <a name="object-variables-in-visual-basic"></a>Proměnné objektu v jazyce Visual Basic

Kromě přímého ukládání hodnot proměnná může odkazovat na objekt. K proměnné přiřadíte objekt ze stejných důvodů, jako je přiřazení libovolné hodnoty k proměnné:

- Název proměnné je často kratší a snazší si pamatovat než úplnou cestu metod a vlastností potřebných pro přístup k objektu samotnému.

- Použití proměnné, která odkazuje na objekt, je efektivnější než opakované přístup k objektu prostřednictvím nezbytných metod nebo vlastností.

- Můžete změnit proměnnou tak, aby odkazovala na jiné objekty v době, kdy váš kód běží.

## <a name="making-code-shorter"></a>Kratší vytváření kódu

Můžete použít proměnné objektu pro zkrácení kódu, který je třeba zadat. Následující příklad používá úplnou cestu metod a vlastností pro přístup k objektu <xref:System.Windows.Forms.Control>.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Pokud použijete proměnnou objektu pro ovládací prvek, můžete tento kód zkrátit a zrychlit spouštění. Měli byste deklarovat objektovou proměnnou se specifickou třídou, kterou máte v úmyslu přiřadit (`Control` v tomto případě). Jakmile přiřadíte objekt proměnné, můžete s ní pracovat stejně, jako při zpracování objektu, na který odkazuje. Můžete nastavit nebo načíst vlastnosti objektu nebo použít kteroukoli z jeho metod. Následující příklad používá proměnnou objektu pro zjednodušení kódu v předchozím příkladu.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Viz také:

- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
