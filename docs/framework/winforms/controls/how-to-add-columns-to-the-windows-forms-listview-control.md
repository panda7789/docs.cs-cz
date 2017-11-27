---
title: "Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView"
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
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8df87e62e8c19ee6e30ffdbc2a4e473b444f538
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="76205-102">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="76205-102">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="76205-103">V zobrazení Podrobnosti o <xref:System.Windows.Forms.ListView> ovládací prvek může zobrazit více sloupců pro každou položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="76205-103">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="76205-104">Sloupce můžete zobrazit uživateli několik typů informací o jednotlivé položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="76205-104">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="76205-105">Seznam souborů, například může zobrazit, název souboru, typu souboru, velikost a datum poslední úpravy souboru.</span><span class="sxs-lookup"><span data-stu-id="76205-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="76205-106">Informace o vyplnění sloupce po jejich vytvoření najdete v tématu [postupy: zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="76205-106">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="76205-107">Chcete-li přidat sloupce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="76205-107">To add columns programmatically</span></span>  
  
1.  <span data-ttu-id="76205-108">Nastavte ovládacího prvku <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="76205-108">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="76205-109">Použití <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metoda zobrazení seznamu <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76205-109">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="76205-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="76205-110">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 [<span data-ttu-id="76205-111">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="76205-111">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="76205-112">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="76205-112">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
