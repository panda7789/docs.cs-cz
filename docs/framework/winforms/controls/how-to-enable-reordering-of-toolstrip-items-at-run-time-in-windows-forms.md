---
title: 'Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms'
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
ms.openlocfilehash: 0800acc955ff8cf9efa7bc183f10d2b5cc87aac6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713710"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Postupy: Povolení změny pořadí položek ToolStrip za běhu ve Windows Forms
Můžete povolit uživatelům změnit uspořádání <xref:System.Windows.Forms.ToolStripItem> ovládací prvky na <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Aby ovládací prvek ToolStripItem změny uspořádání v době běhu  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> vlastnost `true`. Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> je `false`.  
  
     V době běhu uživatele obsahuje stisknutou klávesu ALT a levé tlačítko myši přetáhněte <xref:System.Windows.Forms.ToolStripItem> do jiného umístění v <xref:System.Windows.Forms.ToolStrip>.  
  
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
