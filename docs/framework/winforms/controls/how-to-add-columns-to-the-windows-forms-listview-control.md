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
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView
V zobrazení podrobností <xref:System.Windows.Forms.ListView> může ovládací prvek zobrazit více sloupců pro každou položku seznamu. Můžete použít sloupce k zobrazení pro uživatele s několika typy informací o každé položce seznamu. Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru. Informace o naplnění sloupců po jejich vytvoření naleznete v tématu [How to: Display items in Columns with model Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Chcete-li přidat sloupce programově  
  
1. Nastavte vlastnost ovládacího prvku <xref:System.Windows.Forms.ListView.View%2A> na <xref:System.Windows.Forms.View.Details> .  
  
2. Použijte <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metodu vlastnosti zobrazení seznamu <xref:System.Windows.Forms.ListView.Columns%2A> .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListView>
- [ListView – ovládací prvek](listview-control-windows-forms.md)
- [ListView – přehled ovládacího prvku](listview-control-overview-windows-forms.md)
