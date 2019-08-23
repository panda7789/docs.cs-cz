---
title: 'Postupy: Povolit automatické dokončování v ovládacích prvcích ToolStrip v model Windows Forms'
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
ms.openlocfilehash: 301f1b156bbaee5c5f7be95e972ee1ebaa83777f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963612"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Postupy: Povolit automatické dokončování v ovládacích prvcích ToolStrip v model Windows Forms
Následující postup kombinuje <xref:System.Windows.Forms.ToolStripLabel> s a <xref:System.Windows.Forms.ToolStripComboBox> , který je možné vyřadit, aby zobrazoval seznam položek, například nedávno navštívené weby. Pokud uživatel zadá znak, který se shoduje s prvním znakem jedné z položek v seznamu, položka se zobrazí okamžitě.  
  
> [!NOTE]
> Automatické dokončování funguje `ToolStrip` s ovládacími prvky stejným způsobem, jako pracují s tradičními ovládacími <xref:System.Windows.Forms.TextBox>prvky, jako jsou <xref:System.Windows.Forms.ComboBox> a.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Povolení automatického dokončování v ovládacím prvku ToolStrip  
  
1. <xref:System.Windows.Forms.ToolStrip> Vytvořte ovládací prvek a přidejte do něj položky.  
  
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
  
2. Nastavte vlastnost popisku a pole se seznamem na <xref:System.Windows.Forms.ToolStripItemOverflow.Never> tak, aby byl seznam vždy dostupný bez ohledu na velikost formuláře. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
  
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
  
4. Nastavte vlastnost pole se seznamem na <xref:System.Windows.Forms.AutoCompleteMode.Append>. <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Nastavte vlastnost pole se seznamem na <xref:System.Windows.Forms.AutoCompleteSource.ListItems>. <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>  
  
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
