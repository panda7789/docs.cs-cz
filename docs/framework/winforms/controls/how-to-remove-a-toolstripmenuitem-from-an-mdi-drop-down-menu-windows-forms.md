---
title: 'Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: c650f8a26629d942aa4ccf0066aee6af4b51f8b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632059"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)
V některých aplikacích druh podřízené okno rozhraní více dokumentů (MDI) může lišit od nadřazeného okna MDI. Například nadřazený objekt MDI může být tabulku a podřízený formulář MDI může být grafu. V takovém případě budete chtít aktualizovat obsah nabídky nadřazený objekt MDI obsah nabídky podřízený formulář MDI jako podřízená okna MDI různé druhy se aktivují.  
  
 Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete odebrat položku nabídky z část rozevíracího seznamu MDI nadřazené nabídky. Zavření podřízené okno MDI obnoví položky nabídky odebrané do nadřazené nabídky MDI.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Chcete-li odebrat prvku MenuStrip z rozevíracího seznamu MDI  
  
1.  Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2.  Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavit <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
3.  Přidání položky do nabídek nejvyšší úrovně `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.  
  
4.  Přidejte tři položky podnabídky do `&File` položky nabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Open`, `&Import from`, a `E&xit`.  
  
5.  Přidání dvou položek podnabídky do `&Import from` položku podnabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Word` a `&Excel`.  
  
6.  Přidání formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
7.  Přidání položky do nabídek nejvyšší úrovně `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&File`.  
  
8.  Přidat `&Import from` podnabídky položku `&File` nabídku `Form2`a přidejte `&Word` položky podnabídky a `&File` nabídky.  
  
9. Nastavte <xref:System.Windows.Forms.MergeAction> a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti `Form2` položky nabídky, jak je znázorněno v následující tabulce.  
  
    |Položka nabídky Form2|Hodnota MergeAction|Hodnota MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Soubor|MatchOnly|-1|  
    |Importovat z|MatchOnly|-1|  
    |Word|odebrat|-1|  
  
10. V `Form1`, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`:  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. Umístit podobně jako v následujícím příkladu kódu v kódu `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> zaregistrovat obslužnou rutinu události.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
