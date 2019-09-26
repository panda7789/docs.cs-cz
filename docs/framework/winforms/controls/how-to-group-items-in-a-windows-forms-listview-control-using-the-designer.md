---
title: 'Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69039403"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="0f102-102">Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="0f102-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="0f102-103">Funkce <xref:System.Windows.Forms.ListView> seskupení ovládacího prvku umožňuje zobrazit související sady položek ve skupinách.</span><span class="sxs-lookup"><span data-stu-id="0f102-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="0f102-104">Tyto skupiny jsou oddělené na obrazovce vodorovnými záhlavími skupin, která obsahují názvy skupin.</span><span class="sxs-lookup"><span data-stu-id="0f102-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="0f102-105">Skupiny můžete použít <xref:System.Windows.Forms.ListView> k jednoduššímu procházení rozsáhlých seznamů tím, že položky seskupíte podle abecedy, podle data nebo do jiného logického seskupení.</span><span class="sxs-lookup"><span data-stu-id="0f102-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="0f102-106">Následující obrázek ukazuje některé seskupené položky:</span><span class="sxs-lookup"><span data-stu-id="0f102-106">The following image shows some grouped items:</span></span>

![Čísla rozdělená na liché a sudé skupiny.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="0f102-108">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ListView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="0f102-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="0f102-109">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0f102-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="0f102-110">Chcete-li povolit seskupování, je nutné nejprve vytvořit jeden <xref:System.Windows.Forms.ListViewGroup> nebo více objektů buď v návrháři, nebo programově.</span><span class="sxs-lookup"><span data-stu-id="0f102-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="0f102-111">Po definování skupiny můžete k ní přiřadit položky.</span><span class="sxs-lookup"><span data-stu-id="0f102-111">Once a group has been defined, you can assign items to it.</span></span>

> [!NOTE]
> <span data-ttu-id="0f102-112"><xref:System.Windows.Forms.ListView>skupiny jsou k dispozici [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] pouze v případě, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> že vaše aplikace volá metodu.</span><span class="sxs-lookup"><span data-stu-id="0f102-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0f102-113">Ve starších operačních systémech žádný kód týkající se skupin nemá žádný vliv a skupiny se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="0f102-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="0f102-114">Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f102-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="0f102-115">Přidání nebo odebrání skupin v Návrháři</span><span class="sxs-lookup"><span data-stu-id="0f102-115">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="0f102-116">V okně **vlastnosti** klikněte![na tlačítko se **třemi** tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio <xref:System.Windows.Forms.ListView.Groups%2A> .) vedle vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0f102-116">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="0f102-117">Zobrazí se **Editor kolekce objektu ListView** .</span><span class="sxs-lookup"><span data-stu-id="0f102-117">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="0f102-118">Chcete-li přidat skupinu, klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="0f102-118">To add a group, click the **Add** button.</span></span> <span data-ttu-id="0f102-119">Pak můžete nastavit vlastnosti nové skupiny, například <xref:System.Windows.Forms.ListViewGroup.Header%2A> vlastnosti a. <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A></span><span class="sxs-lookup"><span data-stu-id="0f102-119">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="0f102-120">Pokud chcete skupinu odebrat, vyberte ji a klikněte na tlačítko **Odebrat** .</span><span class="sxs-lookup"><span data-stu-id="0f102-120">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="0f102-121">Přiřazení položek do skupin v Návrháři</span><span class="sxs-lookup"><span data-stu-id="0f102-121">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="0f102-122">V okně **vlastnosti** klikněte![na tlačítko se **třemi** tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio <xref:System.Windows.Forms.ListView.Items%2A> .) vedle vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0f102-122">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="0f102-123">Zobrazí se **Editor kolekce ListViewItems** .</span><span class="sxs-lookup"><span data-stu-id="0f102-123">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="0f102-124">Chcete-li přidat novou položku, klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="0f102-124">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="0f102-125">Pak můžete nastavit vlastnosti nové položky, například <xref:System.Windows.Forms.ListViewItem.Text%2A> vlastnosti a. <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="0f102-125">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="0f102-126"><xref:System.Windows.Forms.ListViewItem.Group%2A> Vyberte vlastnost a v rozevíracím seznamu vyberte skupinu.</span><span class="sxs-lookup"><span data-stu-id="0f102-126">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f102-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f102-127">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="0f102-128">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="0f102-128">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="0f102-129">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="0f102-129">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="0f102-130">Postupy: Přidávání a odebírání položek pomocí ovládacího prvku model Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="0f102-130">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
