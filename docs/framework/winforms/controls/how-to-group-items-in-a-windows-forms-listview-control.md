---
title: Seskupení položek v ovládacím prvku ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 45846751780f433c29b186fe8b9a908f5d295ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736627"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView
Pomocí funkce seskupení ovládacího prvku <xref:System.Windows.Forms.ListView> můžete zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce vodorovnými záhlavími skupin, která obsahují názvy skupin. Skupiny <xref:System.Windows.Forms.ListView> můžete použít k jednoduššímu procházení rozsáhlých seznamů tím, že položky seskupíte podle abecedy, podle data nebo do jiného logického seskupení. Následující obrázek znázorňuje některé seskupené položky.  
  
 ![Snímek obrazovky s lichými a sudými skupinami ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Chcete-li povolit seskupování, je nutné nejprve vytvořit jednu nebo více skupin buď v návrháři, nebo programově. Po definování skupiny můžete přiřadit <xref:System.Windows.Forms.ListView> položky do skupin. Položky můžete také přesunout z jedné skupiny do jiné programově.  
  
### <a name="to-add-groups"></a>Přidání skupin  
  
1. Použijte metodu <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> kolekce <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Odebrání skupin  
  
1. Použijte metodu <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> kolekce <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     Metoda <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> odstraní jednu skupinu. Metoda <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> odebere ze seznamu všechny skupiny.  
  
    > [!NOTE]
    > Odebráním skupiny nedojde k odebrání položek v této skupině.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Přiřazení položek do skupin nebo přesouvání položek mezi skupinami  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> jednotlivých položek.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
