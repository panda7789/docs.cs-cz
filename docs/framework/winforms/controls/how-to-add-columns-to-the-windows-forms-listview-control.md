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
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView
V zobrazení podrobností může ovládací prvek <xref:System.Windows.Forms.ListView> Zobrazit více sloupců pro každou položku seznamu. Můžete použít sloupce k zobrazení pro uživatele s několika typy informací o každé položce seznamu. Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru. Informace o naplnění sloupců po jejich vytvoření naleznete v tématu [How to: Display items in Columns with model Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Chcete-li přidat sloupce programově  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.ListView.View%2A> ovládacího prvku na hodnotu <xref:System.Windows.Forms.View.Details>.  
  
2. Použijte metodu <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> vlastnosti <xref:System.Windows.Forms.ListView.Columns%2A> zobrazení seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
