---
title: 'Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: c532cadc5b42c26f1598c4e7586309cf690456bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView pomocí Návrháře
Funkci seskupení <xref:System.Windows.Forms.ListView> řízení umožňuje zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce podle hlaviček vodorovné skupiny, které obsahují názvy skupiny. Můžete použít <xref:System.Windows.Forms.ListView> skupiny, aby bylo navigace velké seznamy jednodušší podle abecedy, seskupení položek podle data, nebo pomocí jiné logické seskupení. Následující obrázek ukazuje některé seskupené položky.  
  
 ![ListView skupiny](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Pokud chcete povolit seskupování, musíte nejdřív vytvořit jeden nebo více <xref:System.Windows.Forms.ListViewGroup> objektů v Návrháři nebo prostřednictvím kódu programu. Po definování skupiny, můžete přiřadit položky k němu.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> skupiny jsou k dispozici pouze na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda. V dřívějších operačních systémech žádný kód týkající se skupiny nemá žádný vliv a skupin nebude zobrazovat. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Chcete-li přidat nebo odebrat skupiny v Návrháři  
  
1.  V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ListView.Groups%2A> vlastnost.  
  
     **Editor kolekce ListViewGroup** se zobrazí.  
  
2.  Chcete-li přidat skupinu, klikněte na tlačítko **přidat** tlačítko. Pak můžete nastavit vlastnosti nové skupiny, jako <xref:System.Windows.Forms.ListViewGroup.Header%2A> a <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> vlastnosti. Chcete-li odebrat skupinu, vyberte ho a klikněte na tlačítko **odebrat** tlačítko.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Přiřazení položky ke skupinám v Návrháři  
  
1.  V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.  
  
     **Editor kolekce ListViewItem** se zobrazí.  
  
2.  Chcete-li přidat novou položku, klikněte na tlačítko **přidat** tlačítko. Pak můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListViewItem.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.  
  
3.  Vyberte <xref:System.Windows.Forms.ListViewItem.Group%2A> vlastnosti a pak vyberte skupinu z rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Funkce systému Windows XP a Windows Forms – ovládací prvky](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
