---
title: Kalendář
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: e99a716e7ca8f7b2c9ed11543f37e0b8cb7422a6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460818"
---
# <a name="calendar"></a>Kalendář
Kalendář umožňuje uživateli vybrat datum pomocí vizuálního zobrazení kalendáře.  
  
 Ovládací prvek <xref:System.Windows.Controls.Calendar> lze použít samostatně nebo jako rozevírací část <xref:System.Windows.Controls.DatePicker> ovládacího prvku. Další informace najdete v tématu <xref:System.Windows.Controls.DatePicker>.  
  
 Následující ilustrace znázorňuje dva ovládací prvky <xref:System.Windows.Controls.Calendar>, jeden s výběry a nedostupnosti data a jedna bez.  
  
 ![Ovládací prvky kalendáře](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Ovládací prvky kalendáře  
  
 Následující tabulka poskytuje informace o úlohách, které jsou obvykle spojeny s <xref:System.Windows.Controls.Calendar>.  
  
|Úloha|Implementace|  
|----------|--------------------|  
|Zadejte data, která nelze vybrat.|Použijte vlastnost <xref:System.Windows.Controls.Calendar.BlackoutDates%2A>.|  
|Zobrazí <xref:System.Windows.Controls.Calendar> měsíc, celý rok nebo desetiletí.|Vlastnost <xref:System.Windows.Controls.Calendar.DisplayMode%2A> nastavte na month, Year nebo desetiletí.|  
|Určete, zda může uživatel vybrat datum, rozsah kalendářních dat nebo více rozsahů dat.|Použijte <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Zadejte rozsah dat, který <xref:System.Windows.Controls.Calendar> zobrazit.|Použijte vlastnosti <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> a <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A>.|  
|Určuje, zda je zvýrazněno aktuální datum.|Použijte vlastnost <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>. Ve výchozím nastavení je <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> `true`.|  
|Změňte velikost <xref:System.Windows.Controls.Calendar>.|Použijte <xref:System.Windows.Controls.Viewbox> nebo nastavte vlastnost <xref:System.Windows.FrameworkElement.LayoutTransform%2A> na <xref:System.Windows.Media.ScaleTransform>. Všimněte si, že pokud nastavíte <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Calendar>, skutečný kalendář nemění jeho velikost.|  
  
 Ovládací prvek <xref:System.Windows.Controls.Calendar> poskytuje základní navigaci pomocí myši nebo klávesnice. Následující tabulka shrnuje navigaci na klávesnici.  
  
|Kombinace kláves|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Akce|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|ŠIPKU|<xref:System.Windows.Controls.CalendarMode.Month>|Změní vlastnost <xref:System.Windows.Controls.Calendar.SelectedDate%2A>, pokud vlastnost <xref:System.Windows.Controls.Calendar.SelectionMode%2A> není nastavena na <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|ŠIPKU|<xref:System.Windows.Controls.CalendarMode.Year>|Změní měsíc vlastnosti <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Všimněte si, že se <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nemění.|  
|ŠIPKU|<xref:System.Windows.Controls.CalendarMode.Decade>|Změní rok <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Všimněte si, že se <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nemění.|  
|SHIFT + ŠIPKA|<xref:System.Windows.Controls.CalendarMode.Month>|Pokud <xref:System.Windows.Controls.Calendar.SelectionMode%2A> není nastavená na <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> nebo <xref:System.Windows.Controls.CalendarSelectionMode.None>, rozšiřuje rozsah vybraných dat.|  
|DOMOVSKÉ|<xref:System.Windows.Controls.CalendarMode.Month>|Změní <xref:System.Windows.Controls.Calendar.SelectedDate%2A> na první den aktuálního měsíce.|  
|DOMOVSKÉ|<xref:System.Windows.Controls.CalendarMode.Year>|Změní měsíc <xref:System.Windows.Controls.Calendar.DisplayDate%2A> do prvního měsíce roku. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> se nemění.|  
|DOMOVSKÉ|<xref:System.Windows.Controls.CalendarMode.Decade>|Změní rok <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na první rok desetiletí. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> se nemění.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Změní <xref:System.Windows.Controls.Calendar.SelectedDate%2A> na poslední den aktuálního měsíce.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Změní měsíc <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na poslední měsíc v roce. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> se nemění.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Změní rok <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na poslední rok desetiletí. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> se nemění.|  
|CTRL + ŠIPKA NAHORU|Jakýmikoli|Přepne na další větší <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Pokud je již <xref:System.Windows.Controls.Calendar.DisplayMode%2A> <xref:System.Windows.Controls.CalendarMode.Decade>, žádná akce.|  
|CTRL + ŠIPKA DOLŮ|Jakýmikoli|Přepne na další menší <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Pokud je již <xref:System.Windows.Controls.Calendar.DisplayMode%2A> <xref:System.Windows.Controls.CalendarMode.Month>, žádná akce.|  
|MEZERNÍK nebo ENTER|<xref:System.Windows.Controls.CalendarMode.Year> nebo <xref:System.Windows.Controls.CalendarMode.Decade>|Přepne <xref:System.Windows.Controls.Calendar.DisplayMode%2A> do <xref:System.Windows.Controls.CalendarMode.Month> nebo <xref:System.Windows.Controls.CalendarMode.Year> reprezentované položkou s fokusem.|  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky](index.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
