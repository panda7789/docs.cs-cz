---
title: 'Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731018"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)
Rozhraní MDI (Multiple Document Interface) slouží k vytváření aplikací, které mohou současně otevřít několik dokumentů a kopírovat a vkládat obsah z jednoho dokumentu na druhý.  
  
 Tento postup ukazuje, jak vytvořit seznam všech aktivních podřízených formulářů v nabídce nadřazeného okna.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Vytvoření seznamu oken MDI na ovládacím prvku MenuStrip  
  
1. Vytvořte formulář a nastavte jeho vlastnost <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.  
  
2. Přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře.  
  
3. Přidejte dvě položky nabídky nejvyšší úrovně do <xref:System.Windows.Forms.MenuStrip> a nastavte jejich vlastnosti <xref:System.Windows.Forms.Control.Text%2A> na `&File` a `&Window`.  
  
4. Přidejte položku podnabídky do položky nabídky `&File` a nastavte její vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Open`.  
  
5. Nastavte vlastnost <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> <xref:System.Windows.Forms.MenuStrip> na <xref:System.Windows.Forms.ToolStripMenuItem>`&Window`.  
  
6. Přidejte do projektu formulář a přidejte do něj požadovaný ovládací prvek, jako je například jiný <xref:System.Windows.Forms.MenuStrip>.  
  
7. Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8. V rámci obslužné rutiny události vložte kód podobný následujícímu pro vytvoření a zobrazení nových instancí `Form2` jako podřízených objektů MDI `Form1`.  
  
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
  
9. Umístěte kód podobný následujícímu v <xref:System.Windows.Forms.ToolStripMenuItem> `&New`k registraci obslužné rutiny události.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
- <xref:System.Windows.Forms.MenuStrip> ovládací prvek `Form1` s názvem `menuStrip1`a ovládací prvek <xref:System.Windows.Forms.MenuStrip> na `Form2` s názvem `menuStrip2`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření nadřazených formulářů MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
