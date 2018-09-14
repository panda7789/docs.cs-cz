---
title: 'Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 64e7e7875a635bcd4fbafb62d3ee7b7018214ee4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521437"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="178ae-102">Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="178ae-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="178ae-103">V některých aplikacích druh podřízené okno rozhraní více dokumentů (MDI) může lišit od nadřazeného okna MDI.</span><span class="sxs-lookup"><span data-stu-id="178ae-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="178ae-104">Například nadřazený objekt MDI může být tabulku a podřízený formulář MDI může být grafu.</span><span class="sxs-lookup"><span data-stu-id="178ae-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="178ae-105">V takovém případě budete chtít aktualizovat obsah nabídky nadřazený objekt MDI obsah nabídky podřízený formulář MDI jako podřízená okna MDI různé druhy se aktivují.</span><span class="sxs-lookup"><span data-stu-id="178ae-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="178ae-106">Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete vložit skupinu položek nabídky v nabídce podřízeného MDI do části rozevíracího seznamu MDI nadřazené nabídky.</span><span class="sxs-lookup"><span data-stu-id="178ae-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="178ae-107">Zavření podřízené okno MDI odebere položky vložené nabídky z nadřazený objekt MDI.</span><span class="sxs-lookup"><span data-stu-id="178ae-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="178ae-108">K vložení prvku MenuStrip do rozevíracího seznamu MDI</span><span class="sxs-lookup"><span data-stu-id="178ae-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="178ae-109">Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="178ae-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="178ae-110">Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavit <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="178ae-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="178ae-111">Přidání položky do nabídek nejvyšší úrovně `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="178ae-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="178ae-112">Přidejte tři položky podnabídky do `&File` položky nabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Open`, `&Import from`, a `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="178ae-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="178ae-113">Přidání dvou položek podnabídky do `&Import from` položku podnabídky a nastavte jejich <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností `&Word` a `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="178ae-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="178ae-114">Přidání formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="178ae-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="178ae-115">Přidání položky do nabídek nejvyšší úrovně `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="178ae-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="178ae-116">Přidat podnabídku položky, které chcete `&File` nabídku `Form2` v následujícím pořadí: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`a další <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="178ae-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="178ae-117">Nastavte <xref:System.Windows.Forms.MergeAction> a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti `Form2` položky nabídky, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="178ae-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="178ae-118">Položka nabídky Form2</span><span class="sxs-lookup"><span data-stu-id="178ae-118">Form2 menu item</span></span>|<span data-ttu-id="178ae-119">Hodnota MergeAction</span><span class="sxs-lookup"><span data-stu-id="178ae-119">MergeAction value</span></span>|<span data-ttu-id="178ae-120">Hodnota MergeIndex</span><span class="sxs-lookup"><span data-stu-id="178ae-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="178ae-121">Soubor</span><span class="sxs-lookup"><span data-stu-id="178ae-121">File</span></span>|<span data-ttu-id="178ae-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="178ae-122">MatchOnly</span></span>|<span data-ttu-id="178ae-123">-1</span><span class="sxs-lookup"><span data-stu-id="178ae-123">-1</span></span>|  
    |<span data-ttu-id="178ae-124">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="178ae-124">Separator</span></span>|<span data-ttu-id="178ae-125">Insert</span><span class="sxs-lookup"><span data-stu-id="178ae-125">Insert</span></span>|<span data-ttu-id="178ae-126">2</span><span class="sxs-lookup"><span data-stu-id="178ae-126">2</span></span>|  
    |<span data-ttu-id="178ae-127">Uložit</span><span class="sxs-lookup"><span data-stu-id="178ae-127">Save</span></span>|<span data-ttu-id="178ae-128">Insert</span><span class="sxs-lookup"><span data-stu-id="178ae-128">Insert</span></span>|<span data-ttu-id="178ae-129">3</span><span class="sxs-lookup"><span data-stu-id="178ae-129">3</span></span>|  
    |<span data-ttu-id="178ae-130">Uložit a zavřít</span><span class="sxs-lookup"><span data-stu-id="178ae-130">Save and Close</span></span>|<span data-ttu-id="178ae-131">Insert</span><span class="sxs-lookup"><span data-stu-id="178ae-131">Insert</span></span>|<span data-ttu-id="178ae-132">4</span><span class="sxs-lookup"><span data-stu-id="178ae-132">4</span></span>|  
    |<span data-ttu-id="178ae-133">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="178ae-133">Separator</span></span>|<span data-ttu-id="178ae-134">Insert</span><span class="sxs-lookup"><span data-stu-id="178ae-134">Insert</span></span>|<span data-ttu-id="178ae-135">5</span><span class="sxs-lookup"><span data-stu-id="178ae-135">5</span></span>|  
  
10. <span data-ttu-id="178ae-136">Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="178ae-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="178ae-137">V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="178ae-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="178ae-138">Umístit podobně jako v následujícím příkladu kódu v kódu `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> zaregistrovat obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="178ae-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="178ae-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="178ae-139">Compiling the Code</span></span>  
 <span data-ttu-id="178ae-140">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="178ae-140">This example requires:</span></span>  
  
-   <span data-ttu-id="178ae-141">Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="178ae-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="178ae-142">A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="178ae-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="178ae-143">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="178ae-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="178ae-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="178ae-144">See Also</span></span>  
 [<span data-ttu-id="178ae-145">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="178ae-145">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="178ae-146">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="178ae-146">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="178ae-147">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="178ae-147">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
