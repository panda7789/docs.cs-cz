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
ms.openlocfilehash: bd41dda048aadc399c7f8ffe0926b010991d08a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686748"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek mohl zobrazit další text nebo podřízené položky pro každou položku v zobrazení Details. První sloupec zobrazuje text položky, například číslo zaměstnance. Druhá s názvem třetí a následující sloupce obsahují první, druhý a další související podřízené položky.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Chcete-li přidat podřízené položky pro položku seznamu  
  
1.  Přidáte všechny sloupce potřeba. Protože první sloupec se zobrazí položky <xref:System.Windows.Forms.ListView.Text%2A> vlastnost, budete potřebovat jeden další sloupec, než je podřízené položky. Další informace o přidání sloupce, naleznete v tématu [jak: Přidání sloupce, které chcete Windows Forms ovládací prvek ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Volání <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metoda kolekci vrácené poskytovatelem <xref:System.Windows.Forms.ListViewItem.SubItems%2A> vlastnosti položky. Následující příklad kódu nastaví jméno zaměstnance a oddělení pro položku seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
