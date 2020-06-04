---
title: Proměnné objektu
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410332"
---
# <a name="object-variables-in-visual-basic"></a>Proměnné objektu v jazyce Visual Basic

Kromě přímého ukládání hodnot proměnná může odkazovat na objekt. K proměnné přiřadíte objekt ze stejných důvodů, jako je přiřazení libovolné hodnoty k proměnné:

- Název proměnné je často kratší a snazší si pamatovat než úplnou cestu metod a vlastností potřebných pro přístup k objektu samotnému.

- Použití proměnné, která odkazuje na objekt, je efektivnější než opakované přístup k objektu prostřednictvím nezbytných metod nebo vlastností.

- Můžete změnit proměnnou tak, aby odkazovala na jiné objekty v době, kdy váš kód běží.

## <a name="making-code-shorter"></a>Kratší vytváření kódu

Můžete použít proměnné objektu pro zkrácení kódu, který je třeba zadat. Následující příklad používá úplnou cestu metod a vlastností pro přístup k <xref:System.Windows.Forms.Control> objektu.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Pokud použijete proměnnou objektu pro ovládací prvek, můžete tento kód zkrátit a zrychlit spouštění. Měli byste deklarovat objektovou proměnnou se specifickou třídou, kterou máte v úmyslu přiřadit ( `Control` v tomto případě). Jakmile přiřadíte objekt proměnné, můžete s ní pracovat stejně, jako při zpracování objektu, na který odkazuje. Můžete nastavit nebo načíst vlastnosti objektu nebo použít kteroukoli z jeho metod. Následující příklad používá proměnnou objektu pro zjednodušení kódu v předchozím příkladu.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Viz také

- [Deklarace proměnné](variable-declaration.md)
- [Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Deklarace proměnné objektu](object-variable-declaration.md)
- [Přiřazení proměnné objektu](object-variable-assignment.md)
- [Hodnoty proměnné objektu](object-variable-values.md)
