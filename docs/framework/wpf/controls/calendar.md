---
title: Kalendář
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: 9a64c6cd6fc1cc53383f2617f7a7a78959e87c4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124784"
---
# <a name="calendar"></a>Kalendář
Kalendář umožňuje uživateli vybrat datum pomocí vizuálního zobrazení kalendáře.  
  
 A <xref:System.Windows.Controls.Calendar> ovládací prvek můžete použít samostatně nebo jako součást rozevíracího seznamu <xref:System.Windows.Controls.DatePicker> ovládacího prvku. Další informace naleznete v tématu <xref:System.Windows.Controls.DatePicker>.  
  
 Následující obrázek ukazuje dva <xref:System.Windows.Controls.Calendar> ovládací prvky s výběry a přerušení spojení data a jedna bez ní.  
  
 ![Ovládací prvky v kalendáři](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Ovládací prvky kalendáře  
  
 Následující tabulka obsahuje informace o úlohách, které jsou obvykle přidruženy k <xref:System.Windows.Controls.Calendar>.  
  
|Úloha|Implementace|  
|----------|--------------------|  
|Zadejte data, která nelze vybrat.|Použití <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> vlastnost.|  
|Máte <xref:System.Windows.Controls.Calendar> zobrazení za měsíc, celý rok nebo deset let.|Nastavte <xref:System.Windows.Controls.Calendar.DisplayMode%2A> vlastnost na měsíc, rok nebo deset let.|  
|Zadejte, jestli může uživatel vybrat datum, rozsah kalendářních dat nebo více rozsahy kalendářních dat.|Použití <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Zadejte rozsah dat, která <xref:System.Windows.Controls.Calendar> zobrazí.|Použití <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> a <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> vlastnosti.|  
|Určete, jestli aktuální datum je zvýrazněn.|Použití <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> vlastnost. Ve výchozím nastavení <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> je `true`.|  
|Změnit velikost <xref:System.Windows.Controls.Calendar>.|Použití <xref:System.Windows.Controls.Viewbox> nebo nastavit <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost <xref:System.Windows.Media.ScaleTransform>. Poznámka: Pokud nastavíte <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti <xref:System.Windows.Controls.Calendar>, skutečné kalendáře nedojde ke změně jeho velikosti.|  
  
 <xref:System.Windows.Controls.Calendar> Řízení poskytuje základní navigaci pomocí klávesnice nebo myši. Následující tabulka shrnuje navigaci pomocí klávesnice.  
  
|Kombinace kláves|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Akce|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Month>|Změny <xref:System.Windows.Controls.Calendar.SelectedDate%2A> vlastnost Pokud <xref:System.Windows.Controls.Calendar.SelectionMode%2A> vlastnost není nastavena na <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Year>|Změní z měsíce <xref:System.Windows.Controls.Calendar.DisplayDate%2A> vlastnost. Všimněte si, <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nezmění.|  
|ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Decade>|Rok se změní <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Všimněte si, <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nezmění.|  
|SHIFT + ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Month>|Pokud <xref:System.Windows.Controls.Calendar.SelectionMode%2A> není nastavená na <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> nebo <xref:System.Windows.Controls.CalendarSelectionMode.None>, rozšiřuje škálu vybraná data.|  
|DOMOVSKÁ STRÁNKA|<xref:System.Windows.Controls.CalendarMode.Month>|Změny <xref:System.Windows.Controls.Calendar.SelectedDate%2A> k prvnímu dni aktuálního měsíce.|  
|DOMOVSKÁ STRÁNKA|<xref:System.Windows.Controls.CalendarMode.Year>|Změní z měsíce <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na první měsíc v roce. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nezmění.|  
|DOMOVSKÁ STRÁNKA|<xref:System.Windows.Controls.CalendarMode.Decade>|Rok se změní <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na první rok deset let. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nezmění.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Změny <xref:System.Windows.Controls.Calendar.SelectedDate%2A> na poslední den v aktuálním měsíci.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Změní z měsíce <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na poslední měsíc v roce. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nezmění.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Rok se změní <xref:System.Windows.Controls.Calendar.DisplayDate%2A> s tím loňským desetiletí. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nezmění.|  
|CTRL + ŠIPKA NAHORU|Jakýkoli|Přepne na další větší <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Pokud <xref:System.Windows.Controls.Calendar.DisplayMode%2A> již <xref:System.Windows.Controls.CalendarMode.Decade>, žádná akce.|  
|CTRL + ŠIPKA DOLŮ|Jakýkoli|Přepne na další menší <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Pokud <xref:System.Windows.Controls.Calendar.DisplayMode%2A> již <xref:System.Windows.Controls.CalendarMode.Month>, žádná akce.|  
|MEZERNÍK nebo ENTER|<xref:System.Windows.Controls.CalendarMode.Year> or <xref:System.Windows.Controls.CalendarMode.Decade>|Přepínače <xref:System.Windows.Controls.Calendar.DisplayMode%2A> k <xref:System.Windows.Controls.CalendarMode.Month> nebo <xref:System.Windows.Controls.CalendarMode.Year> reprezentována cílených položky.|  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky](index.md)
- [Styly a šablony](styling-and-templating.md)
