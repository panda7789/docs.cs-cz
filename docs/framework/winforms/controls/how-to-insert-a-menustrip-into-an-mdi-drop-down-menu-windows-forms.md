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
ms.workload: dotnet
ms.openlocfilehash: 8ba658bcbd27e0af3a838f5a511b8dd1555c85cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="a404b-102">Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a404b-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="a404b-103">V některých aplikacích může být odlišný od nadřazeného okna MDI druh podřízeného okna rozhraní více dokumentů (MDI).</span><span class="sxs-lookup"><span data-stu-id="a404b-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="a404b-104">Například nadřazené MDI může být tabulkou a podřízeného MDI může být graf.</span><span class="sxs-lookup"><span data-stu-id="a404b-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="a404b-105">V takovém případě chcete aktualizovat obsah nabídky MDI nadřazeného objektu s obsahem podřízeného MDI nabídky, jako jsou aktivované podřízených oken MDI různého druhu.</span><span class="sxs-lookup"><span data-stu-id="a404b-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="a404b-106">Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete vložit skupinu položek nabídky v nabídce podřízeného MDI do rozevíracího seznamu součástí nabídky nadřazené MDI.</span><span class="sxs-lookup"><span data-stu-id="a404b-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="a404b-107">Ukončování podřízeného okna MDI odebere MDI nadřazené položky vložené nabídky.</span><span class="sxs-lookup"><span data-stu-id="a404b-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="a404b-108">Vložení prvku MenuStrip do rozevíracího seznamu MDI</span><span class="sxs-lookup"><span data-stu-id="a404b-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="a404b-109">Vytvoření formuláře a nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="a404b-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="a404b-110">Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="a404b-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="a404b-111">Přidání položky nabídky nejvyšší úrovně na `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="a404b-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="a404b-112">Přidejte tři položky podnabídky k `&File` položky nabídky a sadu jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti, které chcete `&Open`, `&Import from`, a `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="a404b-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="a404b-113">Přidat dvě dílčí položky do `&Import from` položku podnabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti, které chcete `&Word` a `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="a404b-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="a404b-114">Přidejte formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="a404b-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="a404b-115">Přidání položky nabídky nejvyšší úrovně na `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavit jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="a404b-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="a404b-116">Přidání položek podnabídky pro `&File` nabídky `Form2` v následujícím pořadí: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `&Close``and Save`a jiné <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="a404b-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `&Close``and Save`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="a404b-117">Nastavte <xref:System.Windows.Forms.MergeAction> a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti `Form2` položky nabídky, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a404b-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a404b-118">Položky nabídky Form2</span><span class="sxs-lookup"><span data-stu-id="a404b-118">Form2 menu item</span></span>|<span data-ttu-id="a404b-119">Hodnota MergeAction</span><span class="sxs-lookup"><span data-stu-id="a404b-119">MergeAction value</span></span>|<span data-ttu-id="a404b-120">Hodnota MergeIndex</span><span class="sxs-lookup"><span data-stu-id="a404b-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="a404b-121">Soubor</span><span class="sxs-lookup"><span data-stu-id="a404b-121">File</span></span>|<span data-ttu-id="a404b-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="a404b-122">MatchOnly</span></span>|<span data-ttu-id="a404b-123">-1</span><span class="sxs-lookup"><span data-stu-id="a404b-123">-1</span></span>|  
    |<span data-ttu-id="a404b-124">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="a404b-124">Separator</span></span>|<span data-ttu-id="a404b-125">Insert</span><span class="sxs-lookup"><span data-stu-id="a404b-125">Insert</span></span>|<span data-ttu-id="a404b-126">2</span><span class="sxs-lookup"><span data-stu-id="a404b-126">2</span></span>|  
    |<span data-ttu-id="a404b-127">Uložit</span><span class="sxs-lookup"><span data-stu-id="a404b-127">Save</span></span>|<span data-ttu-id="a404b-128">Insert</span><span class="sxs-lookup"><span data-stu-id="a404b-128">Insert</span></span>|<span data-ttu-id="a404b-129">3</span><span class="sxs-lookup"><span data-stu-id="a404b-129">3</span></span>|  
    |<span data-ttu-id="a404b-130">Uložte a zavřete</span><span class="sxs-lookup"><span data-stu-id="a404b-130">Save and Close</span></span>|<span data-ttu-id="a404b-131">Insert</span><span class="sxs-lookup"><span data-stu-id="a404b-131">Insert</span></span>|<span data-ttu-id="a404b-132">4</span><span class="sxs-lookup"><span data-stu-id="a404b-132">4</span></span>|  
    |<span data-ttu-id="a404b-133">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="a404b-133">Separator</span></span>|<span data-ttu-id="a404b-134">Insert</span><span class="sxs-lookup"><span data-stu-id="a404b-134">Insert</span></span>|<span data-ttu-id="a404b-135">5</span><span class="sxs-lookup"><span data-stu-id="a404b-135">5</span></span>|  
  
10. <span data-ttu-id="a404b-136">Vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> události `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="a404b-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="a404b-137">V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nové instance třídy `Form2` jako podřízené objekty MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a404b-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="a404b-138">Umístěte podobně jako následující příklad kódu v kódu `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a404b-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a404b-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a404b-139">Compiling the Code</span></span>  
 <span data-ttu-id="a404b-140">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a404b-140">This example requires:</span></span>  
  
-   <span data-ttu-id="a404b-141">Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="a404b-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="a404b-142">A <xref:System.Windows.Forms.MenuStrip> řízení na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> řízení na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="a404b-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="a404b-143">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="a404b-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a404b-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="a404b-144">See Also</span></span>  
 [<span data-ttu-id="a404b-145">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="a404b-145">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="a404b-146">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="a404b-146">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="a404b-147">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="a404b-147">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
