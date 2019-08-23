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
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="4863f-102">Postupy: Povolit automatické dokončování v ovládacích prvcích ToolStrip v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4863f-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="4863f-103">Následující postup kombinuje <xref:System.Windows.Forms.ToolStripLabel> s a <xref:System.Windows.Forms.ToolStripComboBox> , který je možné vyřadit, aby zobrazoval seznam položek, například nedávno navštívené weby.</span><span class="sxs-lookup"><span data-stu-id="4863f-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="4863f-104">Pokud uživatel zadá znak, který se shoduje s prvním znakem jedné z položek v seznamu, položka se zobrazí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="4863f-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4863f-105">Automatické dokončování funguje `ToolStrip` s ovládacími prvky stejným způsobem, jako pracují s tradičními ovládacími <xref:System.Windows.Forms.TextBox>prvky, jako jsou <xref:System.Windows.Forms.ComboBox> a.</span><span class="sxs-lookup"><span data-stu-id="4863f-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="4863f-106">Povolení automatického dokončování v ovládacím prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4863f-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1. <span data-ttu-id="4863f-107"><xref:System.Windows.Forms.ToolStrip> Vytvořte ovládací prvek a přidejte do něj položky.</span><span class="sxs-lookup"><span data-stu-id="4863f-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
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
  
2. <span data-ttu-id="4863f-108">Nastavte vlastnost popisku a pole se seznamem na <xref:System.Windows.Forms.ToolStripItemOverflow.Never> tak, aby byl seznam vždy dostupný bez ohledu na velikost formuláře. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A></span><span class="sxs-lookup"><span data-stu-id="4863f-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
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
  
3. <span data-ttu-id="4863f-109">Přidejte slova do kolekce <xref:System.Windows.Forms.ToolStripComboBox> Items ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4863f-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. <span data-ttu-id="4863f-110">Nastavte vlastnost pole se seznamem na <xref:System.Windows.Forms.AutoCompleteMode.Append>. <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A></span><span class="sxs-lookup"><span data-stu-id="4863f-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. <span data-ttu-id="4863f-111">Nastavte vlastnost pole se seznamem na <xref:System.Windows.Forms.AutoCompleteSource.ListItems>. <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A></span><span class="sxs-lookup"><span data-stu-id="4863f-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4863f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4863f-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [<span data-ttu-id="4863f-113">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4863f-113">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="4863f-114">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4863f-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="4863f-115">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4863f-115">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
