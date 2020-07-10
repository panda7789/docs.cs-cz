---
title: Přidat sloupce do ovládacího prvku ListView
description: Naučte se, jak přidat sloupce do ovládacího prvku model Windows Forms ListView pro zobrazení několika typů informací o každé položce seznamu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174559"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="65bf5-103">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="65bf5-103">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="65bf5-104">V zobrazení podrobností <xref:System.Windows.Forms.ListView> může ovládací prvek zobrazit více sloupců pro každou položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="65bf5-104">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="65bf5-105">Můžete použít sloupce k zobrazení pro uživatele s několika typy informací o každé položce seznamu.</span><span class="sxs-lookup"><span data-stu-id="65bf5-105">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="65bf5-106">Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru.</span><span class="sxs-lookup"><span data-stu-id="65bf5-106">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="65bf5-107">Informace o naplnění sloupců po jejich vytvoření naleznete v tématu [How to: Display items in Columns with model Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="65bf5-107">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="65bf5-108">Chcete-li přidat sloupce programově</span><span class="sxs-lookup"><span data-stu-id="65bf5-108">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="65bf5-109">Nastavte vlastnost ovládacího prvku <xref:System.Windows.Forms.ListView.View%2A> na <xref:System.Windows.Forms.View.Details> .</span><span class="sxs-lookup"><span data-stu-id="65bf5-109">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="65bf5-110">Použijte <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metodu vlastnosti zobrazení seznamu <xref:System.Windows.Forms.ListView.Columns%2A> .</span><span class="sxs-lookup"><span data-stu-id="65bf5-110">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="65bf5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="65bf5-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="65bf5-112">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="65bf5-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="65bf5-113">ListView – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="65bf5-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
