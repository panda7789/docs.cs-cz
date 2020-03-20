---
title: Položky skupiny v ovládacím prvku ListView
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141988"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView
Pomocí funkce seskupení <xref:System.Windows.Forms.ListView> ovládacího prvku můžete zobrazit související sady položek ve skupinách. Tyto skupiny jsou na obrazovce odděleny vodorovnými záhlavími skupin, které obsahují názvy skupin. <xref:System.Windows.Forms.ListView> Pomocí skupin můžete usnadnit navigaci ve velkých seznamech seskupením položek abecedně, podle data nebo podle jiného logického seskupení. Následující obrázek znázorňuje některé seskupené položky.  
  
 ![Snímek obrazovky s lichými a sudými skupinami ListView](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 Chcete-li povolit seskupení, musíte nejprve vytvořit jednu nebo více skupin buď v návrháři nebo programově. Po definování skupiny můžete položky přiřadit <xref:System.Windows.Forms.ListView> ke skupinám. Položky můžete také programově přesunout z jedné skupiny do druhé.  
  
### <a name="to-add-groups"></a>Přidání skupin  
  
1. Použijte <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Odebrání skupin  
  
1. Použijte <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> nebo <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     Metoda <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> odebere jednu skupinu; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda odebere všechny skupiny ze seznamu.  
  
    > [!NOTE]
    > Odebráním skupiny neodeberete položky v této skupině.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Přiřazení položek skupinám nebo přesunutí položek mezi skupinami  
  
1. Nastavte <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> vlastnost jednotlivých položek.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView – ovládací prvek](listview-control-windows-forms.md)
- [ListView – přehled ovládacího prvku](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
