---
title: 'Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: bfe84ccb30b13b8232172749454bf8f3625269ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139201"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)
Můžete vytvářet aplikace, které můžete otevřít několik dokumentů ve stejný čas a zkopírujte a vložte obsah z jednoho dokumentu do jiné rozhraní více dokumentů (MDI).  
  
 Tento postup ukazuje, jak vytvořit seznam všech aktivních podřízených formulářů v nabídce okno nadřazeného objektu.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Vytvoření seznamu okna MDI v prvku MenuStrip  
  
1.  Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2.  Přidat <xref:System.Windows.Forms.MenuStrip> do formuláře.  
  
3.  Přidání dvou položek nabídek nejvyšší úrovně na <xref:System.Windows.Forms.MenuStrip> a nastavte jejich <xref:System.Windows.Forms.Control.Text%2A> vlastností `&File` a `&Window`.  
  
4.  Přidat podnabídku položku `&File` položky nabídky a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&Open`.  
  
5.  Nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Přidat formuláře do projektu a přidejte ovládací prvek, například jiného <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  V rámci obslužné rutiny události, vložte kód podobný následujícímu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. Umístěte kód v následujícím postupem `&New`<xref:System.Windows.Forms.ToolStripMenuItem> zaregistrovat obslužnou rutinu události.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření nadřazených formulářů MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
