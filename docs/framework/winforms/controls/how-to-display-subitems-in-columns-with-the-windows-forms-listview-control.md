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
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ListView> může zobrazit další text nebo podpoložky pro každou položku v zobrazení podrobností. První sloupec zobrazuje text položky, například číslo zaměstnance. Druhý, třetí a následující sloupce zobrazují první, druhou a následnou přidruženou podpoložku.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Přidání podpoložky do položky seznamu  
  
1. Přidejte všechny požadované sloupce. Vzhledem k tomu, že se v prvním sloupci zobrazí vlastnost <xref:System.Windows.Forms.ListView.Text%2A> položky, budete potřebovat jeden sloupec, než kolik jich obsahuje. Další informace o přidávání sloupců najdete v tématu [Postup: Přidání sloupců do ovládacího prvku model Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2. Volejte metodu <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> kolekce, kterou vrátila vlastnost <xref:System.Windows.Forms.ListViewItem.SubItems%2A> položky. Následující příklad kódu nastaví jméno zaměstnance a oddělení pro položku seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
