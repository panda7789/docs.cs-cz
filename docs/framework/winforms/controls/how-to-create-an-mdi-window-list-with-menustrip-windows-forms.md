---
title: "Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)"
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
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8bf09170b4def3f041e34942a968fdf41fcdf66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="8f2d9-102">Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8f2d9-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="8f2d9-103">Použijte rozhraní více dokumentů (MDI) k vytvoření aplikace, které můžete otevřít několik dokumentů na stejný čas a zkopírujte a vložte obsah z jednoho dokumentu na druhý.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="8f2d9-104">Tento postup ukazuje, jak vytvořit seznam všech aktivních podřízených formulářů v nabídce okno nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="8f2d9-105">K vytvoření seznamu okna MDI v prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="8f2d9-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1.  <span data-ttu-id="8f2d9-106">Vytvoření formuláře a nastavit jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="8f2d9-107">Přidat <xref:System.Windows.Forms.MenuStrip> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3.  <span data-ttu-id="8f2d9-108">Přidat dvě položky do nejvyšší úrovně <xref:System.Windows.Forms.MenuStrip> a nastavte jejich <xref:System.Windows.Forms.Control.Text%2A> vlastnosti, které chcete `&File` a `&Window`.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4.  <span data-ttu-id="8f2d9-109">Přidání položky podnabídky a `&File` položky nabídky a sadu jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&Open`.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5.  <span data-ttu-id="8f2d9-110">Nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6.  <span data-ttu-id="8f2d9-111">Přidejte formuláře do projektu a přidejte chcete ovládací prvek, například jiného <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7.  <span data-ttu-id="8f2d9-112">Vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> události `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8.  <span data-ttu-id="8f2d9-113">V rámci obslužné rutiny události vložení kódu podobný následujícímu k vytváření a zobrazování nové instance třídy `Form2` jako podřízené objekty MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. <span data-ttu-id="8f2d9-114">Umístěte kód jako následující `&New` <xref:System.Windows.Forms.ToolStripMenuItem> k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f2d9-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8f2d9-115">Compiling the Code</span></span>  
 <span data-ttu-id="8f2d9-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8f2d9-116">This example requires:</span></span>  
  
-   <span data-ttu-id="8f2d9-117">Dva <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="8f2d9-118">A <xref:System.Windows.Forms.MenuStrip> řízení na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> řízení na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="8f2d9-119">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f2d9-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2d9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f2d9-120">See Also</span></span>  
 [<span data-ttu-id="8f2d9-121">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="8f2d9-121">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="8f2d9-122">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="8f2d9-122">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="8f2d9-123">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="8f2d9-123">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
