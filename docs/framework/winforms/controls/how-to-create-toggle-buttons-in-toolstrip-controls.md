---
title: 'Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972354"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip

Když uživatel klikne na přepínací tlačítko, zobrazí se vmáčknutý a zůstane zobrazený vmáčknutý, dokud uživatel znovu neklikne na tlačítko.

## <a name="to-create-a-toggling-toolstripbutton"></a>Vytvoření přepínání prvek ToolStripButton

- Použijte kód, jako je například následující příklad kódu. Tento kód předpokládá, <xref:System.Windows.Forms.ToolStrip> že formulář obsahuje ovládací prvek a že jeho <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekce obsahuje <xref:System.Windows.Forms.ToolStripButton> volání `toolStripButton1`. Také předpokládá, že máte volanou `toolStripButton1_CheckedChanged`obslužnou rutinu události.

    ```vb
    toolStripButton1.CheckOnClick = True
    toolStripButton1.CheckedChanged AddressOf _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

    ```csharp
    toolStripButton1.CheckOnClick = true;
    toolStripButton1.CheckedChanged += new _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStripButton>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
