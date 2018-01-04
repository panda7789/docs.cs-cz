---
title: "Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5547b35bda8054b3ca41435e04855408d8a77c8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip
Když uživatel klikne na přepínací tlačítko, zobrazí se vyvýšených a vyvýšených vzhled uchová, dokud uživatel klikne na tlačítko znovu.  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>Chcete-li vytvořit toggling prvek ToolStripButton  
  
-   Použijte kód jako následující příklad kódu. Tento kód předpokládá, že formulář obsahuje <xref:System.Windows.Forms.ToolStrip> řízení a že jeho <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekce obsahuje <xref:System.Windows.Forms.ToolStripButton> názvem `toolStripButton1`. Také předpokládá, že máte obslužné rutiny události názvem `toolStripButton1_CheckedChanged`.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripButton>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
