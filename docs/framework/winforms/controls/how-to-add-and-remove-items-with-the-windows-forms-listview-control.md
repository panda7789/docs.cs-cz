---
title: Přidání a odebrání položek pomocí ovládacího prvku ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: bbfe99db857ebe3a80bf99926f3ce0bec38a1f3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743135"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView
Proces přidání položky do ovládacího prvku model Windows Forms <xref:System.Windows.Forms.ListView> se skládá hlavně z určení položky a přiřazení vlastností. Přidávání a odebírání položek seznamu lze provést kdykoli.  
  
### <a name="to-add-items-programmatically"></a>Chcete-li přidat položky programově  
  
1. Použijte metodu <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> vlastnosti <xref:System.Windows.Forms.ListView.Items%2A>.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Programové odebrání položek  
  
1. Pro vlastnost <xref:System.Windows.Forms.ListView.Items%2A> použijte metodu <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A>. Metoda <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> odstraní jednu položku; Metoda <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> odebere všechny položky ze seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
