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
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="d01af-103">Návod: Vytváření rozhraní ve stylu Průzkumníku s ovládacími prvky ListView a TreeView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d01af-103">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="d01af-104">Jednou z výhod sady Visual Studio je možnost vytvářet profesionálně vypadající model Windows Forms aplikace v krátké době.</span><span class="sxs-lookup"><span data-stu-id="d01af-104">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="d01af-105">Běžným scénářem je vytvoření uživatelského rozhraní s <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> ovládacími prvky a, které se podobá funkci Průzkumníka Windows v operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="d01af-105">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="d01af-106">Průzkumník Windows zobrazuje hierarchickou strukturu souborů a složek v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="d01af-106">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="d01af-107">Vytvoření formuláře obsahujícího ovládací prvek ListView a TreeView</span><span class="sxs-lookup"><span data-stu-id="d01af-107">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="d01af-108">V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="d01af-108">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="d01af-109">V dialogovém okně **New Project** (Nový projekt) proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="d01af-109">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="d01af-110">V kategoriích vyberte buď **Visual Basic** , nebo **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="d01af-110">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="d01af-111">V seznamu šablon vyberte možnost **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="d01af-111">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="d01af-112">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d01af-112">Click **OK**.</span></span> <span data-ttu-id="d01af-113">Vytvoří se nový projekt model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d01af-113">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="d01af-114">Přidejte <xref:System.Windows.Forms.SplitContainer> do formuláře ovládací prvek a nastavte jeho <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="d01af-114">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="d01af-115">Přidejte <xref:System.Windows.Forms.ImageList> `imageList1` do formuláře pojmenovaný a pomocí okno Vlastnosti přidejte dvě obrázky: obrázek složky a obrázek dokumentu v tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="d01af-115">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="d01af-116">Přidejte <xref:System.Windows.Forms.TreeView> ovládací prvek s názvem `treeview1` do formuláře a umístěte jej na levou stranu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d01af-116">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="d01af-117">V okno Vlastnosti `treeView1` postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="d01af-117">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="d01af-118">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na hodnotu <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="d01af-118">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="d01af-119">Nastavte <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost na`imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="d01af-119">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="d01af-120">Přidejte <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` do formuláře a umístěte jej na pravou stranu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d01af-120">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="d01af-121">V okno Vlastnosti `listview1` postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="d01af-121">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="d01af-122">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na hodnotu <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="d01af-122">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="d01af-123">Nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost na hodnotu <xref:System.Windows.Forms.View.Details> .</span><span class="sxs-lookup"><span data-stu-id="d01af-123">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="d01af-124">Otevřete Editor kolekce ColumnHeader kliknutím na elipsy ( ![ tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio. ](./media/visual-studio-ellipsis-button.png) ) ve <xref:System.Windows.Forms.ListView.Columns%2A> vlastnosti **.**</span><span class="sxs-lookup"><span data-stu-id="d01af-124">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="d01af-125">Přidejte tři sloupce a nastavte jejich <xref:System.Windows.Forms.ColumnHeader.Text%2A> vlastnost na `Name` , `Type` , a `Last Modified` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d01af-125">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="d01af-126">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d01af-126">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="d01af-127">Nastavte <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnost na`imageList1.`</span><span class="sxs-lookup"><span data-stu-id="d01af-127">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="d01af-128">Implementujte kód pro naplnění <xref:System.Windows.Forms.TreeView> uzlů a dílčích uzlů.</span><span class="sxs-lookup"><span data-stu-id="d01af-128">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="d01af-129">Přidejte tento kód do `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="d01af-129">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="d01af-130">Vzhledem k tomu, že předchozí kód používá obor názvů System.IO, přidejte do horní části formuláře příslušný příkaz using nebo import.</span><span class="sxs-lookup"><span data-stu-id="d01af-130">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="d01af-131">Zavolejte metodu set-up z předchozího kroku v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metodě zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="d01af-131">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="d01af-132">Přidejte tento kód do konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="d01af-132">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="d01af-133">Zpracujte <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost pro `treeview1` a implementujte kód **,** který se naplní `listview1` obsahem uzlu při kliknutí na uzel.</span><span class="sxs-lookup"><span data-stu-id="d01af-133">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="d01af-134">Přidejte tento kód do `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="d01af-134">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="d01af-135">Pokud používáte jazyk C#, ujistěte se, že máte <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost přidruženou ke své metodě zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="d01af-135">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="d01af-136">Přidejte tento kód do konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="d01af-136">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="d01af-137">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="d01af-137">Testing the Application</span></span>

<span data-ttu-id="d01af-138">Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="d01af-138">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="d01af-139">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="d01af-139">To test the form</span></span>

- <span data-ttu-id="d01af-140">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d01af-140">Press F5 to run the application.</span></span>

     <span data-ttu-id="d01af-141">Zobrazí se rozdělený formulář <xref:System.Windows.Forms.TreeView> , který obsahuje ovládací prvek, který zobrazí adresář projektu na levé straně a <xref:System.Windows.Forms.ListView> ovládací prvek na pravé straně se třemi sloupci.</span><span class="sxs-lookup"><span data-stu-id="d01af-141">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="d01af-142">Můžete procházet tím, že <xref:System.Windows.Forms.TreeView> vyberete uzly adresáře a <xref:System.Windows.Forms.ListView> naplní se obsahem vybraného adresáře.</span><span class="sxs-lookup"><span data-stu-id="d01af-142">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d01af-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d01af-143">Next Steps</span></span>

<span data-ttu-id="d01af-144">Tato aplikace poskytuje příklad způsobu, jakým můžete použít <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ListView> ovládat dohromady.</span><span class="sxs-lookup"><span data-stu-id="d01af-144">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="d01af-145">Další informace o těchto ovládacích prvcích naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="d01af-145">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="d01af-146">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d01af-146">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="d01af-147">Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="d01af-147">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="d01af-148">Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView</span><span class="sxs-lookup"><span data-stu-id="d01af-148">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="d01af-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="d01af-149">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="d01af-150">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d01af-150">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="d01af-151">Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="d01af-151">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="d01af-152">Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d01af-152">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="d01af-153">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d01af-153">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
