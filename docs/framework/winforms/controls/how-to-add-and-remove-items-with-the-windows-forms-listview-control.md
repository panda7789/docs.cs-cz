---
title: 'Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: 8a97d73b9b2c46d02ae0794ad66b20a04db58af6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011122"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView
Proces přidání položky do formulářů Windows <xref:System.Windows.Forms.ListView> ovládací prvek sestává především z zadáním položky a přiřazení vlastnosti k němu. Přidávání a odebírání položek seznamu lze provést kdykoli.  
  
### <a name="to-add-items-programmatically"></a>Chcete-li programově přidat položky  
  
1. Použití <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>K odebrání položek prostřednictvím kódu programu  
  
1. Použití <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> metodu <xref:System.Windows.Forms.ListView.Items%2A> vlastnost. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> Metoda odebere jednu položku; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> metoda odebere všechny položky ze seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
