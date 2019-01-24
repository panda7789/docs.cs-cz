---
title: 'Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: eccac1b3b02da41a34d47072be267f6c51a7d490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504558"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater (Visual Studio)
Položky hlavičky v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení poskytuje vizuální indikátor při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> je vybrána. Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (výchozí), záhlaví položky se zobrazí nalevo od každé položky. Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, záhlaví položky se zobrazí v horní části každé položky.  
  
 Pokud je první vybranou, záhlaví položky se zobrazí v barvu, která je určená <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> vlastnost a ikona bílé šipky se zobrazí.  
  
> [!NOTE]
>  Pokud jste nastavili <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru se nezobrazí, je nejprve vybranou položku.  
  
 Pole v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> má fokus, barva položky záhlaví se změní <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> pozadí barvu a ikona šipka se změní na černou. Pokud se data změní, symbol tužky se zobrazí v záhlaví položky.  
  
 Výchozí šířka (nebo výška při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) položky záhlaví je 15 pixelů. Můžete změnit šířku nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastnost.  
  
> [!NOTE]
>  Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, nebude zobrazen indikátor symboly v hlavičce položky.  
  
 Záhlaví položek můžete skrýt nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> vlastnost **False**. Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> je nastavena na **False**, jediné, co zjistí, že je vybrána položka se tečkovaná čára kolem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Můžete také zadat vlastní indikátor výběru sledováním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> vlastnost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Změna vzhledu položky záhlaví  
  
1.  V Návrháři formulářů Windows vyberte menší oblast <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Musíte vybrat dolní oblasti ovládacího prvku. Pokud jste vybrali v části šablony položky, zobrazí se různé sady vlastností v okně Vlastnosti.  
  
2.  V okně vlastnosti použijte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> vlastnosti a změňte barvu záhlaví položek.  
  
    > [!NOTE]
    >  Pokud jste nastavili <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru se nezobrazí, je nejprve vybranou položku.  
  
3.  Použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastností můžete změnit šířku (nebo výška) záhlaví položek.  
  
    > [!NOTE]
    >  Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, nebude zobrazen indikátor symboly v hlavičce položky.  
  
### <a name="to-hide-item-headers"></a>Chcete-li skrýt záhlaví položek  
  
1.  V Návrháři formulářů Windows vyberte menší oblast <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Musíte vybrat dolní oblasti ovládacího prvku. Pokud jste vybrali v části šablony položky, zobrazí se různé sady vlastností v okně Vlastnosti.  
  
2.  V okně Vlastnosti nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> vlastnost **False**.  
  
     Pokud položka v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je vybrána, bude pouze označení tečkovaná čára kolem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Postupy: Změna rozložení ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
