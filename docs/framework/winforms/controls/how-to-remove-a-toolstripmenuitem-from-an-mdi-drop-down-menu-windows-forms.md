---
title: 'Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI'
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
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735849"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="7d02e-102">Postupy: Odebrání prvku ToolStripMenuItem z rozevíracího seznamu MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7d02e-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="7d02e-103">V některých aplikacích se může v nadřazeném okně MDI lišit druh podřízeného okna rozhraní MDI (Multiple Document Interface).</span><span class="sxs-lookup"><span data-stu-id="7d02e-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="7d02e-104">Nadřazený objekt MDI může být například tabulka a podřízená položka MDI může být graf.</span><span class="sxs-lookup"><span data-stu-id="7d02e-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="7d02e-105">V takovém případě chcete aktualizovat obsah nabídky nadřazeného objektu MDI s obsahem nabídky podřízeného objektu MDI, protože jsou aktivována podřízená okna MDI různých druhů.</span><span class="sxs-lookup"><span data-stu-id="7d02e-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="7d02e-106">Následující postup používá vlastnosti <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> k odebrání položky nabídky z rozevírací části v nadřazené nabídce MDI.</span><span class="sxs-lookup"><span data-stu-id="7d02e-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="7d02e-107">Zavření podřízeného okna MDI obnoví odebrané položky nabídky do nadřazené nabídky MDI.</span><span class="sxs-lookup"><span data-stu-id="7d02e-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="7d02e-108">Odebrání prvku MenuStrip z rozevírací nabídky MDI</span><span class="sxs-lookup"><span data-stu-id="7d02e-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="7d02e-109">Vytvořte formulář a nastavte jeho vlastnost <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="7d02e-110">Přidejte <xref:System.Windows.Forms.MenuStrip> do `Form1` a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="7d02e-111">Přidejte položku nabídky nejvyšší úrovně do `Form1`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.Control.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="7d02e-112">Přidejte tři položky podnabídky do položky nabídky `&File` a nastavte jejich vlastnosti <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Open`, `&Import from`a `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="7d02e-113">Přidejte dvě položky podnabídky do položky podnabídky `&Import from` a nastavte jejich vlastnosti <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Word` a `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="7d02e-114">Přidejte do projektu formulář, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`ho <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="7d02e-115">Přidejte položku nabídky nejvyšší úrovně do `Form2`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="7d02e-116">Přidejte položku podnabídky `&Import from` do nabídky `&File` `Form2`a přidejte položku `&Word` podnabídky do nabídky `&File`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="7d02e-117">Nastavte <xref:System.Windows.Forms.MergeAction> a vlastnosti <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> položek nabídky `Form2`, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="7d02e-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="7d02e-118">Položka nabídky Form2</span><span class="sxs-lookup"><span data-stu-id="7d02e-118">Form2 menu item</span></span>|<span data-ttu-id="7d02e-119">Hodnota MergeAction</span><span class="sxs-lookup"><span data-stu-id="7d02e-119">MergeAction value</span></span>|<span data-ttu-id="7d02e-120">Hodnota MergeIndex</span><span class="sxs-lookup"><span data-stu-id="7d02e-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="7d02e-121">Soubor</span><span class="sxs-lookup"><span data-stu-id="7d02e-121">File</span></span>|<span data-ttu-id="7d02e-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="7d02e-122">MatchOnly</span></span>|<span data-ttu-id="7d02e-123">-1</span><span class="sxs-lookup"><span data-stu-id="7d02e-123">-1</span></span>|  
    |<span data-ttu-id="7d02e-124">Importovat z</span><span class="sxs-lookup"><span data-stu-id="7d02e-124">Import from</span></span>|<span data-ttu-id="7d02e-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="7d02e-125">MatchOnly</span></span>|<span data-ttu-id="7d02e-126">-1</span><span class="sxs-lookup"><span data-stu-id="7d02e-126">-1</span></span>|  
    |<span data-ttu-id="7d02e-127">Word</span><span class="sxs-lookup"><span data-stu-id="7d02e-127">Word</span></span>|<span data-ttu-id="7d02e-128">Odebrat</span><span class="sxs-lookup"><span data-stu-id="7d02e-128">Remove</span></span>|<span data-ttu-id="7d02e-129">-1</span><span class="sxs-lookup"><span data-stu-id="7d02e-129">-1</span></span>|  
  
10. <span data-ttu-id="7d02e-130">V `Form1`vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="7d02e-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="7d02e-131">V rámci obslužné rutiny události vložte kód podobný následujícímu příkladu kódu, který vytvoří a zobrazí nové instance `Form2` jako podřízené objekty MDI `Form1`:</span><span class="sxs-lookup"><span data-stu-id="7d02e-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
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
  
12. <span data-ttu-id="7d02e-132">Umístěte kód podobný následujícímu příkladu kódu v `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7d02e-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d02e-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7d02e-133">Compiling the Code</span></span>  
 <span data-ttu-id="7d02e-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7d02e-134">This example requires:</span></span>  
  
- <span data-ttu-id="7d02e-135">Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="7d02e-136"><xref:System.Windows.Forms.MenuStrip> ovládací prvek `Form1` s názvem `menuStrip1`a ovládací prvek <xref:System.Windows.Forms.MenuStrip> na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="7d02e-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="7d02e-137">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d02e-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d02e-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d02e-138">See also</span></span>

- [<span data-ttu-id="7d02e-139">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="7d02e-139">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="7d02e-140">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="7d02e-140">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="7d02e-141">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="7d02e-141">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
