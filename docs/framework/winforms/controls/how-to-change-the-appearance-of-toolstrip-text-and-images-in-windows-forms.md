---
title: 'Postupy: Změna vzhledu textu a obrázků ToolStrip'
ms.date: 03/30/2017
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
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746605"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms
Můžete určit, zda se text a obrázky zobrazí na <xref:System.Windows.Forms.ToolStripItem> a jak jsou zarovnány relativně k sobě navzájem a <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Definování obsahu zobrazeného na ToolStripItem  
  
- Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na požadovanou hodnotu. Možnosti jsou `Image`, `ImageAndText`, `None`a `Text`. Výchozí formát je `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Zarovnání textu v prvku ToolStripItem  
  
- Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> na požadovanou hodnotu. Možnosti jsou jakékoli kombinace horní, prostřední a dolní části s levou, střední a pravou. Výchozí formát je `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Zarovnání obrázku v prvku ToolStripItem  
  
- Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> na požadovanou hodnotu. Možnosti jsou jakékoli kombinace horní, prostřední a dolní části s levou, střední a pravou. Výchozí formát je `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Definování způsobu vzájemného zobrazení textu a obrázků prvku ToolStripItem  
  
- Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> na požadovanou hodnotu. Tyto možnosti jsou `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`a `TextBeforeImage`. Výchozí formát je `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStrip>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
