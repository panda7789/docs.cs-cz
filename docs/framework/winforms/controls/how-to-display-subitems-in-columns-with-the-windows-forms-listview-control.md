---
title: 'Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView'
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
ms.openlocfilehash: efee926301bc358bb7645ba67826f412c0d0dbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView
Windows Forms <xref:System.Windows.Forms.ListView> řízení můžete zobrazit další text nebo pro každou položku v zobrazení Podrobnosti o podřízených položek. První sloupec zobrazuje text položky, například číslo zaměstnance. Druhá s názvem sloupce třetí a následné zobrazení první, druhý a další související podřízených položek.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Chcete-li přidat položku seznamu podřízených položek  
  
1.  Přidáte všechny sloupce potřeby. Vzhledem k tomu, že první sloupec zobrazí položky <xref:System.Windows.Forms.ListView.Text%2A> vlastnost, je třeba jeden další sloupec, než je počet podřízených položek. Další informace o přidání sloupců naleznete v tématu [postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Volání <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metoda kolekce vrácené <xref:System.Windows.Forms.ListViewItem.SubItems%2A> vlastnosti položky. Následující příklad kódu nastaví název zaměstnanců a oddělení pro položku seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
