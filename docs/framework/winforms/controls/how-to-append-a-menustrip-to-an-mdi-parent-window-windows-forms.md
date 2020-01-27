---
title: 'Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747153"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a><span data-ttu-id="d28ad-102">Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d28ad-102">How to: Append a MenuStrip to an MDI Parent Window (Windows Forms)</span></span>
<span data-ttu-id="d28ad-103">V některých aplikacích se může v nadřazeném okně MDI lišit druh podřízeného okna rozhraní MDI (Multiple Document Interface).</span><span class="sxs-lookup"><span data-stu-id="d28ad-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="d28ad-104">Nadřazený objekt MDI může být například tabulka a podřízená položka MDI může být graf.</span><span class="sxs-lookup"><span data-stu-id="d28ad-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="d28ad-105">V takovém případě chcete aktualizovat obsah nabídky nadřazeného objektu MDI s obsahem nabídky podřízeného objektu MDI, protože jsou aktivována podřízená okna MDI různých druhů.</span><span class="sxs-lookup"><span data-stu-id="d28ad-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="d28ad-106">Následující postup používá vlastnosti <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> k připojení podřízené nabídky MDI do nadřazené nabídky MDI.</span><span class="sxs-lookup"><span data-stu-id="d28ad-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to append the MDI child menu to the MDI parent menu.</span></span> <span data-ttu-id="d28ad-107">Zavřením podřízeného okna MDI dojde k odebrání připojené nabídky z nadřazeného objektu MDI.</span><span class="sxs-lookup"><span data-stu-id="d28ad-107">Closing the MDI child window removes the appended menu from the MDI parent.</span></span>  
  
 <span data-ttu-id="d28ad-108">Viz také [aplikace MDI (Multiple Document Interface)](../advanced/multiple-document-interface-mdi-applications.md).</span><span class="sxs-lookup"><span data-stu-id="d28ad-108">Also see [Multiple-Document Interface (MDI) Applications](../advanced/multiple-document-interface-mdi-applications.md).</span></span>  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a><span data-ttu-id="d28ad-109">Postup připojení položky nabídky k nadřazené položce MDI</span><span class="sxs-lookup"><span data-stu-id="d28ad-109">To append a menu item to an MDI parent</span></span>  
  
1. <span data-ttu-id="d28ad-110">Vytvořte formulář a nastavte jeho vlastnost <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-110">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="d28ad-111">Přidejte <xref:System.Windows.Forms.MenuStrip> do `Form1` a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-111">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="d28ad-112">Vlastnost <xref:System.Windows.Forms.ToolStripItem.Visible%2A> `Form1`<xref:System.Windows.Forms.MenuStrip> nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the `Form1`<xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
4. <span data-ttu-id="d28ad-113">Přidejte položku nabídky nejvyšší úrovně do `Form1`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.Control.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-113">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
5. <span data-ttu-id="d28ad-114">Přidejte položku podnabídky do položky nabídky `&File` a nastavte její vlastnost <xref:System.Windows.Forms.Form.Text%2A> na `&Open`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-114">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Open`.</span></span>  
  
6. <span data-ttu-id="d28ad-115">Přidejte do projektu formulář, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`ho <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-115">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="d28ad-116">Přidejte položku nabídky nejvyšší úrovně do `Form2`<xref:System.Windows.Forms.MenuStrip> a nastavte její vlastnost <xref:System.Windows.Forms.Form.Text%2A> na `&Special`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-116">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Special`.</span></span>  
  
8. <span data-ttu-id="d28ad-117">Přidejte dvě položky podnabídky do položky nabídky `&Special` a nastavte jejich vlastnosti <xref:System.Windows.Forms.Form.Text%2A> na `Command&1` a `Command&2`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d28ad-117">Add two submenu items to the `&Special` menu item and set their <xref:System.Windows.Forms.Form.Text%2A> properties to `Command&1` and `Command&2`, respectively.</span></span>  
  
9. <span data-ttu-id="d28ad-118">Nastavte vlastnost <xref:System.Windows.Forms.MergeAction> položek nabídky `&Special`, `Command&1`a `Command&2` na <xref:System.Windows.Forms.MergeAction.Append>.</span><span class="sxs-lookup"><span data-stu-id="d28ad-118">Set the <xref:System.Windows.Forms.MergeAction> property of the `&Special`, `Command&1`, and `Command&2` menu items to <xref:System.Windows.Forms.MergeAction.Append>.</span></span>  
  
10. <span data-ttu-id="d28ad-119">Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="d28ad-119">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="d28ad-120">V rámci obslužné rutiny události vložte kód podobný následujícímu příkladu kódu pro vytvoření a zobrazení nových instancí `Form2` jako podřízených objektů MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-120">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="d28ad-121">Umístěte kód podobný následujícímu příkladu kódu v `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d28ad-121">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d28ad-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d28ad-122">Compiling the Code</span></span>  
 <span data-ttu-id="d28ad-123">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d28ad-123">This example requires:</span></span>  
  
- <span data-ttu-id="d28ad-124">Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-124">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="d28ad-125"><xref:System.Windows.Forms.MenuStrip> ovládací prvek `Form1` s názvem `menuStrip1`a ovládací prvek <xref:System.Windows.Forms.MenuStrip> na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="d28ad-125">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="d28ad-126">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="d28ad-126">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>
