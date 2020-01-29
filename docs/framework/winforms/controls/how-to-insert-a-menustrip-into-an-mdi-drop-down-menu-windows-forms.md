---
title: 'Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 6e189dd159c48b5779679d0563fab85e9b848992
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736413"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="a425c-102">Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a425c-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="a425c-103">V některých aplikacích se může v nadřazeném okně MDI lišit druh podřízeného okna rozhraní MDI (Multiple Document Interface).</span><span class="sxs-lookup"><span data-stu-id="a425c-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="a425c-104">Nadřazený objekt MDI může být například tabulka a podřízená položka MDI může být graf.</span><span class="sxs-lookup"><span data-stu-id="a425c-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="a425c-105">V takovém případě chcete aktualizovat obsah nabídky nadřazeného objektu MDI s obsahem nabídky podřízeného objektu MDI, protože jsou aktivována podřízená okna MDI různých druhů.</span><span class="sxs-lookup"><span data-stu-id="a425c-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="a425c-106">Následující postup používá vlastnosti <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> k vložení skupiny položek nabídky z podřízené nabídky MDI do rozevíracího seznamu v rámci nadřazené nabídky MDI.</span><span class="sxs-lookup"><span data-stu-id="a425c-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="a425c-107">Zavření podřízeného okna MDI odebere položky vložené nabídky z nadřazeného objektu MDI.</span><span class="sxs-lookup"><span data-stu-id="a425c-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="a425c-108">Vložení prvku MenuStrip do rozevírací nabídky MDI</span><span class="sxs-lookup"><span data-stu-id="a425c-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="a425c-109">Vytvořte formulář a nastavte jeho vlastnost <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a425c-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="a425c-110">Přidejte <xref:System.Windows.Forms.MenuStrip> do `Form1` a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a425c-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="a425c-111">Přidejte položku nabídky nejvyšší úrovně do `Form1`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.Control.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="a425c-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="a425c-112">Přidejte tři položky podnabídky do položky nabídky `&File` a nastavte jejich vlastnosti <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Open`, `&Import from`a `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="a425c-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="a425c-113">Přidejte dvě položky podnabídky do položky podnabídky `&Import from` a nastavte jejich vlastnosti <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Word` a `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="a425c-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="a425c-114">Přidejte do projektu formulář, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`ho <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a425c-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="a425c-115">Přidejte položku nabídky nejvyšší úrovně do `Form2`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="a425c-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="a425c-116">Přidejte položky podnabídky do nabídky `&File` `Form2` v následujícím pořadí: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`a další <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="a425c-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="a425c-117">Nastavte <xref:System.Windows.Forms.MergeAction> a vlastnosti <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> položek nabídky `Form2`, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a425c-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a425c-118">Položka nabídky Form2</span><span class="sxs-lookup"><span data-stu-id="a425c-118">Form2 menu item</span></span>|<span data-ttu-id="a425c-119">Hodnota MergeAction</span><span class="sxs-lookup"><span data-stu-id="a425c-119">MergeAction value</span></span>|<span data-ttu-id="a425c-120">Hodnota MergeIndex</span><span class="sxs-lookup"><span data-stu-id="a425c-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="a425c-121">Soubor</span><span class="sxs-lookup"><span data-stu-id="a425c-121">File</span></span>|<span data-ttu-id="a425c-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="a425c-122">MatchOnly</span></span>|<span data-ttu-id="a425c-123">-1</span><span class="sxs-lookup"><span data-stu-id="a425c-123">-1</span></span>|  
    |<span data-ttu-id="a425c-124">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="a425c-124">Separator</span></span>|<span data-ttu-id="a425c-125">Insert</span><span class="sxs-lookup"><span data-stu-id="a425c-125">Insert</span></span>|<span data-ttu-id="a425c-126">2</span><span class="sxs-lookup"><span data-stu-id="a425c-126">2</span></span>|  
    |<span data-ttu-id="a425c-127">Uložit</span><span class="sxs-lookup"><span data-stu-id="a425c-127">Save</span></span>|<span data-ttu-id="a425c-128">Insert</span><span class="sxs-lookup"><span data-stu-id="a425c-128">Insert</span></span>|<span data-ttu-id="a425c-129">3</span><span class="sxs-lookup"><span data-stu-id="a425c-129">3</span></span>|  
    |<span data-ttu-id="a425c-130">Uložit a zavřít</span><span class="sxs-lookup"><span data-stu-id="a425c-130">Save and Close</span></span>|<span data-ttu-id="a425c-131">Insert</span><span class="sxs-lookup"><span data-stu-id="a425c-131">Insert</span></span>|<span data-ttu-id="a425c-132">4</span><span class="sxs-lookup"><span data-stu-id="a425c-132">4</span></span>|  
    |<span data-ttu-id="a425c-133">Oddělovač</span><span class="sxs-lookup"><span data-stu-id="a425c-133">Separator</span></span>|<span data-ttu-id="a425c-134">Insert</span><span class="sxs-lookup"><span data-stu-id="a425c-134">Insert</span></span>|<span data-ttu-id="a425c-135">5</span><span class="sxs-lookup"><span data-stu-id="a425c-135">5</span></span>|  
  
10. <span data-ttu-id="a425c-136">Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="a425c-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="a425c-137">V rámci obslužné rutiny události vložte kód podobný následujícímu příkladu kódu pro vytvoření a zobrazení nových instancí `Form2` jako podřízených objektů MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a425c-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="a425c-138">Umístěte kód podobný následujícímu příkladu kódu v `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a425c-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a425c-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a425c-139">Compiling the Code</span></span>  
 <span data-ttu-id="a425c-140">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a425c-140">This example requires:</span></span>  
  
- <span data-ttu-id="a425c-141">Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="a425c-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="a425c-142"><xref:System.Windows.Forms.MenuStrip> ovládací prvek `Form1` s názvem `menuStrip1`a ovládací prvek <xref:System.Windows.Forms.MenuStrip> na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="a425c-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="a425c-143">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="a425c-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a425c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a425c-144">See also</span></span>

- [<span data-ttu-id="a425c-145">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="a425c-145">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="a425c-146">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="a425c-146">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="a425c-147">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="a425c-147">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
