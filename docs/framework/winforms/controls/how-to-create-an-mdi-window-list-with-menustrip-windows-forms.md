---
title: "Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)"
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
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8bf09170b4def3f041e34942a968fdf41fcdf66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)
Použijte rozhraní více dokumentů (MDI) k vytvoření aplikace, které můžete otevřít několik dokumentů na stejný čas a zkopírujte a vložte obsah z jednoho dokumentu na druhý.  
  
 Tento postup ukazuje, jak vytvořit seznam všech aktivních podřízených formulářů v nabídce okno nadřazeného objektu.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>K vytvoření seznamu okna MDI v prvku MenuStrip  
  
1.  Vytvoření formuláře a nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2.  Přidat <xref:System.Windows.Forms.MenuStrip> do formuláře.  
  
3.  Přidat dvě položky do nejvyšší úrovně <xref:System.Windows.Forms.MenuStrip> a nastavte jejich <xref:System.Windows.Forms.Control.Text%2A> vlastnosti, které chcete `&File` a `&Window`.  
  
4.  Přidání položky podnabídky a `&File` položky nabídky a sadu jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&Open`.  
  
5.  Nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Přidejte formuláře do projektu a přidejte chcete ovládací prvek, například jiného <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> události `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  V rámci obslužné rutiny události vložení kódu podobný následujícímu k vytváření a zobrazování nové instance třídy `Form2` jako podřízené objekty MDI `Form1`.  
  
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
  
9. Umístěte kód jako následující `&New` <xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> řízení na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> řízení na `Form2` s názvem `menuStrip2`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Postupy: Vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Ovládací prvek MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
