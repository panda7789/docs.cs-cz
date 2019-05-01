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
ms.openlocfilehash: e688e9a220e6c82caa2d107589b5ca9a1e59e72b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052154"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip
Když uživatel klikne na tlačítko přepínací tlačítko, se zobrazí vmáčknuté a zachová vmáčknuté vzhled, dokud uživatel neklikne na tlačítko znovu.  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>Chcete-li vytvořit toggling ovládací prvek ToolStripButton  
  
- Použijte kód jako v následujícím příkladu kódu. Tento kód předpokládá, že váš formulář obsahuje <xref:System.Windows.Forms.ToolStrip> ovládacího prvku a že jeho <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekce obsahuje <xref:System.Windows.Forms.ToolStripButton> volá `toolStripButton1`. Dále předpokládá, že máte volá obslužná rutina události `toolStripButton1_CheckedChanged`.  
  
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
