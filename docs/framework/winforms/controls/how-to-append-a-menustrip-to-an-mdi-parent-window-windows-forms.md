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
ms.openlocfilehash: 048add340a81856cd30482c52c93c76bbf6181f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI (Windows Forms)
V některých aplikacích může být odlišný od nadřazeného okna MDI druh podřízeného okna rozhraní více dokumentů (MDI). Například nadřazené MDI může být tabulkou a podřízeného MDI může být graf. V takovém případě chcete aktualizovat obsah nabídky MDI nadřazeného objektu s obsahem podřízeného MDI nabídky, jako jsou aktivované podřízených oken MDI různého druhu.  
  
 Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete připojit v nabídce podřízeného MDI do nabídky MDI nadřazené. Ukončování podřízeného okna MDI odebere nadřazené MDI nabídce připojením.  
  
 Viz také [aplikace rozhraní více dokumentů (MDI)](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Pro připojení nadřazené MDI položku nabídky  
  
1.  Vytvoření formuláře a nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2.  Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
3.  Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `Form1` <xref:System.Windows.Forms.MenuStrip> k `false`.  
  
4.  Přidání položky nabídky nejvyšší úrovně na `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.  
  
5.  Přidání položky podnabídky a `&File` položky nabídky a sadu jeho <xref:System.Windows.Forms.Form.Text%2A> vlastnost `&Open`.  
  
6.  Přidejte formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.  
  
7.  Přidání položky nabídky nejvyšší úrovně na `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.Form.Text%2A> vlastnost `&Special`.  
  
8.  Přidat dvě dílčí položky do `&Special` položky nabídky a sadu jejich <xref:System.Windows.Forms.Form.Text%2A> vlastnosti, které chcete `Command&1` a `Command&2`, v uvedeném pořadí.  
  
9. Nastavte <xref:System.Windows.Forms.MergeAction> vlastnost `&Special`, `Command&1`, a `Command&2` položky nabídky mají <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> události `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nové instance třídy `Form2` jako podřízené objekty MDI `Form1`.  
  
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
