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
ms.openlocfilehash: db411023ad624e4c3d60b09bdbd588c85f8e22d1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745501"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Postupy: Povolení AutoComplete v ovládacích prvcích ToolStrip ve Windows Forms
Následující postup kombinuje <xref:System.Windows.Forms.ToolStripLabel> s <xref:System.Windows.Forms.ToolStripComboBox>, které je možné vyřadit, aby se zobrazil seznam položek, například nedávno navštívené weby. Pokud uživatel zadá znak, který se shoduje s prvním znakem jedné z položek v seznamu, položka se zobrazí okamžitě.  
  
> [!NOTE]
> Automatické dokončování funguje s ovládacími prvky `ToolStrip` stejným způsobem jako s tradičními ovládacími prvky, jako jsou <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Povolení automatického dokončování v ovládacím prvku ToolStrip  
  
1. Vytvořte ovládací prvek <xref:System.Windows.Forms.ToolStrip> a přidejte do něj položky.  
  
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
  
2. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> popisku a pole se seznamem na <xref:System.Windows.Forms.ToolStripItemOverflow.Never> tak, aby byl seznam vždy dostupný bez ohledu na velikost formuláře.  
  
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
  
3. Přidejte slova do kolekce Items ovládacího prvku <xref:System.Windows.Forms.ToolStripComboBox>.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Vlastnost <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> pole se seznamem nastavte na hodnotu <xref:System.Windows.Forms.AutoCompleteMode.Append>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Vlastnost <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> pole se seznamem nastavte na hodnotu <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
