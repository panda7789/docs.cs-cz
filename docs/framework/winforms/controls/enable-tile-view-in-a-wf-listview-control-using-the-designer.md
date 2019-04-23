---
title: 'Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: f8c8a1b2e3d2adfa7daadd609051ffc304150efe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300590"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView pomocí Návrháře
Funkci zobrazení dlaždice <xref:System.Windows.Forms.ListView> ovládací prvek můžete zadat vizuální rovnováhu mezi textové a grafické informace. Textové informace zobrazené položky v zobrazení tile je stejný jako sloupec informace definované pro zobrazení podrobností. Dlaždice zobrazit funkce v kombinaci s seskupení nebo vložení označit funkce <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
 Zobrazení tile používá ikony 32 x 32 a několik řádků textu, jak je znázorněno na následujícím obrázku.  
  
 ![Dlaždice zobrazení v ovládacím prvku ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "dlaždici zobrazení ikon a textu")  
  
 Zobrazení, vlastnosti a metody umožňují určit sloupce pole k zobrazení pro každou položku a souhrnně řídit velikost a vzhled všech položek v dlaždici zobrazení okna vedle sebe. Pro přehlednost první řádek textu v bloku je vždy název položky. nelze změnit.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Je k dispozici pouze v zobrazení tile [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. Ve starších operačních systémech, jakýkoli kód související s zobrazení tile nemá žádný účinek a <xref:System.Windows.Forms.ListView> ovládací prvek zobrazí v zobrazení LargeIcon. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Chcete-li nastavit zobrazení tile v Návrháři  
  
1. Vyberte <xref:System.Windows.Forms.ListView> ovládací prvek na formuláři.  
  
2. V **vlastnosti** okna, vyberte <xref:System.Windows.Forms.ListView.View%2A> vlastnosti a zvolte **dlaždice**.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
