---
title: 'Postup: Změna mezer a zarovnání položek panelu nástrojů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182233"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms
Ovládací <xref:System.Windows.Forms.ToolStrip> prvek plně podporuje funkce rozložení, jako je <xref:System.Windows.Forms.ToolStripItem> například velikost, mezery ovládacích <xref:System.Windows.Forms.ToolStrip>prvků vzhledem k sobě navzájem, uspořádání ovládacích prvků na , a mezery ovládacích prvků vzhledem <xref:System.Windows.Forms.ToolStrip>k .  
  
 Vzhledem k tomu, <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> `true`že výchozí hodnota vlastnosti je <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> , `false`ovládací prvky jsou velikosti automaticky, pokud nenastavíte vlastnost na .  
  
### <a name="to-manually-size-a-toolstripitem"></a>Ruční velikost položky ToolStripItem  
  
1. Nastavte <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `false` pro přidružený ovládací prvek.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Nastavte <xref:System.Windows.Forms.ToolStripItem.Size%2A> vlastnost požadovaným způsobem pro <xref:System.Windows.Forms.ToolStripItem>přidružené .  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Nastavení mezer položky ToolStripItem  
  
1. Vložte požadované hodnoty v obrazových <xref:System.Windows.Forms.ToolStripItem.Margin%2A> bodech do vlastnosti přidruženého ovládacího prvku.  
  
     Hodnoty vlastnosti <xref:System.Windows.Forms.ToolStripItem.Margin%2A> určují mezery mezi položkou a sousedními položkami v tomto pořadí: Vlevo, Nahoře, Vpravo a Dole.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Zarovnání položky ToolStripItem k pravé straně panelu nástrojů  
  
1. Nastavte <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pro přidružený ovládací prvek. Ve výchozím <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> nastavení <xref:System.Windows.Forms.ToolStripItemAlignment.Left>je nastavena na , která <xref:System.Windows.Forms.ToolStrip>zarovná ovládací prvky na levou stranu rozhraní .  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Uspořádání položek Panelu nástrojů na panelu nástrojů  
  
- Nastavte <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastnost na požadovanou hodnotu. <xref:System.Windows.Forms.ToolStripLayoutStyle>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip – přehled ovládacího prvku](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Souhrn technologie ToolStrip](toolstrip-technology-summary.md)
