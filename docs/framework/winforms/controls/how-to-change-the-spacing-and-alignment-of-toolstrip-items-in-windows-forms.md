---
title: 'Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: c7a874659be8dbaec66b78e1e065bcbec21da3b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650879"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms
<xref:System.Windows.Forms.ToolStrip> Ovládací prvek plně podporuje rozložení funkce jako je například změna velikosti, mezery mezi <xref:System.Windows.Forms.ToolStripItem> řídí relativně vůči sobě navzájem, uspořádání ovládacích prvků na <xref:System.Windows.Forms.ToolStrip>a mezery ovládacích prvků vzhledem k <xref:System.Windows.Forms.ToolStrip>.  
  
 Protože výchozí hodnotu <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `true`, ovládací prvky se velikost automaticky, pokud nenastavíte <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Chcete-li ručně změnit velikost prvku ToolStripItem  
  
1. Nastavte <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `false` pro přidružený ovládací prvek.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Nastavte <xref:System.Windows.Forms.ToolStripItem.Size%2A> vlastnost tak, jak chcete, aby pro přidružený <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Nastavit mezery mezi ovládacího prvku ToolStripItem  
  
1. Vložit do požadované hodnoty v pixelech <xref:System.Windows.Forms.ToolStripItem.Margin%2A> vlastnost přidružený ovládací prvek.  
  
     Hodnoty <xref:System.Windows.Forms.ToolStripItem.Margin%2A> vlastnost určovat mezery mezi položkou a sousední položky v tomto pořadí: Vlevo, nahoře, vpravo a dole.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Chcete-li zarovnat ToolStripItem na pravé straně ovládacího prvku ToolStrip  
  
1. Nastavte <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pro přidružený ovládací prvek. Ve výchozím nastavení <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> je nastavena na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, který odpovídá ovládacích prvků na levé straně <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Chcete-li uspořádat ovládací prvek ToolStrip položek na ovládacím prvku ToolStrip  
  
- Nastavte <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastnost na hodnotu <xref:System.Windows.Forms.ToolStripLayoutStyle> , který chcete.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
