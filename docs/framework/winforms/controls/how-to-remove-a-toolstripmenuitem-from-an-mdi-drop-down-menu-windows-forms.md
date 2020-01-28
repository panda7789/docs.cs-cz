---
title: 'Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI'
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
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735849"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)
V některých aplikacích se může v nadřazeném okně MDI lišit druh podřízeného okna rozhraní MDI (Multiple Document Interface). Nadřazený objekt MDI může být například tabulka a podřízená položka MDI může být graf. V takovém případě chcete aktualizovat obsah nabídky nadřazeného objektu MDI s obsahem nabídky podřízeného objektu MDI, protože jsou aktivována podřízená okna MDI různých druhů.  
  
 Následující postup používá vlastnosti <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> k odebrání položky nabídky z rozevírací části v nadřazené nabídce MDI. Zavření podřízeného okna MDI obnoví odebrané položky nabídky do nadřazené nabídky MDI.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Odebrání prvku MenuStrip z rozevírací nabídky MDI  
  
1. Vytvořte formulář a nastavte jeho vlastnost <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.  
  
2. Přidejte <xref:System.Windows.Forms.MenuStrip> do `Form1` a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.  
  
3. Přidejte položku nabídky nejvyšší úrovně do `Form1`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.Control.Text%2A> na `&File`.  
  
4. Přidejte tři položky podnabídky do položky nabídky `&File` a nastavte jejich vlastnosti <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Open`, `&Import from`a `E&xit`.  
  
5. Přidejte dvě položky podnabídky do položky podnabídky `&Import from` a nastavte jejich vlastnosti <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Word` a `&Excel`.  
  
6. Přidejte do projektu formulář, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`ho <xref:System.Windows.Forms.MenuStrip> na `true`.  
  
7. Přidejte položku nabídky nejvyšší úrovně do `Form2`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&File`.  
  
8. Přidejte položku podnabídky `&Import from` do nabídky `&File` `Form2`a přidejte položku `&Word` podnabídky do nabídky `&File`.  
  
9. Nastavte <xref:System.Windows.Forms.MergeAction> a vlastnosti <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> položek nabídky `Form2`, jak je znázorněno v následující tabulce.  
  
    |Položka nabídky Form2|Hodnota MergeAction|Hodnota MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Soubor|MatchOnly|-1|  
    |Importovat z|MatchOnly|-1|  
    |Word|Odebrat|-1|  
  
10. V `Form1`vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. V rámci obslužné rutiny události vložte kód podobný následujícímu příkladu kódu, který vytvoří a zobrazí nové instance `Form2` jako podřízené objekty MDI `Form1`:  
  
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
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
- <xref:System.Windows.Forms.MenuStrip> ovládací prvek `Form1` s názvem `menuStrip1`a ovládací prvek <xref:System.Windows.Forms.MenuStrip> na `Form2` s názvem `menuStrip2`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření nadřazených formulářů MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
