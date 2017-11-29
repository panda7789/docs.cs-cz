---
title: "Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cadf31d45f8650336c6ac6257a84655a978a9035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí Návrháře
Dlaždice zobrazení funkce <xref:System.Windows.Forms.ListView> řízení umožňuje zadat visual rovnováhu mezi grafické a textové informace. Textové informace zobrazené položky v dlaždici zobrazení je stejný jako informace o sloupci definována pro zobrazení podrobností. Označit funkcí v dlaždici zobrazit funkce v kombinaci s seskupení nebo vložení <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
 Zobrazení tile používá ikonou 32 x 32 a několik řádků textu, jak je znázorněno na následujícím obrázku.  
  
 ![Dlaždicové zobrazení v ovládacím prvku ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 Dlaždice zobrazení, vlastnosti a metody umožňují určit, která pole sloupce k zobrazení pro každou položku a souhrnně řídí velikost a vzhled všechny položky v rámci časového období zobrazení dlaždice. Pro přehlednost první řádek textu v dlaždici je vždy název položky; nelze změnit.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Je k dispozici pouze v dlaždici zobrazení [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda. V dřívějších operačních systémech, všechny kód týkající se zobrazení tile nemá žádný vliv a <xref:System.Windows.Forms.ListView> zobrazí v zobrazení velkých ikon. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Chcete-li nastavit zobrazení tile v Návrháři  
  
1.  Vyberte <xref:System.Windows.Forms.ListView> ovládací prvek na formuláři.  
  
2.  V **vlastnosti** vyberte <xref:System.Windows.Forms.ListView.View%2A> vlastnost a zvolte **dlaždice**.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Funkce systému Windows XP a Windows Forms – ovládací prvky](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
