---
title: 'Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: 07f6a7e06c5b1e91597ab6b6d816407a2c172278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater (Visual Studio)
Položka hlavičky v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení poskytuje vizuální indikátor při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> je vybrána. Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (výchozí), hlavička se zobrazí vlevo od jednotlivých položek. Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, hlavička se zobrazí v horní části každé položky.  
  
 První vybranou, hlavička se zobrazí v barvu, která je zadána <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> se zobrazí vlastnosti a ikona bílé šipky.  
  
> [!NOTE]
>  Pokud nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru nezobrazí první vybranou položku.  
  
 Když pole v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> má právě fokus, barva změny položky hlavičky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> barvy a změny ikonu šipky černé na pozadí. Pokud dojde ke změně dat, se zobrazí symbol tužky v hlavičce položky.  
  
 Výchozí šířku (nebo výšky při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) položky hlavičky je 15 pixelů. Můžete změnit šířku nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastnost.  
  
> [!NOTE]
>  Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, symbol indikátoru v hlavičce položky se nezobrazí.  
  
 Záhlaví položek můžete skrýt, a to nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> vlastnost **False**. Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> je nastaven na **False**, jediné, že je vybrána položka je tečkovaná čára po obvodu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Můžete také zadat vlastní indikátor výběru sledováním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> vlastnost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> události <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Změna vzhledu položky záhlaví  
  
1.  V Návrháři formulářů Windows, vyberte menší oblast <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Je třeba vybrat nižší oblast ovládacího prvku. Pokud vyberete oddíl šablony položky, zobrazí se v okně vlastností jinou sadu vlastností.  
  
2.  V okně Vlastnosti použít <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> vlastnosti chcete změnit barvu položky záhlaví.  
  
    > [!NOTE]
    >  Pokud nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru nezobrazí první vybranou položku.  
  
3.  Použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastnost změnit šířku (nebo výška) položek záhlaví.  
  
    > [!NOTE]
    >  Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, symbol indikátoru v hlavičce položky se nezobrazí.  
  
### <a name="to-hide-item-headers"></a>Skrytí položek záhlaví  
  
1.  V Návrháři formulářů Windows, vyberte menší oblast <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Je třeba vybrat nižší oblast ovládacího prvku. Pokud vyberete oddíl šablony položky, zobrazí se v okně vlastností jinou sadu vlastností.  
  
2.  V okně vlastnosti nastavit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> vlastnost **False**.  
  
     Když je položka v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je vybrána, bude jediné tečkovaná čára po obvodu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Postupy: Změna rozložení ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
