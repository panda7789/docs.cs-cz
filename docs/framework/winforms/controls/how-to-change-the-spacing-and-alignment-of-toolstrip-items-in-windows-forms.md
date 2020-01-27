---
title: 'Postupy: Změna mezer a zarovnání položek ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746561"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms
Ovládací prvek <xref:System.Windows.Forms.ToolStrip> plně podporuje funkce rozložení, jako je například velikost, rozestup <xref:System.Windows.Forms.ToolStripItem>ch ovládacích prvků, které jsou vzájemně relativní, uspořádání ovládacích prvků na <xref:System.Windows.Forms.ToolStrip>a mezery mezi ovládacími prvky relativními k <xref:System.Windows.Forms.ToolStrip>.  
  
 Vzhledem k tomu, že je výchozí hodnota vlastnosti <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> `true`, mají ovládací prvky velikost automaticky, pokud nenastavíte vlastnost <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> na `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Ruční změna velikosti prvku ToolStripItem  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> na `false` pro přidružený ovládací prvek.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Vlastnost <xref:System.Windows.Forms.ToolStripItem.Size%2A> nastavte tak, jak chcete pro související <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Nastavení mezer ovládacího prvku ToolStripItem  
  
1. Vložte požadované hodnoty (v pixelech) do vlastnosti <xref:System.Windows.Forms.ToolStripItem.Margin%2A> přidruženého ovládacího prvku.  
  
     Hodnoty vlastnosti <xref:System.Windows.Forms.ToolStripItem.Margin%2A> určují mezery mezi položkou a sousedními položkami v tomto pořadí: vlevo, nahoře, vpravo a dole.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Zarovnání prvku ToolStripItem na pravou stranu ovládacího prvku ToolStrip  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> na <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pro přidružený ovládací prvek. Ve výchozím nastavení je <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> nastavena na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, která zarovnává ovládací prvky na levou stranu <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Uspořádání položek ToolStrip na ovládacím prvku ToolStrip  
  
- Vlastnost <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> nastavte na hodnotu <xref:System.Windows.Forms.ToolStripLayoutStyle>, kterou požadujete.  
  
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
