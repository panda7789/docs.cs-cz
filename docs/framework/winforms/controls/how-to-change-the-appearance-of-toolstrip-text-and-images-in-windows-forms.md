---
title: "Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms"
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
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe88ff8d31a83b8516b11cd9aadd4bc2d4bf99a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms
Můžete řídit, jestli na zobrazení textu a obrázků <xref:System.Windows.Forms.ToolStripItem> a jakým způsobem je zarovnán relativně k sobě navzájem a <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Chcete-li definovat, co se zobrazí na ToolStripItem  
  
-   Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na požadovanou hodnotu. Možnosti jsou `Image`, `ImageAndText`, `None`, a `Text`. Výchozí hodnota je `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Chcete-li zarovnat text na ToolStripItem  
  
-   Nastavte <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> vlastnost na požadovanou hodnotu. Možnosti jsou libovolnou kombinaci nejvyšší, střední a dolní s vlevo, na střed a doprava. Výchozí hodnota je `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Chcete-li zarovnat bitové kopie v prvku ToolStripItem  
  
-   Nastavte <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> vlastnost na požadovanou hodnotu. Možnosti jsou libovolnou kombinaci nejvyšší, střední a dolní s vlevo, na střed a doprava. Výchozí hodnota je `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Chcete-li definovat zobrazení ToolStripItem textu a obrázků relativně k sobě navzájem  
  
-   Nastavte <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> vlastnost na požadovanou hodnotu. Možnosti jsou `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, a `TextBeforeImage`. Výchozí hodnota je `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Shrnutí technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
