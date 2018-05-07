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
ms.openlocfilehash: 7951a545fd8cbd0ae30907922551216161171a8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms
<xref:System.Windows.Forms.ToolStrip> Řízení plně podporuje rozložení funkce jako je například změna velikosti, mezery mezi <xref:System.Windows.Forms.ToolStripItem> na ovládací prvky relativně k sobě navzájem, uspořádání ovládacích prvků <xref:System.Windows.Forms.ToolStrip>a mezery mezi ovládací prvky vzhledem k <xref:System.Windows.Forms.ToolStrip>.  
  
 Protože výchozí hodnota <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost je `true`, ovládací prvky jsou automaticky dimenzované, není-li nastavena <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost, která má `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Chcete-li ručně velikost ToolStripItem  
  
1.  Nastavte <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `false` pro související ovládací prvek.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Size%2A> vlastnost způsob, jakým chcete pro přidruženého <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Chcete-li nastavit mezery mezi ToolStripItem  
  
1.  Příkaz Insert požadované hodnoty v pixelech <xref:System.Windows.Forms.ToolStripItem.Margin%2A> vlastnosti přidruženého ovládacího prvku.  
  
     Hodnoty <xref:System.Windows.Forms.ToolStripItem.Margin%2A> vlastnost určovat mezery mezi položkou a u položky v tomto pořadí: vlevo, horní, pravé a dolní.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Chcete-li zarovnat ToolStripItem na pravé straně ovládacího prvku ToolStrip  
  
1.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pro související ovládací prvek. Ve výchozím nastavení <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> je nastaven na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, který Zarovná ovládací prvky na levé straně <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>K uspořádání položek ToolStrip v ovládacím prvku ToolStrip  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastnost na hodnotu <xref:System.Windows.Forms.ToolStripLayoutStyle> , které chcete.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Shrnutí technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
