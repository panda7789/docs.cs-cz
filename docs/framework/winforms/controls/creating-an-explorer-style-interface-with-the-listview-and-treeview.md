---
title: "Návod: Vytváření rozhraní ve stylu Průzkumníku s ovládacími prvky ListView a TreeView pomocí Návrháře"
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
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4a16ee1ca39ffb0eb170e206467d612cb707e5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Návod: Vytváření rozhraní ve stylu Průzkumníku s ovládacími prvky ListView a TreeView pomocí Návrháře
Jednou z výhod sady Visual Studio je schopnost vytvářet profesionální aplikace Windows Forms v krátkou dobu. Běžný scénář vytváří uživatelské rozhraní (UI) s <xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> ovládacích prvků, které se podobá funkci Windows Explorer operačních systémů Windows. Průzkumník Windows zobrazí hierarchická struktura souborů a složek v počítači uživatele.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Chcete-li vytvořit formulář obsahující ovládacího prvku ListView a TreeView  
  
1.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
2.  V **nový projekt** dialogové okno pole, postupujte takto:  
  
    1.  V kategoriích, vyberte buď **jazyka Visual Basic** nebo **Visual C#**.  
  
    2.  V seznamu šablon, zvolte **formulářové aplikace Windows**.  
  
3.  Click **OK**. Vytvoření nového projektu Windows Forms.  
  
4.  Přidat <xref:System.Windows.Forms.SplitContainer> řízení formuláře a nastavit jeho <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Přidat <xref:System.Windows.Forms.ImageList> s názvem `imageList1` formuláře a používání vlastnosti okno pro přidání dvě bitové kopie: bitovou kopii složku a dokument bitové kopie v tomto pořadí.  
  
6.  Přidat <xref:System.Windows.Forms.TreeView> ovládací prvek s názvem `treeview1` do formuláře a umístěte ho na levé straně <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V okně Vlastnosti pro `treeView1` postupujte takto:  
  
    1.  Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Nastavte <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnosti`imagelist1.`  
  
7.  Přidat <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` do formuláře a umístěte ho na pravé straně <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V okně Vlastnosti pro `listview1` postupujte takto:  
  
    1.  Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.  
  
    3.  Otevřete Editor kolekce ColumnHeader kliknutím na symbol tří teček (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) v <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost**.** Přidejte tři sloupce a nastavte jejich <xref:System.Windows.Forms.ColumnHeader.Text%2A> vlastnost `Name`, `Type`, a `Last Modified`, v uvedeném pořadí. Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
    4.  Nastavte <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnosti`imageList1.`  
  
8.  Implementaci kódu k naplnění <xref:System.Windows.Forms.TreeView> s uzly a podřízených uzlů. Přidejte tento kód, který `Form1` třídy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Protože předchozí kód používá System.IO – obor názvů, přidejte odpovídající pomocí nebo importovat příkaz v horní části formuláře.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Volání metody nastavení z předchozího kroku v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metoda zpracování událostí. Tento kód vložte do konstruktoru formuláře.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Zpracování <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost pro `treeview1` **,** a implementaci kódu k naplnění `listview1` s obsahem uzlu při kliknutí na uzel. Přidejte tento kód, který `Form1` třídy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     Pokud používáte C#, ujistěte se, máte <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost spojenou s příslušnou metodu zpracování událostí. Tento kód vložte do konstruktoru formuláře.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Postup testování formuláře  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
     Uvidíte obsahující formulář rozdělení <xref:System.Windows.Forms.TreeView> ovládací prvek, který zobrazí adresáře projekt na levé straně a <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně s tři sloupce. Můžete procházet <xref:System.Windows.Forms.TreeView> výběrem directory uzly a <xref:System.Windows.Forms.ListView> naplněný obsah vybrané adresáře.  
  
## <a name="next-steps"></a>Další kroky  
 Tuto aplikaci poskytuje příklad můžete použít způsob <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ListView> prvky společně. Další informace o těchto ovládacích prvků najdete v následujících tématech:  
  
-   [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [Postupy: přidání schopností vyhledávání do ovládacího prvku ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [Postupy: připojení místní nabídky k uzlu TreeView](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [ListView – ovládací prvek](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Postupy: Přidání a odebrání uzlů pomocí ovládacího prvku Windows Forms TreeView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Postupy: přidávání sloupců do ovládacího prvku Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
