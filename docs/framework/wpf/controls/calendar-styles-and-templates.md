---
title: Styly a šablony kalendáře
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: a6f88d3371f4122a11c25a7cdf498f5822420498
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="calendar-styles-and-templates"></a>Styly a šablony kalendáře
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Calendar> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Části kalendáře  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Calendar> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Aktuálně zobrazený měsíc nebo rok na <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Na panelu, který obsahuje <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Stavy kalendáře  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Calendar> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendaritem-parts"></a>CalendarItem částí  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Primitives.CalendarItem> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Kořen ovládacího prvku.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Tlačítko, které se zobrazí na předchozí stránku kalendáře po klepnutí.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Tlačítko, které se zobrazí na další stránku kalendáře po klepnutí.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Tlačítko, které umožňuje přepínání mezi režimu měsíc, rok režim a režim desetiletí.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Hostitelem obsahu v režimu měsíc.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Hostitelem obsahu v roce nebo desetiletí režimu.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Překrytí pro zakázaném stavu.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> , Který popisuje strukturu visual.|  
  
## <a name="calendaritem-states"></a>CalendarItem stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.CalendarItem> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální stavu|CommonStates|Ve výchozím stavu.|  
|Stav Zakázáno|CommonStates|Stav kalendáře při <xref:System.Windows.UIElement.IsEnabled%2A> vlastnost je `false`.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton částí  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> Ovládací prvek nemá žádné pojmenované částí.  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.CalendarDayButton> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Je zakázána.|  
|Myš nad|CommonStates|Umístění ukazatele myši nad <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Stisknutí tlačítka|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Stisknutí.|  
|Vybrané|SelectionStates|Výběru tlačítka.|  
|Nezaškrtnuté|SelectionStates|Tlačítko není vybraná.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Tlačítko má právě fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Tlačítko nemá fokus.|  
|Zaměřuje|FocusStates|Tlačítko má právě fokus.|  
|Nezaostřená|FocusStates|Tlačítko nemá fokus.|  
|Aktivní|ActiveStates|Tlačítko je aktivní.|  
|Neaktivní|ActiveStates|Tlačítko je neaktivní.|  
|RegularDay|DayStates|Tlačítko nepředstavuje <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Dnes|DayStates|Tlačítko představuje <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Tlačítko představuje dne, kterou je možné vybrat.|  
|BlackoutDay|BlackoutDayStates|Tlačítko představuje za den, který nelze vybrat.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendarbutton-parts"></a>CalendarButton částí  
 <xref:System.Windows.Controls.Primitives.CalendarButton> Ovládací prvek nemá žádné pojmenované částí.  
  
## <a name="calendarbutton-states"></a>CalendarButton stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.CalendarButton> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Je zakázána.|  
|Myš nad|CommonStates|Umístění ukazatele myši nad <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Stisknutí tlačítka|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Stisknutí.|  
|Vybrané|SelectionStates|Výběru tlačítka.|  
|Nezaškrtnuté|SelectionStates|Tlačítko není vybraná.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Tlačítko má právě fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Tlačítko nemá fokus.|  
|Zaměřuje|FocusStates|Tlačítko má právě fokus.|  
|Nezaostřená|FocusStates|Tlačítko nemá fokus.|  
|Aktivní|ActiveStates|Tlačítko je aktivní.|  
|Neaktivní|ActiveStates|Tlačítko je neaktivní.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendar-controltemplate-example"></a>Příklad ControlTemplate kalendáře  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Calendar> řízení a přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
