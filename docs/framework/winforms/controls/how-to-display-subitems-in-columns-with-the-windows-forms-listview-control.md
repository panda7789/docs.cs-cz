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
ms.openlocfilehash: defa8aa736927c9076eb2410d6d914a8f7550d03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183713"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek mohl zobrazit další text nebo podřízené položky pro každou položku v zobrazení Details. První sloupec zobrazuje text položky, například číslo zaměstnance. Druhá s názvem třetí a následující sloupce obsahují první, druhý a další související podřízené položky.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Chcete-li přidat podřízené položky pro položku seznamu  
  
1.  Přidáte všechny sloupce potřeba. Protože první sloupec se zobrazí položky <xref:System.Windows.Forms.ListView.Text%2A> vlastnost, budete potřebovat jeden další sloupec, než je podřízené položky. Další informace o přidání sloupce, naleznete v tématu [jak: Přidání sloupce, které chcete Windows Forms ovládací prvek ListView](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Volání <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metoda kolekci vrácené poskytovatelem <xref:System.Windows.Forms.ListViewItem.SubItems%2A> vlastnosti položky. Následující příklad kódu nastaví jméno zaměstnance a oddělení pro položku seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
