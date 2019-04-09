---
title: 'Návod: Vytváření rozhraní ve stylu Průzkumníka s ovládacími prvky ListView a TreeView pomocí Návrháře'
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
ms.openlocfilehash: 21a3f7f687f72fe6e73b5d2420675634ff834d2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117985"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="772a8-102">Návod: Vytváření rozhraní ve stylu Průzkumníka s ovládacími prvky ListView a TreeView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="772a8-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>
<span data-ttu-id="772a8-103">Jednou z výhod sady Visual Studio je schopnost vytvářet profesionálně vypadajících aplikací Windows Forms v krátké množství času.</span><span class="sxs-lookup"><span data-stu-id="772a8-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="772a8-104">Běžný scénář, kdy je vytváření uživatelského rozhraní (UI) s <xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> ovládací prvky, které se podobá funkci Windows Explorer operačních systémů Windows.</span><span class="sxs-lookup"><span data-stu-id="772a8-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="772a8-105">Průzkumník Windows zobrazí hierarchickou strukturu souborů a složek v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="772a8-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="772a8-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="772a8-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="772a8-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="772a8-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="772a8-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="772a8-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="772a8-109">Chcete-li vytvořit formulář obsahující ovládací prvek ListView a TreeView</span><span class="sxs-lookup"><span data-stu-id="772a8-109">To create the form containing a ListView and TreeView control</span></span>  
  
1.  <span data-ttu-id="772a8-110">Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="772a8-110">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="772a8-111">V **nový projekt** dialogové okno pole, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="772a8-111">In the **New Project** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="772a8-112">V kategoriích, zvolte buď **jazyka Visual Basic** nebo **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="772a8-112">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>  
  
    2.  <span data-ttu-id="772a8-113">V seznamu šablon vyberte **formulářová aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="772a8-113">In the list of templates, choose **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="772a8-114">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="772a8-114">Click **OK**.</span></span> <span data-ttu-id="772a8-115">Vytvoření nového projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="772a8-115">A new Windows Forms project is created.</span></span>  
  
4.  <span data-ttu-id="772a8-116">Přidat <xref:System.Windows.Forms.SplitContainer> ovládací prvek do formuláře a nastavte jeho <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="772a8-116">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="772a8-117">Přidat <xref:System.Windows.Forms.ImageList> s názvem `imageList1` chcete formulář opravdu zavřít a použít přidejte dvě bitové kopie v okně Vlastnosti: obrázek složky a bitovou kopii dokumentu, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="772a8-117">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>  
  
6.  <span data-ttu-id="772a8-118">Přidat <xref:System.Windows.Forms.TreeView> ovládací prvek s názvem `treeview1` do formuláře a umístěte ho na levé straně <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="772a8-118">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="772a8-119">V okně Vlastnosti `treeView1` postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="772a8-119">In the Properties window for `treeView1` do the following:</span></span>  
  
    1.  <span data-ttu-id="772a8-120">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="772a8-120">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="772a8-121">Nastavte <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="772a8-121">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to</span></span> `imagelist1.`  
  
7.  <span data-ttu-id="772a8-122">Přidat <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` do formuláře a umístěte ho na pravé straně <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="772a8-122">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="772a8-123">V okně Vlastnosti `listview1` postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="772a8-123">In the Properties window for `listview1` do the following:</span></span>  
  
    1.  <span data-ttu-id="772a8-124">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="772a8-124">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="772a8-125">Nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="772a8-125">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
    3.  <span data-ttu-id="772a8-126">Otevřete Editor kolekce ColumnHeader kliknutím na symbol tří teček (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) v <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost **.**</span><span class="sxs-lookup"><span data-stu-id="772a8-126">Open the ColumnHeader Collection Editor by clicking the ellipses (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="772a8-127">Přidejte tři sloupce a nastavte jejich <xref:System.Windows.Forms.ColumnHeader.Text%2A> vlastnost `Name`, `Type`, a `Last Modified`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="772a8-127">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="772a8-128">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="772a8-128">Click **OK** to close the dialog box.</span></span>  
  
    4.  <span data-ttu-id="772a8-129">Nastavte <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="772a8-129">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to</span></span> `imageList1.`  
  
8.  <span data-ttu-id="772a8-130">Implementujte kód pro naplnění <xref:System.Windows.Forms.TreeView> s uzly a podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="772a8-130">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="772a8-131">Přidejte tento kód `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="772a8-131">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. <span data-ttu-id="772a8-132">Protože předchozí kód používá System.IO – obor názvů, přidejte odpovídající použití nebo importovat výraz v horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="772a8-132">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="772a8-133">Volat metodu nastavení z předchozího kroku v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metody zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="772a8-133">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="772a8-134">Tento kód vložte do konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="772a8-134">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. <span data-ttu-id="772a8-135">Zpracování <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost pro `treeview1` **,** a implementujte kód pro naplnění `listview1` s obsahem uzlu při kliknutí na uzel.</span><span class="sxs-lookup"><span data-stu-id="772a8-135">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="772a8-136">Přidejte tento kód `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="772a8-136">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     <span data-ttu-id="772a8-137">Pokud používáte C#, ujistěte se, že máte <xref:System.Windows.Forms.TreeView.NodeMouseClick> událost spojenou s jeho metody zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="772a8-137">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="772a8-138">Tento kód vložte do konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="772a8-138">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="772a8-139">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="772a8-139">Testing the Application</span></span>  
 <span data-ttu-id="772a8-140">Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="772a8-140">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="772a8-141">K otestování formuláře</span><span class="sxs-lookup"><span data-stu-id="772a8-141">To test the form</span></span>  
  
-   <span data-ttu-id="772a8-142">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="772a8-142">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="772a8-143">Uvidíte obsahující formulář rozdělení <xref:System.Windows.Forms.TreeView> ovládací prvek, který se zobrazí na levé straně adresáře vašeho projektu a <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně se třemi sloupci.</span><span class="sxs-lookup"><span data-stu-id="772a8-143">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="772a8-144">Můžete procházet <xref:System.Windows.Forms.TreeView> tak, že vyberete uzly adresáře a <xref:System.Windows.Forms.ListView> se vyplní obsah vybrané adresáře.</span><span class="sxs-lookup"><span data-stu-id="772a8-144">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="772a8-145">Další kroky</span><span class="sxs-lookup"><span data-stu-id="772a8-145">Next Steps</span></span>  
 <span data-ttu-id="772a8-146">Tato aplikace poskytuje příklad ukazuje, jak můžete použít <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ListView> řídí společně.</span><span class="sxs-lookup"><span data-stu-id="772a8-146">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="772a8-147">Další informace o těchto ovládacích prvků naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="772a8-147">For more information on these controls, see the following topics:</span></span>  
  
-   [<span data-ttu-id="772a8-148">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="772a8-148">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [<span data-ttu-id="772a8-149">Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="772a8-149">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [<span data-ttu-id="772a8-150">Postupy: Připojení místní nabídky k uzlu TreeView</span><span class="sxs-lookup"><span data-stu-id="772a8-150">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a><span data-ttu-id="772a8-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="772a8-151">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="772a8-152">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="772a8-152">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="772a8-153">Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="772a8-153">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="772a8-154">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="772a8-154">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="772a8-155">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="772a8-155">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
