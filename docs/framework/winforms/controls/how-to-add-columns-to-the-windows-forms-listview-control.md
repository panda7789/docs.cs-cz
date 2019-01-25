---
title: 'Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: eed032ec0bacd50666c30979b33362dabf00d565
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700192"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="05954-102">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="05954-102">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="05954-103">V podrobném zobrazení <xref:System.Windows.Forms.ListView> ovládací prvek mohl zobrazit více sloupců pro každou položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="05954-103">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="05954-104">Sloupce, které slouží k zobrazení uživatelům několik typů informací o každou položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="05954-104">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="05954-105">Seznam souborů může například zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru.</span><span class="sxs-lookup"><span data-stu-id="05954-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="05954-106">Informace o naplnění sloupce po jejich vytvoření najdete v tématu [jak: Zobrazení podřízených položek ve sloupcích pomocí Windows Forms ovládací prvek ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="05954-106">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="05954-107">Chcete-li programově přidat sloupce</span><span class="sxs-lookup"><span data-stu-id="05954-107">To add columns programmatically</span></span>  
  
1.  <span data-ttu-id="05954-108">Nastavit u tohoto prvku <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="05954-108">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="05954-109">Použití <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> způsob zobrazení seznamu <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="05954-109">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="05954-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05954-110">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="05954-111">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="05954-111">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="05954-112">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="05954-112">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
