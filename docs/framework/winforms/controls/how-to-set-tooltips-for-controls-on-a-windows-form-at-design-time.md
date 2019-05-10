---
title: 'Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211688"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu

Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrháři formulářů Windows v sadě Visual Studio. Další informace o <xref:System.Windows.Forms.ToolTip> komponenty, naleznete v tématu [ToolTip – přehled komponenty](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Popis nastavit prostřednictvím kódu programu

1. Přidejte ovládací prvek, který se zobrazí popisek.

2. Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.

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

## <a name="set-a-tooltip-in-the-designer"></a>Popis nastavit v Návrháři

1. V sadě Visual Studio, přidejte <xref:System.Windows.Forms.ToolTip> komponentu do formuláře.

2. Vyberte ovládací prvek, který zobrazí popis tlačítka, nebo ho přidejte do formuláře.

3. V **vlastnosti** okno, nastaveno **popisu tlačítka ToolTip1** hodnota, která má odpovídající řetězec textu.

### <a name="to-remove-a-tooltip-programmatically"></a>Chcete-li odebrat popisek prostřednictvím kódu programu

1. Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.

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

## <a name="remove-a-tooltip-in-the-designer"></a>Odebrat popisek v Návrháři

1. V sadě Visual Studio vyberte ovládací prvek, který se zobrazuje v popisku.

2. V **vlastnosti** okna, odstraníte tím stávající text v **popisu tlačítka ToolTip1**.

## <a name="see-also"></a>Viz také:

- [Přehled komponenty ToolTip](tooltip-component-overview-windows-forms.md)
- [Postupy: Změna zpoždění komponenty Windows Forms ToolTip](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [Komponenta ToolTip](tooltip-component-windows-forms.md)
