---
title: 'Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: bfe84ccb30b13b8232172749454bf8f3625269ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139201"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="63f59-102">Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="63f59-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="63f59-103">Můžete vytvářet aplikace, které můžete otevřít několik dokumentů ve stejný čas a zkopírujte a vložte obsah z jednoho dokumentu do jiné rozhraní více dokumentů (MDI).</span><span class="sxs-lookup"><span data-stu-id="63f59-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="63f59-104">Tento postup ukazuje, jak vytvořit seznam všech aktivních podřízených formulářů v nabídce okno nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="63f59-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="63f59-105">Vytvoření seznamu okna MDI v prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="63f59-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1.  <span data-ttu-id="63f59-106">Vytvořit formulář a nastavte jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="63f59-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="63f59-107">Přidat <xref:System.Windows.Forms.MenuStrip> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="63f59-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3.  <span data-ttu-id="63f59-108">Přidání dvou položek nabídek nejvyšší úrovně na <xref:System.Windows.Forms.MenuStrip> a nastavte jejich <xref:System.Windows.Forms.Control.Text%2A> vlastností `&File` a `&Window`.</span><span class="sxs-lookup"><span data-stu-id="63f59-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4.  <span data-ttu-id="63f59-109">Přidat podnabídku položku `&File` položky nabídky a nastavte jeho <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost `&Open`.</span><span class="sxs-lookup"><span data-stu-id="63f59-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5.  <span data-ttu-id="63f59-110">Nastavte <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="63f59-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6.  <span data-ttu-id="63f59-111">Přidat formuláře do projektu a přidejte ovládací prvek, například jiného <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="63f59-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7.  <span data-ttu-id="63f59-112">Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="63f59-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8.  <span data-ttu-id="63f59-113">V rámci obslužné rutiny události, vložte kód podobný následujícímu k vytváření a zobrazování nových instancí `Form2` jako podřízený objekt MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="63f59-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
9. <span data-ttu-id="63f59-114">Umístěte kód v následujícím postupem `&New`<xref:System.Windows.Forms.ToolStripMenuItem> zaregistrovat obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="63f59-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63f59-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="63f59-115">Compiling the Code</span></span>  
 <span data-ttu-id="63f59-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="63f59-116">This example requires:</span></span>  
  
-   <span data-ttu-id="63f59-117">Dvě <xref:System.Windows.Forms.Form> ovládací prvky s názvem `Form1` a `Form2`.</span><span class="sxs-lookup"><span data-stu-id="63f59-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="63f59-118">A <xref:System.Windows.Forms.MenuStrip> ovládání na `Form1` s názvem `menuStrip1`a <xref:System.Windows.Forms.MenuStrip> ovládání na `Form2` s názvem `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="63f59-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="63f59-119">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="63f59-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f59-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63f59-120">See also</span></span>

- [<span data-ttu-id="63f59-121">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="63f59-121">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="63f59-122">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="63f59-122">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="63f59-123">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="63f59-123">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
