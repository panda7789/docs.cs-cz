---
title: 'Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 9c39b80c06cae91c43c7a79390cef71ae781489e
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442741"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a><span data-ttu-id="9efd7-102">Postupy: Připojení prvku MenuStrip do nadřazeného okna MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9efd7-102">How to: Append a MenuStrip to an MDI Parent Window (Windows Forms)</span></span>
<span data-ttu-id="9efd7-103">V některých aplikacích druh podřízené okno rozhraní více dokumentů (MDI) může lišit od nadřazeného okna MDI.</span><span class="sxs-lookup"><span data-stu-id="9efd7-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="9efd7-104">Například nadřazený objekt MDI může být tabulku a podřízený formulář MDI může být grafu.</span><span class="sxs-lookup"><span data-stu-id="9efd7-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="9efd7-105">V takovém případě budete chtít aktualizovat obsah nabídky nadřazený objekt MDI obsah nabídky podřízený formulář MDI jako podřízená okna MDI různé druhy se aktivují.</span><span class="sxs-lookup"><span data-stu-id="9efd7-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="9efd7-106">Následující postup používá <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, a <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnosti, které chcete připojit k nadřazené nabídky MDI podřízené nabídky MDI.</span><span class="sxs-lookup"><span data-stu-id="9efd7-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to append the MDI child menu to the MDI parent menu.</span></span> <span data-ttu-id="9efd7-107">Zavření podřízené okno MDI odebere připojený nabídku z nadřazený objekt MDI.</span><span class="sxs-lookup"><span data-stu-id="9efd7-107">Closing the MDI child window removes the appended menu from the MDI parent.</span></span>  
  
 <span data-ttu-id="9efd7-108">Viz také [aplikace rozhraní více dokumentů (MDI)](../advanced/multiple-document-interface-mdi-applications.md).</span><span class="sxs-lookup"><span data-stu-id="9efd7-108">Also see [Multiple-Document Interface (MDI) Applications](../advanced/multiple-document-interface-mdi-applications.md).</span></span>  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a><span data-ttu-id="9efd7-109">Připojit položky nabídky nadřazený objekt MDI</span><span class="sxs-lookup"><span data-stu-id="9efd7-109">To append a menu item to an MDI parent</span></span>  
  
1.  <span data-ttu-id="9efd7-110">Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-110">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="9efd7-111">Přidat <xref:System.Windows.Forms.MenuStrip> k `Form1` a nastavit <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-111">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="9efd7-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `Form1` <xref:System.Windows.Forms.MenuStrip> k `false`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the `Form1`<xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
4.  <span data-ttu-id="9efd7-113">Přidání položky do nabídek nejvyšší úrovně `Form1` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `&File`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-113">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
5.  <span data-ttu-id="9efd7-114">Přidat podnabídku položku `&File` položky nabídky a nastavte jeho <xref:System.Windows.Forms.Form.Text%2A> vlastnost `&Open`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-114">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Open`.</span></span>  
  
6.  <span data-ttu-id="9efd7-115">Přidání formuláře do projektu, přidejte <xref:System.Windows.Forms.MenuStrip> do formuláře a nastavte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost `Form2` <xref:System.Windows.Forms.MenuStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-115">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="9efd7-116">Přidání položky do nabídek nejvyšší úrovně `Form2` <xref:System.Windows.Forms.MenuStrip> a nastavte jeho <xref:System.Windows.Forms.Form.Text%2A> vlastnost `&Special`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-116">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Special`.</span></span>  
  
8.  <span data-ttu-id="9efd7-117">Přidání dvou položek podnabídky do `&Special` položky nabídky a nastavte jejich <xref:System.Windows.Forms.Form.Text%2A> vlastností `Command&1` a `Command&2`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9efd7-117">Add two submenu items to the `&Special` menu item and set their <xref:System.Windows.Forms.Form.Text%2A> properties to `Command&1` and `Command&2`, respectively.</span></span>  
  
9. <span data-ttu-id="9efd7-118">Nastavte <xref:System.Windows.Forms.MergeAction> vlastnost `&Special`, `Command&1`, a `Command&2` položky nabídky <xref:System.Windows.Forms.MergeAction.Append>.</span><span class="sxs-lookup"><span data-stu-id="9efd7-118">Set the <xref:System.Windows.Forms.MergeAction> property of the `&Special`, `Command&1`, and `Command&2` menu items to <xref:System.Windows.Forms.MergeAction.Append>.</span></span>  
  
10. <span data-ttu-id="9efd7-119">Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="9efd7-119">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="9efd7-120">V rámci obslužné rutiny události vložení kódu podobně jako v následujícím příkladu kódu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-120">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="9efd7-121">Umístit podobně jako v následujícím příkladu kódu v kódu `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> zaregistrovat obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="9efd7-121">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9efd7-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9efd7-122">Compiling the Code</span></span>  
 <span data-ttu-id="9efd7-123">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9efd7-123">This example requires:</span></span>  
  
-   <span data-ttu-id="9efd7-124">Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-124">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="9efd7-125">A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="9efd7-125">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="9efd7-126">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="9efd7-126">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>
