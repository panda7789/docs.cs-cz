---
title: 'Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: aaf4b244a15ef982d0a58852a7f408796b2b4474
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882412"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView pomocí Návrháře

Funkci seskupování <xref:System.Windows.Forms.ListView> řízení umožňuje zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce záhlaví vodorovné skupin, které obsahují názvů skupin. Můžete použít <xref:System.Windows.Forms.ListView> skupiny, aby měli procházení rozsáhlých seznamů jednodušší seskupováním položek podle abecedy, datum, nebo jiné logické seskupení. Následující obrázek ukazuje některé seskupených položek:
  
 ![Čísla rozdělit do skupin liché a dokonce i.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
 Pokud chcete povolit seskupování, je nutné nejprve vytvořit jeden nebo více <xref:System.Windows.Forms.ListViewGroup> objektů v Návrháři nebo prostřednictvím kódu programu. Po definování skupinu můžete přiřadit položky k němu.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> jsou k dispozici pouze na skupiny [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. Ve starších operačních systémech jakýkoli kód týkajících se skupin nemá žádný vliv a skupin nebude zobrazovat. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Chcete-li přidat nebo odebrat skupiny v Návrháři  
  
1.  V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle <xref:System.Windows.Forms.ListView.Groups%2A> vlastnost .  
  
     **Editor kolekce ListViewGroup** se zobrazí.  
  
2. Chcete-li přidat skupinu, klikněte na tlačítko **přidat** tlačítko. Potom můžete nastavit vlastnosti nové skupiny, jako <xref:System.Windows.Forms.ListViewGroup.Header%2A> a <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> vlastnosti. Můžete odebrat skupinu, vyberte ho a klikněte **odebrat** tlačítko.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Přiřazení položek do skupin v Návrháři  
  
1.  V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle <xref:System.Windows.Forms.ListView.Items%2A> vlastnost .  
  
     **Editor kolekce ListViewItem** se zobrazí.  
  
2. Chcete-li přidat novou položku, klikněte na tlačítko **přidat** tlačítko. Potom můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListViewItem.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.  
  
3. Vyberte <xref:System.Windows.Forms.ListViewItem.Group%2A> vlastnosti a zvolte skupinu z rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
