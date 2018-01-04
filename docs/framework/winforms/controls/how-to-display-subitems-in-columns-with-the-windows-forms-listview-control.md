---
title: "Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView"
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
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a9da292b5f65ea9dc44b47a8c3bc13cf43e83b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="1660e-102">Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="1660e-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="1660e-103">Windows Forms <xref:System.Windows.Forms.ListView> řízení můžete zobrazit další text nebo pro každou položku v zobrazení Podrobnosti o podřízených položek.</span><span class="sxs-lookup"><span data-stu-id="1660e-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="1660e-104">První sloupec zobrazuje text položky, například číslo zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="1660e-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="1660e-105">Druhá s názvem sloupce třetí a následné zobrazení první, druhý a další související podřízených položek.</span><span class="sxs-lookup"><span data-stu-id="1660e-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="1660e-106">Chcete-li přidat položku seznamu podřízených položek</span><span class="sxs-lookup"><span data-stu-id="1660e-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="1660e-107">Přidáte všechny sloupce potřeby.</span><span class="sxs-lookup"><span data-stu-id="1660e-107">Add any columns needed.</span></span> <span data-ttu-id="1660e-108">Vzhledem k tomu, že první sloupec zobrazí položky <xref:System.Windows.Forms.ListView.Text%2A> vlastnost, je třeba jeden další sloupec, než je počet podřízených položek.</span><span class="sxs-lookup"><span data-stu-id="1660e-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="1660e-109">Další informace o přidání sloupců naleznete v tématu [postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1660e-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="1660e-110">Volání <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metoda kolekce vrácené <xref:System.Windows.Forms.ListViewItem.SubItems%2A> vlastnosti položky.</span><span class="sxs-lookup"><span data-stu-id="1660e-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="1660e-111">Následující příklad kódu nastaví název zaměstnanců a oddělení pro položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="1660e-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="1660e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1660e-112">See Also</span></span>  
 [<span data-ttu-id="1660e-113">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="1660e-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="1660e-114">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="1660e-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="1660e-115">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="1660e-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="1660e-116">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="1660e-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="1660e-117">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1660e-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
