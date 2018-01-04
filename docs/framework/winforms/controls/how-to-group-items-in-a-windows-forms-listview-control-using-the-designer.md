---
title: "Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 537aff8a49e42fe521ca6e0b2b698a461d4f5eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="3371f-102">Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="3371f-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="3371f-103">Funkci seskupení <xref:System.Windows.Forms.ListView> řízení umožňuje zobrazit související sady položek ve skupinách.</span><span class="sxs-lookup"><span data-stu-id="3371f-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="3371f-104">Tyto skupiny jsou oddělené na obrazovce podle hlaviček vodorovné skupiny, které obsahují názvy skupiny.</span><span class="sxs-lookup"><span data-stu-id="3371f-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="3371f-105">Můžete použít <xref:System.Windows.Forms.ListView> skupiny, aby bylo navigace velké seznamy jednodušší podle abecedy, seskupení položek podle data, nebo pomocí jiné logické seskupení.</span><span class="sxs-lookup"><span data-stu-id="3371f-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="3371f-106">Následující obrázek ukazuje některé seskupené položky.</span><span class="sxs-lookup"><span data-stu-id="3371f-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="3371f-107">![ListView skupiny](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="3371f-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
  
 <span data-ttu-id="3371f-108">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3371f-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="3371f-109">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3371f-109">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
 <span data-ttu-id="3371f-110">Pokud chcete povolit seskupování, musíte nejdřív vytvořit jeden nebo více <xref:System.Windows.Forms.ListViewGroup> objektů v Návrháři nebo prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="3371f-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="3371f-111">Po definování skupiny, můžete přiřadit položky k němu.</span><span class="sxs-lookup"><span data-stu-id="3371f-111">Once a group has been defined, you can assign items to it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3371f-112"><xref:System.Windows.Forms.ListView>skupiny jsou k dispozici pouze na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="3371f-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3371f-113">V dřívějších operačních systémech žádný kód týkající se skupiny nemá žádný vliv a skupin nebude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="3371f-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="3371f-114">Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3371f-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="3371f-115">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="3371f-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3371f-116">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="3371f-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3371f-117">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="3371f-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="3371f-118">Chcete-li přidat nebo odebrat skupiny v Návrháři</span><span class="sxs-lookup"><span data-stu-id="3371f-118">To add or remove groups in the designer</span></span>  
  
1.  <span data-ttu-id="3371f-119">V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ListView.Groups%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3371f-119">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>  
  
     <span data-ttu-id="3371f-120">**Editor kolekce ListViewGroup** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="3371f-120">The **ListViewGroup Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="3371f-121">Chcete-li přidat skupinu, klikněte na tlačítko **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="3371f-121">To add a group, click the **Add** button.</span></span> <span data-ttu-id="3371f-122">Pak můžete nastavit vlastnosti nové skupiny, jako <xref:System.Windows.Forms.ListViewGroup.Header%2A> a <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3371f-122">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="3371f-123">Chcete-li odebrat skupinu, vyberte ho a klikněte na tlačítko **odebrat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="3371f-123">To remove a group, select it and click the **Remove** button.</span></span>  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="3371f-124">Přiřazení položky ke skupinám v Návrháři</span><span class="sxs-lookup"><span data-stu-id="3371f-124">To assign items to groups in the designer</span></span>  
  
1.  <span data-ttu-id="3371f-125">V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3371f-125">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="3371f-126">**Editor kolekce ListViewItem** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="3371f-126">The **ListViewItem Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="3371f-127">Chcete-li přidat novou položku, klikněte na tlačítko **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="3371f-127">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="3371f-128">Pak můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListViewItem.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3371f-128">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
3.  <span data-ttu-id="3371f-129">Vyberte <xref:System.Windows.Forms.ListViewItem.Group%2A> vlastnosti a pak vyberte skupinu z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="3371f-129">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3371f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3371f-130">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="3371f-131">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="3371f-131">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="3371f-132">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="3371f-132">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="3371f-133">Funkce systému Windows XP a Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="3371f-133">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="3371f-134">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="3371f-134">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
