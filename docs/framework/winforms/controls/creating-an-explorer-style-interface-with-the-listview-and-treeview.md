---
title: 'Návod: Vytváření rozhraní ve stylu Průzkumníku s ovládacími prvky ListView a TreeView pomocí Návrháře'
description: Naučte se vytvářet rozhraní ve stylu Průzkumníka s ovládacími prvky model Windows Forms ListView a TreeView pomocí návrháře.
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
ms.openlocfilehash: 44d4db1ef3da85dbf411498f486882b86a05c140
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174624"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Návod: Vytváření rozhraní ve stylu Průzkumníku s ovládacími prvky ListView a TreeView pomocí Návrháře

Jednou z výhod sady Visual Studio je možnost vytvářet profesionálně vypadající model Windows Forms aplikace v krátké době. Běžným scénářem je vytvoření uživatelského rozhraní s <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> ovládacími prvky a, které se podobá funkci Průzkumníka Windows v operačních systémech Windows. Průzkumník Windows zobrazuje hierarchickou strukturu souborů a složek v počítači uživatele.

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Vytvoření formuláře obsahujícího ovládací prvek ListView a TreeView

1. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

2. V dialogovém okně **New Project** (Nový projekt) proveďte následující kroky:

    1. V kategoriích vyberte buď **Visual Basic** , nebo **Visual C#**.

    2. V seznamu šablon vyberte možnost **model Windows Forms aplikace**.

3. Klikněte na **OK**. Vytvoří se nový projekt model Windows Forms.

4. Přidejte <xref:System.Windows.Forms.SplitContainer> do formuláře ovládací prvek a nastavte jeho <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Fill> .

5. Přidejte <xref:System.Windows.Forms.ImageList> `imageList1` do formuláře pojmenovaný a pomocí okno Vlastnosti přidejte dvě obrázky: obrázek složky a obrázek dokumentu v tomto pořadí.

6. Přidejte <xref:System.Windows.Forms.TreeView> ovládací prvek s názvem `treeview1` do formuláře a umístěte jej na levou stranu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V okno Vlastnosti `treeView1` postupujte následovně:

    1. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na hodnotu <xref:System.Windows.Forms.DockStyle.Fill> .

    2. Nastavte <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost na`imagelist1.`

7. Přidejte <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` do formuláře a umístěte jej na pravou stranu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. V okno Vlastnosti `listview1` postupujte následovně:

    1. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na hodnotu <xref:System.Windows.Forms.DockStyle.Fill> .

    2. Nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost na hodnotu <xref:System.Windows.Forms.View.Details> .

    3. Otevřete Editor kolekce ColumnHeader kliknutím na elipsy ( ![ tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio. ](./media/visual-studio-ellipsis-button.png) ) ve <xref:System.Windows.Forms.ListView.Columns%2A> vlastnosti **.** Přidejte tři sloupce a nastavte jejich <xref:System.Windows.Forms.ColumnHeader.Text%2A> vlastnost na `Name` , `Type` , a `Last Modified` v uvedeném pořadí. Kliknutím na **OK** zavřete dialogové okno.

    4. Nastavte <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnost na`imageList1.`

8. Implementujte kód pro naplnění <xref:System.Windows.Forms.TreeView> uzlů a dílčích uzlů. Přidejte tento kód do `Form1` třídy.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. Vzhledem k tomu, že předchozí kód používá obor názvů System.IO, přidejte do horní části formuláře příslušný příkaz using nebo import.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. Zavolejte metodu set-up z předchozího kroku v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metodě zpracování událostí. Přidejte tento kód do konstruktoru formuláře.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. Zpracujte <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost pro `treeview1` a implementujte kód **,** který se naplní `listview1` obsahem uzlu při kliknutí na uzel. Přidejte tento kód do `Form1` třídy.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     Pokud používáte jazyk C#, ujistěte se, že máte <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost přidruženou ke své metodě zpracování událostí. Přidejte tento kód do konstruktoru formuláře.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>Testování aplikace

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

#### <a name="to-test-the-form"></a>Testování formuláře

- Stisknutím klávesy F5 spusťte aplikaci.

     Zobrazí se rozdělený formulář <xref:System.Windows.Forms.TreeView> , který obsahuje ovládací prvek, který zobrazí adresář projektu na levé straně a <xref:System.Windows.Forms.ListView> ovládací prvek na pravé straně se třemi sloupci. Můžete procházet tím, že <xref:System.Windows.Forms.TreeView> vyberete uzly adresáře a <xref:System.Windows.Forms.ListView> naplní se obsahem vybraného adresáře.

## <a name="next-steps"></a>Další kroky

Tato aplikace poskytuje příklad způsobu, jakým můžete použít <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ListView> ovládat dohromady. Další informace o těchto ovládacích prvcích naleznete v následujících tématech:

- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView](how-to-add-search-capabilities-to-a-listview-control.md)

- [Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView – ovládací prvek](listview-control-windows-forms.md)
- [Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
