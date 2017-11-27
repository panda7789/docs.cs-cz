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
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView
V zobrazení Podrobnosti o <xref:System.Windows.Forms.ListView> ovládací prvek může zobrazit více sloupců pro každou položku seznamu. Sloupce můžete zobrazit uživateli několik typů informací o jednotlivé položky seznamu. Seznam souborů, například může zobrazit, název souboru, typu souboru, velikost a datum poslední úpravy souboru. Informace o vyplnění sloupce po jejich vytvoření najdete v tématu [postupy: zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Chcete-li přidat sloupce prostřednictvím kódu programu  
  
1.  Nastavte ovládacího prvku <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.  
  
2.  Použití <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metoda zobrazení seznamu <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 [ListView – ovládací prvek](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
