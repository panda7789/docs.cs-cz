---
title: Přidání a odebrání položek pomocí ovládacího prvku ListView
description: Přečtěte si, jak přidat a odebrat položku pomocí ovládacího prvku model Windows Forms ListView zadáním položky a přiřazením vlastností.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618087"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="38331-103">Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="38331-103">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="38331-104">Proces přidání položky do <xref:System.Windows.Forms.ListView> ovládacího prvku model Windows Forms se skládá hlavně z určení položky a přiřazení vlastností k ní.</span><span class="sxs-lookup"><span data-stu-id="38331-104">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="38331-105">Přidávání a odebírání položek seznamu lze provést kdykoli.</span><span class="sxs-lookup"><span data-stu-id="38331-105">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="38331-106">Chcete-li přidat položky programově</span><span class="sxs-lookup"><span data-stu-id="38331-106">To add items programmatically</span></span>  
  
1. <span data-ttu-id="38331-107">Použijte <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Items%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="38331-107">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="38331-108">Programové odebrání položek</span><span class="sxs-lookup"><span data-stu-id="38331-108">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="38331-109">Použijte <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> metodu nebo <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> <xref:System.Windows.Forms.ListView.Items%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="38331-109">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="38331-110"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>Metoda odebere jednu položku. <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> Metoda odebere všechny položky ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="38331-110">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="38331-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38331-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="38331-112">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="38331-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="38331-113">ListView – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="38331-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
