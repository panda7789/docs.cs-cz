---
title: 'Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: d70418c6d8a626fd3ef54161086b24655037b086
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612843"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI (Windows Forms)
V některých aplikacích druh podřízené okno rozhraní více dokumentů (MDI) může lišit od nadřazeného okna MDI. Například nadřazený objekt MDI může být tabulku a podřízený formulář MDI může být grafu. V takovém případě budete chtít aktualizovat obsah nabídky nadřazený objekt MDI obsah nabídky podřízený formulář MDI jako podřízená okna MDI různé druhy se aktivují.  
  
 Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete připojit k nadřazené nabídky MDI podřízené nabídky MDI. Zavření podřízené okno MDI odebere připojený nabídku z nadřazený objekt MDI.  
  
 Viz také [aplikace rozhraní více dokumentů (MDI)](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Připojit položky nabídky nadřazený objekt MDI  
  
1. Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2. Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavit <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
3. Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `Form1` <xref:System.Windows.Forms.MenuStrip> k `false`.  
  
4. Přidání položky do nabídek nejvyšší úrovně `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.  
  
5. Přidat podnabídku položku `&File` položky nabídky a nastavte jeho <xref:System.Windows.Forms.Form.Text%2A> vlastnost `&Open`.  
  
6. Přidání formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
7. Přidání položky do nabídek nejvyšší úrovně `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Form.Text%2A> vlastnost `&Special`.  
  
8. Přidání dvou položek podnabídky do `&Special` položky nabídky a nastavte jejich <xref:System.Windows.Forms.Form.Text%2A> vlastností `Command&1` a `Command&2`v uvedeném pořadí.  
  
9. Nastavte <xref:System.Windows.Forms.MergeAction> vlastnost `&Special`, `Command&1`, a `Command&2` položky nabídky <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`.  
  
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
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
- A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.  
  
- Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.
