---
title: Přidání a odebrání položek s ovládacím prvkem ListView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732293"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="62736-102">Postupy: Přidávání a odebírání položek s ovládacím prvkem Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="62736-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="62736-103">Proces přidání položky do ovládacího prvku model Windows Forms <xref:System.Windows.Forms.ListView> se skládá hlavně z určení položky a přiřazení vlastností.</span><span class="sxs-lookup"><span data-stu-id="62736-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="62736-104">Přidávání a odebírání položek seznamu lze provést kdykoli.</span><span class="sxs-lookup"><span data-stu-id="62736-104">Adding or removing list items can be done at any time.</span></span>

<span data-ttu-id="62736-105">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="62736-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="62736-106">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="62736-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="62736-107">Přidání nebo odebrání položek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="62736-107">To add or remove items using the designer</span></span>

1. <span data-ttu-id="62736-108">Vyberte ovládací prvek <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="62736-108">Select the <xref:System.Windows.Forms.ListView> control.</span></span>

2. <span data-ttu-id="62736-109">V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="62736-109">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="62736-110">Zobrazí se **Editor kolekce ListViewItems** .</span><span class="sxs-lookup"><span data-stu-id="62736-110">The **ListViewItem Collection Editor** appears.</span></span>

3. <span data-ttu-id="62736-111">Chcete-li přidat položku, klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="62736-111">To add an item, click the **Add** button.</span></span> <span data-ttu-id="62736-112">Pak můžete nastavit vlastnosti nové položky, například <xref:System.Windows.Forms.ListView.Text%2A> a vlastnosti <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.</span><span class="sxs-lookup"><span data-stu-id="62736-112">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

4. <span data-ttu-id="62736-113">Pokud chcete položku odebrat, vyberte ji a klikněte na tlačítko **Odebrat** .</span><span class="sxs-lookup"><span data-stu-id="62736-113">To remove an item, select it and click the **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="62736-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="62736-114">See also</span></span>

- [<span data-ttu-id="62736-115">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="62736-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="62736-116">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="62736-116">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="62736-117">Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="62736-117">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="62736-118">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="62736-118">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="62736-119">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="62736-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="62736-120">Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="62736-120">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
