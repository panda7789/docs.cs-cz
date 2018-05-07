---
title: 'Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: 83ef2e108695988bbb0329d9f01e1317d9308f18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView
Postup přidání položky do Windows Forms <xref:System.Windows.Forms.ListView> řízení se primárně skládá z zadáním položky a přiřazení vlastnosti k němu. Přidávání a odebírání položek seznamu lze provést kdykoli.  
  
### <a name="to-add-items-programmatically"></a>Chcete-li přidat položky prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Odebrat položky prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> metodu <xref:System.Windows.Forms.ListView.Items%2A> vlastnost. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> Metoda odebere jednu položku; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> metoda odebere všechny položky ze seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
