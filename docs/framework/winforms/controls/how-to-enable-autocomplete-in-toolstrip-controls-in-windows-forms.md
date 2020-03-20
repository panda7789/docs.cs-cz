---
title: 'Postupy: Povolení AutoComplete v ovládacích prvcích ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: 18b17aaea9d2354c03bb43f3fdd8d3779697cf58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142015"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Postupy: Povolení AutoComplete v ovládacích prvcích ToolStrip ve Windows Forms
Následující postup kombinuje <xref:System.Windows.Forms.ToolStripLabel> s <xref:System.Windows.Forms.ToolStripComboBox> a, které mohou být vynechány dolů zobrazit seznam položek, jako jsou například nedávno navštívené weby. Pokud uživatel zadá znak, který odpovídá prvnímu znaku jedné z položek v seznamu, položka se okamžitě zobrazí.  
  
> [!NOTE]
> Automatické dokončování pracuje s `ToolStrip` ovládacími prvky <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.TextBox>stejným způsobem, jako pracuje s tradičními ovládacími prvky, jako jsou například a .  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Povolení automatického dokončování v ovládacím prvku ToolStrip  
  
1. Vytvořte <xref:System.Windows.Forms.ToolStrip> ovládací prvek a přidejte do něj položky.  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2. Nastavte <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> vlastnost popisku a pole se <xref:System.Windows.Forms.ToolStripItemOverflow.Never> seznamem tak, aby byl seznam vždy k dispozici bez ohledu na velikost formuláře.  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3. Přidejte slova do kolekce <xref:System.Windows.Forms.ToolStripComboBox> Items ovládacího prvku.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Nastavte <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> vlastnost pole se seznamem na <xref:System.Windows.Forms.AutoCompleteMode.Append>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Nastavte <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> vlastnost pole se seznamem na <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [ToolStrip – přehled ovládacího prvku](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Souhrn technologie ToolStrip](toolstrip-technology-summary.md)
