---
title: "Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms"
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
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e295e761f9ac0ec090bf950a67008d19cb350d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms
Můžete zajistit, aby uživatel ke změně uspořádání <xref:System.Windows.Forms.ToolStripItem> ovládací prvky na <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Chcete-li povolit ToolStripItem změnu uspořádání v době běhu  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> vlastnost `true`. Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> je `false`.  
  
     V době běhu uživatele obsahuje stisknutou klávesu ALT a levým tlačítkem myši přetáhněte <xref:System.Windows.Forms.ToolStripItem> do jiného umístění na <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Shrnutí technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
