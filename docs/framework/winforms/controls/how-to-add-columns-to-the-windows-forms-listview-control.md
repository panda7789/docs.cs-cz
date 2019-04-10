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
ms.openlocfilehash: 5c87d43513f2125945145445c61f689cdd9d2aaf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345739"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView
V podrobném zobrazení <xref:System.Windows.Forms.ListView> ovládací prvek mohl zobrazit více sloupců pro každou položku seznamu. Sloupce, které slouží k zobrazení uživatelům několik typů informací o každou položku seznamu. Seznam souborů může například zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru. Informace o naplnění sloupce po jejich vytvoření najdete v tématu [jak: Zobrazení podřízených položek ve sloupcích pomocí Windows Forms ovládací prvek ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Chcete-li programově přidat sloupce  
  
1. Nastavit u tohoto prvku <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.  
  
2. Použití <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> způsob zobrazení seznamu <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- [ListView – ovládací prvek](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
