---
title: 'Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 1b41699d8da1c99705f6796105dab6f3ab1d727d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341631"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)
V některých aplikacích druh podřízené okno rozhraní více dokumentů (MDI) může lišit od nadřazeného okna MDI. Například nadřazený objekt MDI může být tabulku a podřízený formulář MDI může být grafu. V takovém případě budete chtít aktualizovat obsah nabídky nadřazený objekt MDI obsah nabídky podřízený formulář MDI jako podřízená okna MDI různé druhy se aktivují.  
  
 Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete vložit skupinu položek nabídky v nabídce podřízeného MDI do části rozevíracího seznamu MDI nadřazené nabídky. Zavření podřízené okno MDI odebere položky vložené nabídky z nadřazený objekt MDI.  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>K vložení prvku MenuStrip do rozevíracího seznamu MDI  
  
1. Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2. Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavit <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
3. Přidání položky do nabídek nejvyšší úrovně `Form1`<xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.  
  
4. Přidejte tři položky podnabídky do `&File` položky nabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Open`, `&Import from`, a `E&xit`.  
  
5. Přidání dvou položek podnabídky do `&Import from` položku podnabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Word` a `&Excel`.  
  
6. Přidání formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2`<xref:System.Windows.Forms.MenuStrip> k `true`.  
  
7. Přidání položky do nabídek nejvyšší úrovně `Form2`<xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&File`.  
  
8. Přidat podnabídku položky, které chcete `&File` nabídku `Form2` v následujícím pořadí: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`a další <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Nastavte <xref:System.Windows.Forms.MergeAction> a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti `Form2` položky nabídky, jak je znázorněno v následující tabulce.  
  
    |Položka nabídky Form2|Hodnota MergeAction|Hodnota MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Soubor|MatchOnly|-1|  
    |Oddělovač|Insert|2|  
    |Uložit|Insert|3|  
    |Uložit a zavřít|Insert|4|  
    |Oddělovač|Insert|5|  
  
10. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
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
  
12. Umístit podobně jako v následujícím příkladu kódu v kódu `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> zaregistrovat obslužnou rutinu události.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření nadřazených formulářů MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
