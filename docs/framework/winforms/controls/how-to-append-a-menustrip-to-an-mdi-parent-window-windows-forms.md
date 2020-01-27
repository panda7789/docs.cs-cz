---
title: 'Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747153"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI (Windows Forms)
V některých aplikacích se může v nadřazeném okně MDI lišit druh podřízeného okna rozhraní MDI (Multiple Document Interface). Nadřazený objekt MDI může být například tabulka a podřízená položka MDI může být graf. V takovém případě chcete aktualizovat obsah nabídky nadřazeného objektu MDI s obsahem nabídky podřízeného objektu MDI, protože jsou aktivována podřízená okna MDI různých druhů.  
  
 Následující postup používá vlastnosti <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> k připojení podřízené nabídky MDI do nadřazené nabídky MDI. Zavřením podřízeného okna MDI dojde k odebrání připojené nabídky z nadřazeného objektu MDI.  
  
 Viz také [aplikace MDI (Multiple Document Interface)](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Postup připojení položky nabídky k nadřazené položce MDI  
  
1. Vytvořte formulář a nastavte jeho vlastnost <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.  
  
2. Přidejte <xref:System.Windows.Forms.MenuStrip> do `Form1` a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.  
  
3. Vlastnost <xref:System.Windows.Forms.ToolStripItem.Visible%2A> `Form1`<xref:System.Windows.Forms.MenuStrip> nastavte na `false`.  
  
4. Přidejte položku nabídky nejvyšší úrovně do `Form1`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.Control.Text%2A> na `&File`.  
  
5. Přidejte položku podnabídky do položky nabídky `&File` a nastavte její vlastnost <xref:System.Windows.Forms.Form.Text%2A> na `&Open`.  
  
6. Přidejte do projektu formulář, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`ho <xref:System.Windows.Forms.MenuStrip> na `true`.  
  
7. Přidejte položku nabídky nejvyšší úrovně do `Form2`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.Form.Text%2A> na `&Special`.  
  
8. Přidejte dvě položky podnabídky do položky nabídky `&Special` a nastavte jejich vlastnosti <xref:System.Windows.Forms.Form.Text%2A> na `Command&1` a `Command&2`, v uvedeném pořadí.  
  
9. Nastavte vlastnost <xref:System.Windows.Forms.MergeAction> položek nabídky `&Special`, `Command&1`a `Command&2` na <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. V rámci obslužné rutiny události vložte kód podobný následujícímu příkladu kódu pro vytvoření a zobrazení nových instancí `Form2` jako podřízených objektů MDI `Form1`.  
  
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
  
12. Umístěte kód podobný následujícímu příkladu kódu v `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
- <xref:System.Windows.Forms.MenuStrip> ovládací prvek `Form1` s názvem `menuStrip1`a ovládací prvek <xref:System.Windows.Forms.MenuStrip> na `Form2` s názvem `menuStrip2`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.
