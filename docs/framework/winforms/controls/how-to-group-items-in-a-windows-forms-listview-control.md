---
title: 'Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: f616436671da449e4f7b47c0a5d0c1b576584a1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312303"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="a0c97-102">Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="a0c97-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="a0c97-103">S funkcí seskupování <xref:System.Windows.Forms.ListView> ovládacího prvku, lze zobrazit související sady položek ve skupinách.</span><span class="sxs-lookup"><span data-stu-id="a0c97-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="a0c97-104">Tyto skupiny jsou oddělené na obrazovce záhlaví vodorovné skupin, které obsahují názvů skupin.</span><span class="sxs-lookup"><span data-stu-id="a0c97-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="a0c97-105">Můžete použít <xref:System.Windows.Forms.ListView> skupiny, aby měli procházení rozsáhlých seznamů jednodušší seskupováním položek podle abecedy, datum, nebo jiné logické seskupení.</span><span class="sxs-lookup"><span data-stu-id="a0c97-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="a0c97-106">Následující obrázek ukazuje některé seskupených položek.</span><span class="sxs-lookup"><span data-stu-id="a0c97-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="a0c97-107">![Skupiny ListView](./media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="a0c97-107">![ListView Groups](./media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="a0c97-108">Položky jsou seskupeny ListView</span><span class="sxs-lookup"><span data-stu-id="a0c97-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="a0c97-109">Chcete-li povolit seskupování, musíte nejdřív vytvořit jeden nebo více skupin v Návrháři nebo prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="a0c97-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="a0c97-110">Po definování skupinu můžete přiřadit <xref:System.Windows.Forms.ListView> položky do skupin.</span><span class="sxs-lookup"><span data-stu-id="a0c97-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="a0c97-111">Můžete také přesouvání položek z jedné skupiny do jiné prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="a0c97-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c97-112"><xref:System.Windows.Forms.ListView> jsou k dispozici pouze na skupiny [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a0c97-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a0c97-113">Ve starších operačních systémech jakýkoli kód týkajících se skupin nemá žádný vliv a skupin nebude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="a0c97-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="a0c97-114">Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0c97-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="a0c97-115">Přidání skupin</span><span class="sxs-lookup"><span data-stu-id="a0c97-115">To add groups</span></span>  
  
1. <span data-ttu-id="a0c97-116">Použití <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="a0c97-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="a0c97-117">Chcete-li odebrat skupiny</span><span class="sxs-lookup"><span data-stu-id="a0c97-117">To remove groups</span></span>  
  
1. <span data-ttu-id="a0c97-118">Použití <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="a0c97-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="a0c97-119"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Metoda odebere jednu skupinu; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda odebere všechny skupiny ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="a0c97-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0c97-120">Odebrání skupinového neodebírá položky v rámci dané skupiny.</span><span class="sxs-lookup"><span data-stu-id="a0c97-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="a0c97-121">K přiřazení položky do skupin nebo přesouvat položky mezi skupinami</span><span class="sxs-lookup"><span data-stu-id="a0c97-121">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="a0c97-122">Nastavte <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> vlastnost jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="a0c97-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="a0c97-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0c97-123">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="a0c97-124">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="a0c97-124">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="a0c97-125">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="a0c97-125">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="a0c97-126">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="a0c97-126">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
