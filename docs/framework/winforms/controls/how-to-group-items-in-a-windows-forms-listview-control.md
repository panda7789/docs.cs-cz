---
title: 'Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView'
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
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966631"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView
Pomocí funkce <xref:System.Windows.Forms.ListView> seskupení ovládacího prvku můžete zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce vodorovnými záhlavími skupin, která obsahují názvy skupin. Skupiny můžete použít <xref:System.Windows.Forms.ListView> k jednoduššímu procházení rozsáhlých seznamů tím, že položky seskupíte podle abecedy, podle data nebo do jiného logického seskupení. Následující obrázek znázorňuje některé seskupené položky.  
  
 ![Snímek obrazovky s lichými a sudými skupinami ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Chcete-li povolit seskupování, je nutné nejprve vytvořit jednu nebo více skupin buď v návrháři, nebo programově. Po definování skupiny můžete přiřadit <xref:System.Windows.Forms.ListView> položky do skupin. Položky můžete také přesunout z jedné skupiny do jiné programově.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ListView>skupiny jsou k dispozici [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] pouze v případě, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> že vaše aplikace volá metodu. Ve starších operačních systémech žádný kód týkající se skupin nemá žádný vliv a skupiny se nezobrazí. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Přidání skupin  
  
1. <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> Použijte metodu<xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Odebrání skupin  
  
1. <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> Použijte metodu <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> nebo<xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     Metoda odstraní jednu skupinu <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> . metoda odebere ze seznamu všechny skupiny. <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>  
  
    > [!NOTE]
    > Odebráním skupiny nedojde k odebrání položek v této skupině.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Přiřazení položek do skupin nebo přesouvání položek mezi skupinami  
  
1. <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> Nastavte vlastnost jednotlivých položek.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidávání a odebírání položek pomocí ovládacího prvku model Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
