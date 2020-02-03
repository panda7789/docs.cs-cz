---
title: Seskupení položek v ovládacím prvku ListView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736679"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="981ec-102">Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="981ec-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="981ec-103">Funkce seskupení ovládacího prvku <xref:System.Windows.Forms.ListView> umožňuje zobrazit související sady položek ve skupinách.</span><span class="sxs-lookup"><span data-stu-id="981ec-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="981ec-104">Tyto skupiny jsou oddělené na obrazovce vodorovnými záhlavími skupin, která obsahují názvy skupin.</span><span class="sxs-lookup"><span data-stu-id="981ec-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="981ec-105">Skupiny <xref:System.Windows.Forms.ListView> můžete použít k jednoduššímu procházení rozsáhlých seznamů tím, že položky seskupíte podle abecedy, podle data nebo do jiného logického seskupení.</span><span class="sxs-lookup"><span data-stu-id="981ec-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="981ec-106">Následující obrázek ukazuje některé seskupené položky:</span><span class="sxs-lookup"><span data-stu-id="981ec-106">The following image shows some grouped items:</span></span>

![Čísla rozdělená na liché a sudé skupiny.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="981ec-108">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="981ec-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="981ec-109">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="981ec-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="981ec-110">Chcete-li povolit seskupování, je nutné nejprve vytvořit jeden nebo více <xref:System.Windows.Forms.ListViewGroup> objektů buď v návrháři, nebo programově.</span><span class="sxs-lookup"><span data-stu-id="981ec-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="981ec-111">Po definování skupiny můžete k ní přiřadit položky.</span><span class="sxs-lookup"><span data-stu-id="981ec-111">Once a group has been defined, you can assign items to it.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="981ec-112">Přidání nebo odebrání skupin v Návrháři</span><span class="sxs-lookup"><span data-stu-id="981ec-112">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="981ec-113">V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="981ec-113">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="981ec-114">Zobrazí se **Editor kolekce objektu ListView** .</span><span class="sxs-lookup"><span data-stu-id="981ec-114">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="981ec-115">Chcete-li přidat skupinu, klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="981ec-115">To add a group, click the **Add** button.</span></span> <span data-ttu-id="981ec-116">Pak můžete nastavit vlastnosti nové skupiny, například <xref:System.Windows.Forms.ListViewGroup.Header%2A> a vlastnosti <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="981ec-116">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="981ec-117">Pokud chcete skupinu odebrat, vyberte ji a klikněte na tlačítko **Odebrat** .</span><span class="sxs-lookup"><span data-stu-id="981ec-117">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="981ec-118">Přiřazení položek do skupin v Návrháři</span><span class="sxs-lookup"><span data-stu-id="981ec-118">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="981ec-119">V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="981ec-119">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="981ec-120">Zobrazí se **Editor kolekce ListViewItems** .</span><span class="sxs-lookup"><span data-stu-id="981ec-120">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="981ec-121">Chcete-li přidat novou položku, klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="981ec-121">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="981ec-122">Pak můžete nastavit vlastnosti nové položky, například <xref:System.Windows.Forms.ListViewItem.Text%2A> a vlastnosti <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.</span><span class="sxs-lookup"><span data-stu-id="981ec-122">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="981ec-123">Vyberte vlastnost <xref:System.Windows.Forms.ListViewItem.Group%2A> a v rozevíracím seznamu vyberte skupinu.</span><span class="sxs-lookup"><span data-stu-id="981ec-123">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="981ec-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="981ec-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="981ec-125">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="981ec-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="981ec-126">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="981ec-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="981ec-127">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="981ec-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
