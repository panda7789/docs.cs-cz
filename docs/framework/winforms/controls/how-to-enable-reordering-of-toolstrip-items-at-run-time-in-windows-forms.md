---
title: 'Postupy: Povolení změny pořadí položek ToolStrip za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: 44b52bf997819f090569d08eb395d8af18f61370
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745486"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms
Můžete uživateli povolit změnu uspořádání <xref:System.Windows.Forms.ToolStripItem> ovládacích prvků na <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Povolení změny uspořádání ToolStripItem v době běhu  
  
- Nastavte <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> vlastnost `true`. Ve výchozím nastavení je <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> `false`.  
  
     V době běhu uživatel drží klávesu ALT a levé tlačítko myši k přetažení <xref:System.Windows.Forms.ToolStripItem> do jiného umístění v <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
