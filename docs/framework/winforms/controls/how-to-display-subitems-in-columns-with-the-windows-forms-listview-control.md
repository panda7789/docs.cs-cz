---
title: Zobrazit podpoložky ve sloupcích s ovládacím prvkem ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745543"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="53b20-102">Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="53b20-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="53b20-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ListView> může zobrazit další text nebo podpoložky pro každou položku v zobrazení podrobností.</span><span class="sxs-lookup"><span data-stu-id="53b20-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="53b20-104">První sloupec zobrazuje text položky, například číslo zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="53b20-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="53b20-105">Druhý, třetí a následující sloupce zobrazují první, druhou a následnou přidruženou podpoložku.</span><span class="sxs-lookup"><span data-stu-id="53b20-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="53b20-106">Přidání podpoložky do položky seznamu</span><span class="sxs-lookup"><span data-stu-id="53b20-106">To add subitems to a list item</span></span>  
  
1. <span data-ttu-id="53b20-107">Přidejte všechny požadované sloupce.</span><span class="sxs-lookup"><span data-stu-id="53b20-107">Add any columns needed.</span></span> <span data-ttu-id="53b20-108">Vzhledem k tomu, že se v prvním sloupci zobrazí vlastnost <xref:System.Windows.Forms.ListView.Text%2A> položky, budete potřebovat jeden sloupec, než kolik jich obsahuje.</span><span class="sxs-lookup"><span data-stu-id="53b20-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="53b20-109">Další informace o přidávání sloupců najdete v tématu [Postup: Přidání sloupců do ovládacího prvku model Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="53b20-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2. <span data-ttu-id="53b20-110">Volejte metodu <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> kolekce, kterou vrátila vlastnost <xref:System.Windows.Forms.ListViewItem.SubItems%2A> položky.</span><span class="sxs-lookup"><span data-stu-id="53b20-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="53b20-111">Následující příklad kódu nastaví jméno zaměstnance a oddělení pro položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="53b20-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="53b20-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53b20-112">See also</span></span>

- [<span data-ttu-id="53b20-113">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="53b20-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="53b20-114">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="53b20-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="53b20-115">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="53b20-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="53b20-116">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="53b20-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="53b20-117">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="53b20-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
