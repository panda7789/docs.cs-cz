---
title: 'Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: c650f8a26629d942aa4ccf0066aee6af4b51f8b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632059"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="ee2cf-102">Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ee2cf-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="ee2cf-103">V některých aplikacích druh podřízené okno rozhraní více dokumentů (MDI) může lišit od nadřazeného okna MDI.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="ee2cf-104">Například nadřazený objekt MDI může být tabulku a podřízený formulář MDI může být grafu.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="ee2cf-105">V takovém případě budete chtít aktualizovat obsah nabídky nadřazený objekt MDI obsah nabídky podřízený formulář MDI jako podřízená okna MDI různé druhy se aktivují.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="ee2cf-106">Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete odebrat položku nabídky z část rozevíracího seznamu MDI nadřazené nabídky.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="ee2cf-107">Zavření podřízené okno MDI obnoví položky nabídky odebrané do nadřazené nabídky MDI.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="ee2cf-108">Chcete-li odebrat prvku MenuStrip z rozevíracího seznamu MDI</span><span class="sxs-lookup"><span data-stu-id="ee2cf-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="ee2cf-109">Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="ee2cf-110">Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavit <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="ee2cf-111">Přidání položky do nabídek nejvyšší úrovně `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="ee2cf-112">Přidejte tři položky podnabídky do `&File` položky nabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Open`, `&Import from`, a `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="ee2cf-113">Přidání dvou položek podnabídky do `&Import from` položku podnabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Word` a `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="ee2cf-114">Přidání formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="ee2cf-115">Přidání položky do nabídek nejvyšší úrovně `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="ee2cf-116">Přidat `&Import from` podnabídky položku `&File` nabídku `Form2`a přidejte `&Word` položky podnabídky a `&File` nabídky.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="ee2cf-117">Nastavte <xref:System.Windows.Forms.MergeAction> a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti `Form2` položky nabídky, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="ee2cf-118">Položka nabídky Form2</span><span class="sxs-lookup"><span data-stu-id="ee2cf-118">Form2 menu item</span></span>|<span data-ttu-id="ee2cf-119">Hodnota MergeAction</span><span class="sxs-lookup"><span data-stu-id="ee2cf-119">MergeAction value</span></span>|<span data-ttu-id="ee2cf-120">Hodnota MergeIndex</span><span class="sxs-lookup"><span data-stu-id="ee2cf-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="ee2cf-121">Soubor</span><span class="sxs-lookup"><span data-stu-id="ee2cf-121">File</span></span>|<span data-ttu-id="ee2cf-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="ee2cf-122">MatchOnly</span></span>|<span data-ttu-id="ee2cf-123">-1</span><span class="sxs-lookup"><span data-stu-id="ee2cf-123">-1</span></span>|  
    |<span data-ttu-id="ee2cf-124">Importovat z</span><span class="sxs-lookup"><span data-stu-id="ee2cf-124">Import from</span></span>|<span data-ttu-id="ee2cf-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="ee2cf-125">MatchOnly</span></span>|<span data-ttu-id="ee2cf-126">-1</span><span class="sxs-lookup"><span data-stu-id="ee2cf-126">-1</span></span>|  
    |<span data-ttu-id="ee2cf-127">Word</span><span class="sxs-lookup"><span data-stu-id="ee2cf-127">Word</span></span>|<span data-ttu-id="ee2cf-128">odebrat</span><span class="sxs-lookup"><span data-stu-id="ee2cf-128">Remove</span></span>|<span data-ttu-id="ee2cf-129">-1</span><span class="sxs-lookup"><span data-stu-id="ee2cf-129">-1</span></span>|  
  
10. <span data-ttu-id="ee2cf-130">V `Form1`, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="ee2cf-131">V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`:</span><span class="sxs-lookup"><span data-stu-id="ee2cf-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
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
  
12. <span data-ttu-id="ee2cf-132">Umístit podobně jako v následujícím příkladu kódu v kódu `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> zaregistrovat obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ee2cf-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ee2cf-133">Compiling the Code</span></span>  
 <span data-ttu-id="ee2cf-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ee2cf-134">This example requires:</span></span>  
  
-   <span data-ttu-id="ee2cf-135">Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="ee2cf-136">A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="ee2cf-137">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee2cf-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2cf-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee2cf-138">See also</span></span>
- [<span data-ttu-id="ee2cf-139">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="ee2cf-139">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="ee2cf-140">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="ee2cf-140">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="ee2cf-141">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="ee2cf-141">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
