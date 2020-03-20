---
title: Položky skupiny v ovládacím prvku ListView
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141988"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="b3daf-102">Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="b3daf-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="b3daf-103">Pomocí funkce seskupení <xref:System.Windows.Forms.ListView> ovládacího prvku můžete zobrazit související sady položek ve skupinách.</span><span class="sxs-lookup"><span data-stu-id="b3daf-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="b3daf-104">Tyto skupiny jsou na obrazovce odděleny vodorovnými záhlavími skupin, které obsahují názvy skupin.</span><span class="sxs-lookup"><span data-stu-id="b3daf-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="b3daf-105"><xref:System.Windows.Forms.ListView> Pomocí skupin můžete usnadnit navigaci ve velkých seznamech seskupením položek abecedně, podle data nebo podle jiného logického seskupení.</span><span class="sxs-lookup"><span data-stu-id="b3daf-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="b3daf-106">Následující obrázek znázorňuje některé seskupené položky.</span><span class="sxs-lookup"><span data-stu-id="b3daf-106">The following image shows some grouped items.</span></span>  
  
 ![Snímek obrazovky s lichými a sudými skupinami ListView](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 <span data-ttu-id="b3daf-108">Chcete-li povolit seskupení, musíte nejprve vytvořit jednu nebo více skupin buď v návrháři nebo programově.</span><span class="sxs-lookup"><span data-stu-id="b3daf-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="b3daf-109">Po definování skupiny můžete položky přiřadit <xref:System.Windows.Forms.ListView> ke skupinám.</span><span class="sxs-lookup"><span data-stu-id="b3daf-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="b3daf-110">Položky můžete také programově přesunout z jedné skupiny do druhé.</span><span class="sxs-lookup"><span data-stu-id="b3daf-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="b3daf-111">Přidání skupin</span><span class="sxs-lookup"><span data-stu-id="b3daf-111">To add groups</span></span>  
  
1. <span data-ttu-id="b3daf-112">Použijte <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b3daf-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="b3daf-113">Odebrání skupin</span><span class="sxs-lookup"><span data-stu-id="b3daf-113">To remove groups</span></span>  
  
1. <span data-ttu-id="b3daf-114">Použijte <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> nebo <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b3daf-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="b3daf-115">Metoda <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> odebere jednu skupinu; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda odebere všechny skupiny ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="b3daf-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b3daf-116">Odebráním skupiny neodeberete položky v této skupině.</span><span class="sxs-lookup"><span data-stu-id="b3daf-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="b3daf-117">Přiřazení položek skupinám nebo přesunutí položek mezi skupinami</span><span class="sxs-lookup"><span data-stu-id="b3daf-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="b3daf-118">Nastavte <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> vlastnost jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="b3daf-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="b3daf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3daf-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="b3daf-120">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b3daf-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="b3daf-121">ListView – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b3daf-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="b3daf-122">Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="b3daf-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
