---
title: "Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2befec35090cf69c6a12cfe24c3512ae9a9b1bfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)
V některých aplikacích může být odlišný od nadřazeného okna MDI druh podřízeného okna rozhraní více dokumentů (MDI). Například nadřazené MDI může být tabulkou a podřízeného MDI může být graf. V takovém případě chcete aktualizovat obsah nabídky MDI nadřazeného objektu s obsahem podřízeného MDI nabídky, jako jsou aktivované podřízených oken MDI různého druhu.  
  
 Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete vložit skupinu položek nabídky v nabídce podřízeného MDI do rozevíracího seznamu součástí nabídky nadřazené MDI. Ukončování podřízeného okna MDI odebere MDI nadřazené položky vložené nabídky.  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>Vložení prvku MenuStrip do rozevíracího seznamu MDI  
  
1.  Vytvoření formuláře a nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2.  Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
3.  Přidání položky nabídky nejvyšší úrovně na `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.  
  
4.  Přidejte tři položky podnabídky k `&File` položky nabídky a sadu jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti, které chcete `&Open`, `&Import from`, a `E&xit`.  
  
5.  Přidat dvě dílčí položky do `&Import from` položku podnabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti, které chcete `&Word` a `&Excel`.  
  
6.  Přidejte formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
7.  Přidání položky nabídky nejvyšší úrovně na `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&File`.  
  
8.  Přidání položek podnabídky pro `&File` nabídky `Form2` v následujícím pořadí: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `&Close``and Save`a jiné <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Nastavte <xref:System.Windows.Forms.MergeAction> a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti `Form2` položky nabídky, jak je znázorněno v následující tabulce.  
  
    |Položky nabídky Form2|Hodnota MergeAction|Hodnota MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Soubor|MatchOnly|-1|  
    |Oddělovač|Insert|2|  
    |Uložit|Insert|3|  
    |Uložte a zavřete|Insert|4|  
    |Oddělovač|Insert|5|  
  
10. Vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> události `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nové instance třídy `Form2` jako podřízené objekty MDI `Form1`.  
  
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
  
12. Umístěte podobně jako následující příklad kódu v kódu `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> řízení na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> řízení na `Form2` s názvem `menuStrip2`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Postupy: vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
