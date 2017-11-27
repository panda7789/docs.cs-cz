---
title: "Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)"
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
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b265544b45ad0614985fdc1d8dbf6f9c0b909ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="c23a4-102">Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c23a4-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="c23a4-103">V některých aplikacích může být odlišný od nadřazeného okna MDI druh podřízeného okna rozhraní více dokumentů (MDI).</span><span class="sxs-lookup"><span data-stu-id="c23a4-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="c23a4-104">Například nadřazené MDI může být tabulkou a podřízeného MDI může být graf.</span><span class="sxs-lookup"><span data-stu-id="c23a4-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="c23a4-105">V takovém případě chcete aktualizovat obsah nabídky MDI nadřazeného objektu s obsahem podřízeného MDI nabídky, jako jsou aktivované podřízených oken MDI různého druhu.</span><span class="sxs-lookup"><span data-stu-id="c23a4-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="c23a4-106">Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete odebrat položku nabídky z rozevíracího seznamu součástí nabídce MDI nadřazené.</span><span class="sxs-lookup"><span data-stu-id="c23a4-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="c23a4-107">Ukončování podřízeného okna MDI obnoví položek odebrána nabídky do nabídky MDI nadřazené.</span><span class="sxs-lookup"><span data-stu-id="c23a4-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="c23a4-108">Chcete-li odebrat prvku MenuStrip z rozevíracího seznamu MDI</span><span class="sxs-lookup"><span data-stu-id="c23a4-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="c23a4-109">Vytvoření formuláře a nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="c23a4-110">Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="c23a4-111">Přidání položky nabídky nejvyšší úrovně na `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="c23a4-112">Přidejte tři položky podnabídky k `&File` položky nabídky a sadu jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti, které chcete `&Open`, `&Import from`, a `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="c23a4-113">Přidat dvě dílčí položky do `&Import from` položku podnabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti, které chcete `&Word` a `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="c23a4-114">Přidejte formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="c23a4-115">Přidání položky nabídky nejvyšší úrovně na `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="c23a4-116">Přidat `&Import from` položky podnabídky a `&File` nabídky `Form2`a přidejte `&Word` položky podnabídky a `&File` nabídky.</span><span class="sxs-lookup"><span data-stu-id="c23a4-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="c23a4-117">Nastavte <xref:System.Windows.Forms.MergeAction> a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti `Form2` položky nabídky, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c23a4-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="c23a4-118">Položky nabídky Form2</span><span class="sxs-lookup"><span data-stu-id="c23a4-118">Form2 menu item</span></span>|<span data-ttu-id="c23a4-119">Hodnota MergeAction</span><span class="sxs-lookup"><span data-stu-id="c23a4-119">MergeAction value</span></span>|<span data-ttu-id="c23a4-120">Hodnota MergeIndex</span><span class="sxs-lookup"><span data-stu-id="c23a4-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="c23a4-121">Soubor</span><span class="sxs-lookup"><span data-stu-id="c23a4-121">File</span></span>|<span data-ttu-id="c23a4-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="c23a4-122">MatchOnly</span></span>|<span data-ttu-id="c23a4-123">-1</span><span class="sxs-lookup"><span data-stu-id="c23a4-123">-1</span></span>|  
    |<span data-ttu-id="c23a4-124">Importovat z</span><span class="sxs-lookup"><span data-stu-id="c23a4-124">Import from</span></span>|<span data-ttu-id="c23a4-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="c23a4-125">MatchOnly</span></span>|<span data-ttu-id="c23a4-126">-1</span><span class="sxs-lookup"><span data-stu-id="c23a4-126">-1</span></span>|  
    |<span data-ttu-id="c23a4-127">Word</span><span class="sxs-lookup"><span data-stu-id="c23a4-127">Word</span></span>|<span data-ttu-id="c23a4-128">Odebrat</span><span class="sxs-lookup"><span data-stu-id="c23a4-128">Remove</span></span>|<span data-ttu-id="c23a4-129">-1</span><span class="sxs-lookup"><span data-stu-id="c23a4-129">-1</span></span>|  
  
10. <span data-ttu-id="c23a4-130">V `Form1`, vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> události `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="c23a4-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="c23a4-131">V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nové instance třídy `Form2` jako podřízené objekty MDI `Form1`:</span><span class="sxs-lookup"><span data-stu-id="c23a4-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
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
  
12. <span data-ttu-id="c23a4-132">Umístěte podobně jako následující příklad kódu v kódu `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c23a4-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c23a4-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c23a4-133">Compiling the Code</span></span>  
 <span data-ttu-id="c23a4-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c23a4-134">This example requires:</span></span>  
  
-   <span data-ttu-id="c23a4-135">Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="c23a4-136">A <xref:System.Windows.Forms.MenuStrip> řízení na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> řízení na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="c23a4-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="c23a4-137">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="c23a4-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23a4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="c23a4-138">See Also</span></span>  
 [<span data-ttu-id="c23a4-139">Postupy: vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="c23a4-139">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="c23a4-140">Postupy: vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="c23a4-140">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="c23a4-141">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="c23a4-141">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
