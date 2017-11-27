---
title: "Postupy: Přidávání a odebírání položek s ovládacím prvkem Windows Forms ListView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1fe301f4c504d43fd83eb52e3b32f78af2ca78a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="7a30d-102">Postupy: Přidávání a odebírání položek s ovládacím prvkem Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7a30d-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="7a30d-103">Postup přidání položky do Windows Forms <xref:System.Windows.Forms.ListView> řízení se primárně skládá z zadáním položky a přiřazení vlastnosti k němu.</span><span class="sxs-lookup"><span data-stu-id="7a30d-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="7a30d-104">Přidávání a odebírání položek seznamu lze provést kdykoli.</span><span class="sxs-lookup"><span data-stu-id="7a30d-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="7a30d-105">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7a30d-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="7a30d-106">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7a30d-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a30d-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7a30d-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7a30d-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7a30d-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7a30d-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7a30d-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="7a30d-110">Přidat nebo odebrat položkami pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="7a30d-110">To add or remove items using the designer</span></span>  
  
1.  <span data-ttu-id="7a30d-111">Vyberte <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7a30d-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="7a30d-112">V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7a30d-112">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="7a30d-113">**Editor kolekce ListViewItem** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="7a30d-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="7a30d-114">Chcete-li přidat položku, klikněte na tlačítko **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7a30d-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="7a30d-115">Pak můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListView.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7a30d-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4.  <span data-ttu-id="7a30d-116">Chcete-li odebrat položku, vyberte ho a klikněte na tlačítko **odebrat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7a30d-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a30d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a30d-117">See Also</span></span>  
 [<span data-ttu-id="7a30d-118">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="7a30d-118">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="7a30d-119">Postupy: přidávání sloupců do ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7a30d-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="7a30d-120">Postupy: zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7a30d-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="7a30d-121">Postupy: zobrazení ikon pro Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7a30d-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="7a30d-122">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7a30d-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="7a30d-123">Postupy: seskupení položek v systému Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7a30d-123">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
