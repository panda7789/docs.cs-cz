---
title: Přidat sloupce do ovládacího prvku ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: dd438ffbadddfc37ec9eb15e59a908bb58472a45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744580"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="5b40b-102">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="5b40b-102">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="5b40b-103">V zobrazení podrobností může ovládací prvek <xref:System.Windows.Forms.ListView> Zobrazit více sloupců pro každou položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="5b40b-103">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="5b40b-104">Můžete použít sloupce k zobrazení pro uživatele s několika typy informací o každé položce seznamu.</span><span class="sxs-lookup"><span data-stu-id="5b40b-104">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="5b40b-105">Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru.</span><span class="sxs-lookup"><span data-stu-id="5b40b-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="5b40b-106">Informace o naplnění sloupců po jejich vytvoření naleznete v tématu [How to: Display items in Columns with model Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5b40b-106">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="5b40b-107">Chcete-li přidat sloupce programově</span><span class="sxs-lookup"><span data-stu-id="5b40b-107">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="5b40b-108">Nastavte vlastnost <xref:System.Windows.Forms.ListView.View%2A> ovládacího prvku na hodnotu <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="5b40b-108">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="5b40b-109">Použijte metodu <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> vlastnosti <xref:System.Windows.Forms.ListView.Columns%2A> zobrazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="5b40b-109">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="5b40b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b40b-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="5b40b-111">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="5b40b-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="5b40b-112">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="5b40b-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
