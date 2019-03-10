---
title: 'Postupy: Povolení AutoComplete v ovládacích prvcích ToolStrip ve Windows Forms'
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
ms.openlocfilehash: 0e44b2944a24ea4201fda2f0891d74c672a64a4a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718933"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Postupy: Povolení AutoComplete v ovládacích prvcích ToolStrip ve Windows Forms
Následující postup kombinuje <xref:System.Windows.Forms.ToolStripLabel> s <xref:System.Windows.Forms.ToolStripComboBox> , který může být rozbalil zobrazíte seznam položek, jako například naposledy navštívené webové stránky. Pokud uživatel zadá znak, který odpovídá jedné z položek v seznamu první znak, zobrazí se okamžitě položky.  
  
> [!NOTE]
>  Automatické dokončování funguje s `ToolStrip` ovládací prvky stejným způsobem, který funguje s tradiční ovládací prvky, jako například <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>K povolení AutoComplete v ovládacím prvku ToolStrip  
  
1.  Vytvoření <xref:System.Windows.Forms.ToolStrip> ovládací prvek a přidat položky do něj.  
  
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
  
2.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> vlastnost popisek a do pole se seznamem <xref:System.Windows.Forms.ToolStripItemOverflow.Never> tak, aby byla vždy dostupná bez ohledu na velikost formuláře seznamu.  
  
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
  
3.  Přidat do kolekce položek slova <xref:System.Windows.Forms.ToolStripComboBox> ovládacího prvku.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4.  Nastavte <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> vlastnost poli se seznamem <xref:System.Windows.Forms.AutoCompleteMode.Append>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5.  Nastavte <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> vlastnost poli se seznamem <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.  
  
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
