---
title: Přidání a odebrání položek pomocí ovládacího prvku ListView
description: Přečtěte si, jak přidat a odebrat položku pomocí ovládacího prvku model Windows Forms ListView zadáním položky a přiřazením vlastností.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618087"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView
Proces přidání položky do <xref:System.Windows.Forms.ListView> ovládacího prvku model Windows Forms se skládá hlavně z určení položky a přiřazení vlastností k ní. Přidávání a odebírání položek seznamu lze provést kdykoli.  
  
### <a name="to-add-items-programmatically"></a>Chcete-li přidat položky programově  
  
1. Použijte <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Items%2A> Vlastnosti.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Programové odebrání položek  
  
1. Použijte <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> metodu nebo <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> <xref:System.Windows.Forms.ListView.Items%2A> Vlastnosti. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>Metoda odebere jednu položku. <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> Metoda odebere všechny položky ze seznamu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- [ListView – ovládací prvek](listview-control-windows-forms.md)
- [ListView – přehled ovládacího prvku](listview-control-overview-windows-forms.md)
