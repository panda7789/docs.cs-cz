---
title: "Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c22134513c2c6a3ff2bc621e68f546b7bcc93ba9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView
Funkce k seskupení <xref:System.Windows.Forms.ListView> ovládací prvek, můžete zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce podle hlaviček vodorovné skupiny, které obsahují názvy skupiny. Můžete použít <xref:System.Windows.Forms.ListView> skupiny, aby bylo navigace velké seznamy jednodušší podle abecedy, seskupení položek podle data, nebo pomocí jiné logické seskupení. Následující obrázek ukazuje některé seskupené položky.  
  
 ![ListView skupiny](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
ListView seskupeny položky  
  
 Pokud chcete povolit seskupování, musíte nejdřív vytvořit jeden nebo více skupin v Návrháři nebo prostřednictvím kódu programu. Po definování skupiny, můžete přiřadit <xref:System.Windows.Forms.ListView> položky do skupiny. Také můžete přesunout položky z jedné skupiny do jiné prostřednictvím kódu programu.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView>skupiny jsou k dispozici pouze na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda. V dřívějších operačních systémech žádný kód týkající se skupiny nemá žádný vliv a skupin nebude zobrazovat. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Přidání skupin  
  
1.  Použití <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Chcete-li odebrat skupiny  
  
1.  Použití <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> nebo <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metodu <xref:System.Windows.Forms.ListView.Groups%2A> kolekce.  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Metoda odebere jednu skupinu; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda odebere všechny skupiny ze seznamu.  
  
    > [!NOTE]
    >  Odebrání skupiny neodebere položky v rámci dané skupiny.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>K přiřazení položky do skupin nebo položky přesouvat mezi skupinami.  
  
1.  Nastavte <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> vlastnost jednotlivých položek.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [ListView – ovládací prvek](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Funkce systému Windows XP a Windows Forms – ovládací prvky](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
