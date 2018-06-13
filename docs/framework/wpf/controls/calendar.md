---
title: Kalendář
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: b706ec6236b7e3e10865eee9fd32c2eb5a5e7db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557703"
---
# <a name="calendar"></a>Kalendář
Kalendář umožňuje uživateli vybrat datum pomocí zobrazení visual kalendáře.  
  
 A <xref:System.Windows.Controls.Calendar> řízení lze použít samostatně nebo jako součást rozevíracího seznamu <xref:System.Windows.Controls.DatePicker> ovládacího prvku. Další informace naleznete v tématu <xref:System.Windows.Controls.DatePicker>.  
  
 Následující obrázek ukazuje dva <xref:System.Windows.Controls.Calendar> ovládací prvky a s výběry a přerušení spojení data bez.  
  
 ![Ovládací prvky kalendáře](../../../../docs/framework/wpf/controls/media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Ovládací prvky kalendáře  
  
 Následující tabulka obsahuje informace o úlohách, které jsou obvykle přidruženy <xref:System.Windows.Controls.Calendar>.  
  
|Úloha|Implementace|  
|----------|--------------------|  
|Zadat data, není k dispozici.|Použití <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> vlastnost.|  
|Máte <xref:System.Windows.Controls.Calendar> zobrazení měsíce, celý rok nebo deset.|Nastavte <xref:System.Windows.Controls.Calendar.DisplayMode%2A> vlastnost na měsíc, rok nebo desetiletí.|  
|Zadejte, jestli může uživatel vybrat datum, rozsah kalendářních dat nebo víc rozsahů kalendářních dat.|Použití <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Zadejte rozsah dat, který <xref:System.Windows.Controls.Calendar> zobrazí.|Použití <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> a <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> vlastnosti.|  
|Zadejte, zda je označený aktuální datum.|Použití <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> vlastnost. Ve výchozím nastavení <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> je `true`.|  
|Změna velikosti <xref:System.Windows.Controls.Calendar>.|Použití <xref:System.Windows.Controls.Viewbox> nebo nastavte <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnosti <xref:System.Windows.Media.ScaleTransform>. Všimněte si, že pokud nastavíte <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti <xref:System.Windows.Controls.Calendar>, skutečný kalendáře nezmění jeho velikost.|  
  
 <xref:System.Windows.Controls.Calendar> Řízení poskytuje základní navigaci pomocí myši nebo klávesnice. Následující tabulka shrnuje klávesnice navigace.  
  
|Kombinace klíče|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Akce|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Month>|Změny <xref:System.Windows.Controls.Calendar.SelectedDate%2A> vlastnost Pokud <xref:System.Windows.Controls.Calendar.SelectionMode%2A> vlastnost není nastavena na <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Year>|Změní měsíc <xref:System.Windows.Controls.Calendar.DisplayDate%2A> vlastnost. Všimněte si, že <xref:System.Windows.Controls.Calendar.SelectedDate%2A> se nemění.|  
|ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Decade>|Rok se změní <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Všimněte si, že <xref:System.Windows.Controls.Calendar.SelectedDate%2A> se nemění.|  
|SHIFT + ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Month>|Pokud <xref:System.Windows.Controls.Calendar.SelectionMode%2A> není nastavený na <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> nebo <xref:System.Windows.Controls.CalendarSelectionMode.None>, rozšiřuje rozsah dat, vybrané.|  
|DOMOVSKÉ|<xref:System.Windows.Controls.CalendarMode.Month>|Změny <xref:System.Windows.Controls.Calendar.SelectedDate%2A> na první den aktuálního měsíce.|  
|DOMOVSKÉ|<xref:System.Windows.Controls.CalendarMode.Year>|Změní měsíc <xref:System.Windows.Controls.Calendar.DisplayDate%2A> první měsíc v roce. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Se nemění.|  
|DOMOVSKÉ|<xref:System.Windows.Controls.CalendarMode.Decade>|Rok se změní <xref:System.Windows.Controls.Calendar.DisplayDate%2A> k prvnímu roku desetiletí. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Se nemění.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Změny <xref:System.Windows.Controls.Calendar.SelectedDate%2A> na poslední den aktuálního měsíce.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Změní měsíc <xref:System.Windows.Controls.Calendar.DisplayDate%2A> poslední měsíc v roce. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Se nemění.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Rok se změní <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na poslední rok desetiletí. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Se nemění.|  
|CTRL + ŠIPKA NAHORU|všechny|Přepne do dalšího větší <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Pokud <xref:System.Windows.Controls.Calendar.DisplayMode%2A> je již <xref:System.Windows.Controls.CalendarMode.Decade>, žádná akce.|  
|CTRL + ŠIPKA DOLŮ|všechny|Přepne do dalšího menší <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Pokud <xref:System.Windows.Controls.Calendar.DisplayMode%2A> je již <xref:System.Windows.Controls.CalendarMode.Month>, žádná akce.|  
|MEZERNÍK nebo ENTER|<xref:System.Windows.Controls.CalendarMode.Year> Nebo <xref:System.Windows.Controls.CalendarMode.Decade>|Přepínače <xref:System.Windows.Controls.Calendar.DisplayMode%2A> k <xref:System.Windows.Controls.CalendarMode.Month> nebo <xref:System.Windows.Controls.CalendarMode.Year> reprezentována cílených položky.|  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
