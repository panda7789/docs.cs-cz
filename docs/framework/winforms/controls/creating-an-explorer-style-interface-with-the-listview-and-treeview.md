---
title: 'Návod: Vytváření rozhraní ve stylu Průzkumníku s ovládacími prvky ListView a TreeView pomocí Návrháře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 73d3a0bef1ab075aee8e06f676ef17b853773552
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267234"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Návod: Vytváření rozhraní ve stylu Průzkumníku s ovládacími prvky ListView a TreeView pomocí Návrháře
Jednou z výhod sady Visual Studio je schopnost vytvářet profesionálně vypadajících aplikací Windows Forms v krátké množství času. Běžný scénář, kdy je vytváření uživatelského rozhraní (UI) s <xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> ovládací prvky, které se podobá funkci Windows Explorer operačních systémů Windows. Průzkumník Windows zobrazí hierarchickou strukturu souborů a složek v počítači uživatele.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Chcete-li vytvořit formulář obsahující ovládací prvek ListView a TreeView  
  
1.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogové okno pole, postupujte takto:  
  
    1.  V kategoriích, zvolte buď **jazyka Visual Basic** nebo **Visual C#**.  
  
    2.  V seznamu šablon vyberte **formulářová aplikace Windows**.  
  
3.  Klikněte na tlačítko **OK**. Vytvoření nového projektu Windows Forms.  
  
4.  Přidat <xref:System.Windows.Forms.SplitContainer> ovládací prvek do formuláře a nastavte jeho <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Přidat <xref:System.Windows.Forms.ImageList> s názvem `imageList1` chcete formulář opravdu zavřít a použít přidejte dvě bitové kopie v okně Vlastnosti: obrázek složky a bitovou kopii dokumentu, v uvedeném pořadí.  
  
6.  Přidat <xref:System.Windows.Forms.TreeView> ovládací prvek s názvem `treeview1` do formuláře a umístěte ho na levé straně <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V okně Vlastnosti `treeView1` postupujte takto:  
  
    1.  Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Nastavte <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost `imagelist1.`  
  
7.  Přidat <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` do formuláře a umístěte ho na pravé straně <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V okně Vlastnosti `listview1` postupujte takto:  
  
    1.  Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.  
  
    3.  Otevřete Editor kolekce ColumnHeader kliknutím na symbol tří teček (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) v <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost **.** Přidejte tři sloupce a nastavte jejich <xref:System.Windows.Forms.ColumnHeader.Text%2A> vlastnost `Name`, `Type`, a `Last Modified`v uvedeném pořadí. Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
    4.  Nastavte <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnost `imageList1.`  
  
8.  Implementujte kód pro naplnění <xref:System.Windows.Forms.TreeView> s uzly a podřízených uzlů. Přidejte tento kód `Form1` třídy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Protože předchozí kód používá System.IO – obor názvů, přidejte odpovídající použití nebo importovat výraz v horní části formuláře.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Volat metodu nastavení z předchozího kroku v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metody zpracování událostí. Tento kód vložte do konstruktoru formuláře.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Zpracování <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost pro `treeview1` **,** a implementujte kód pro naplnění `listview1` s obsahem uzlu při kliknutí na uzel. Přidejte tento kód `Form1` třídy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     Pokud používáte C#, ujistěte se, že máte <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost spojenou s jeho metody zpracování událostí. Tento kód vložte do konstruktoru formuláře.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
     Uvidíte obsahující formulář rozdělení <xref:System.Windows.Forms.TreeView> ovládací prvek, který se zobrazí na levé straně adresáře vašeho projektu a <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně se třemi sloupci. Můžete procházet <xref:System.Windows.Forms.TreeView> tak, že vyberete uzly adresáře a <xref:System.Windows.Forms.ListView> se vyplní obsah vybrané adresáře.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace poskytuje příklad ukazuje, jak můžete použít <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ListView> řídí společně. Další informace o těchto ovládacích prvků naleznete v následujících tématech:  
  
-   [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
