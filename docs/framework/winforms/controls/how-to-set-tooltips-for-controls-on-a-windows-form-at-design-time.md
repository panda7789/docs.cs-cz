---
title: 'Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu'
description: Naučte se, jak nastavit popisy tlačítek pro ovládací prvky programově nebo v Návrhář formulářů v sadě Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325970"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Postupy: Nastavení popisků pro ovládací prvky ve formuláři Windows v době návrhu

Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrhář formulářů v sadě Visual Studio. Další informace o <xref:System.Windows.Forms.ToolTip> komponentě najdete v tématu [Přehled komponent ToolTip](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Programové nastavení popisu

1. Přidejte ovládací prvek, který zobrazí popisek.

2. Použijte <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a>Nastavení popisu v Návrháři

1. V aplikaci Visual Studio přidejte <xref:System.Windows.Forms.ToolTip> komponentu do formuláře.

2. Vyberte ovládací prvek, který zobrazí popisek, nebo jej přidejte do formuláře.

3. V okně **Vlastnosti nastavte vlastnost** **ToolTip na hodnotu ToolTip1** na příslušný textový řetězec.

### <a name="to-remove-a-tooltip-programmatically"></a>Postup pro odebrání popisku pomocí kódu programu

1. Použijte <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a>Odebrání popisu v Návrháři

1. V aplikaci Visual Studio vyberte ovládací prvek, který zobrazuje popis tlačítka.

2. V okně **vlastnosti** odstraňte text v **popisku v ToolTip1**.

## <a name="see-also"></a>Viz také

- [ToolTip – přehled komponenty](tooltip-component-overview-windows-forms.md)
- [Postupy: Změna zpoždění komponenty Windows Forms ToolTip](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [Komponenta ToolTip](tooltip-component-windows-forms.md)
