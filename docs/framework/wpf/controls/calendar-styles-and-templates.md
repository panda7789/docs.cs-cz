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
ms.openlocfilehash: 64cb62a3459a3eeea6aa5e91b433a58a88ab08ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283560"
---
# <a name="calendar-styles-and-templates"></a>Styly a šablony kalendáře
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Calendar>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="calendar-parts"></a>Části kalendáře  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Calendar>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Aktuálně zobrazený měsíc nebo rok na <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Panel, který obsahuje <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Kalendářní stavy  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Calendar>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="calendaritem-parts"></a>CalendarItem části  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Kořen ovládacího prvku|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Tlačítko, které zobrazí předchozí stránku v kalendáři po kliknutí.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Tlačítko, které zobrazí další stránku v kalendáři po kliknutí.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Tlačítko, které umožňuje přepínání mezi režimem měsíce, rokem a režimem dekády.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Obsah se hostuje v režimu měsíce.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Obsah se hostuje v režimu rok nebo desetiletí.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Překryv pro zakázaný stav.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> popisující vizuální strukturu.|  
  
## <a name="calendaritem-states"></a>CalendarItem stavy  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální stav|CommonStates|Výchozí stav.|  
|Zakázaný stav|CommonStates|Stav kalendáře, pokud je vlastnost <xref:System.Windows.UIElement.IsEnabled%2A> `false`.|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton části  
 Ovládací prvek <xref:System.Windows.Controls.Primitives.CalendarDayButton> neobsahuje žádné pojmenované části.  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton stavy  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.CalendarDayButton>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Výchozí stav.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> je zakázaný.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn na <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Stisknutí|CommonStates|Stiskne se <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Vybrané|SelectionStates|Je vybráno tlačítko.|  
|Nevybrané|SelectionStates|Tlačítko není vybráno.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Tlačítko má fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Tlačítko nemá fokus.|  
|Zaměřil|FocusStates|Tlačítko má fokus.|  
|Bez fokusu|FocusStates|Tlačítko nemá fokus.|  
|Aktivní|ActiveStates|Tlačítko je aktivní.|  
|Neaktivní|ActiveStates|Tlačítko je neaktivní.|  
|RegularDay|DayStates|Tlačítko nepředstavuje <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Dnes|DayStates|Tlačítko představuje <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Tlačítko představuje den, který lze vybrat.|  
|BlackoutDay|BlackoutDayStates|Tlačítko představuje den, který nelze vybrat.|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="calendarbutton-parts"></a>CalendarButton části  
 Ovládací prvek <xref:System.Windows.Controls.Primitives.CalendarButton> neobsahuje žádné pojmenované části.  
  
## <a name="calendarbutton-states"></a>CalendarButton stavy  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.CalendarButton>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Výchozí stav.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> je zakázaný.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn na <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Stisknutí|CommonStates|Stiskne se <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Vybrané|SelectionStates|Je vybráno tlačítko.|  
|Nevybrané|SelectionStates|Tlačítko není vybráno.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Tlačítko má fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Tlačítko nemá fokus.|  
|Zaměřil|FocusStates|Tlačítko má fokus.|  
|Bez fokusu|FocusStates|Tlačítko nemá fokus.|  
|Aktivní|ActiveStates|Tlačítko je aktivní.|  
|Neaktivní|ActiveStates|Tlačítko je neaktivní.|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="calendar-controltemplate-example"></a>Příklad kalendáře ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Calendar> a přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 Předchozí příklad používá jeden nebo více následujících zdrojů.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
