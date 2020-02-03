---
title: Seskupení položek v ovládacím prvku ListView
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
ms.openlocfilehash: 45846751780f433c29b186fe8b9a908f5d295ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736627"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="baff7-102">Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="baff7-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="baff7-103">Pomocí funkce seskupení ovládacího prvku <xref:System.Windows.Forms.ListView> můžete zobrazit související sady položek ve skupinách.</span><span class="sxs-lookup"><span data-stu-id="baff7-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="baff7-104">Tyto skupiny jsou oddělené na obrazovce vodorovnými záhlavími skupin, která obsahují názvy skupin.</span><span class="sxs-lookup"><span data-stu-id="baff7-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="baff7-105">Skupiny <xref:System.Windows.Forms.ListView> můžete použít k jednoduššímu procházení rozsáhlých seznamů tím, že položky seskupíte podle abecedy, podle data nebo do jiného logického seskupení.</span><span class="sxs-lookup"><span data-stu-id="baff7-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="baff7-106">Následující obrázek znázorňuje některé seskupené položky.</span><span class="sxs-lookup"><span data-stu-id="baff7-106">The following image shows some grouped items.</span></span>  
  
 ![Snímek obrazovky s lichými a sudými skupinami ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="baff7-108">Chcete-li povolit seskupování, je nutné nejprve vytvořit jednu nebo více skupin buď v návrháři, nebo programově.</span><span class="sxs-lookup"><span data-stu-id="baff7-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="baff7-109">Po definování skupiny můžete přiřadit <xref:System.Windows.Forms.ListView> položky do skupin.</span><span class="sxs-lookup"><span data-stu-id="baff7-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="baff7-110">Položky můžete také přesunout z jedné skupiny do jiné programově.</span><span class="sxs-lookup"><span data-stu-id="baff7-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="baff7-111">Přidání skupin</span><span class="sxs-lookup"><span data-stu-id="baff7-111">To add groups</span></span>  
  
1. <span data-ttu-id="baff7-112">Použijte metodu <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> kolekce <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="baff7-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="baff7-113">Odebrání skupin</span><span class="sxs-lookup"><span data-stu-id="baff7-113">To remove groups</span></span>  
  
1. <span data-ttu-id="baff7-114">Použijte metodu <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> kolekce <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="baff7-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="baff7-115">Metoda <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> odstraní jednu skupinu. Metoda <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> odebere ze seznamu všechny skupiny.</span><span class="sxs-lookup"><span data-stu-id="baff7-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="baff7-116">Odebráním skupiny nedojde k odebrání položek v této skupině.</span><span class="sxs-lookup"><span data-stu-id="baff7-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="baff7-117">Přiřazení položek do skupin nebo přesouvání položek mezi skupinami</span><span class="sxs-lookup"><span data-stu-id="baff7-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="baff7-118">Nastavte vlastnost <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="baff7-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="baff7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="baff7-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="baff7-120">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="baff7-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="baff7-121">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="baff7-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="baff7-122">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="baff7-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
