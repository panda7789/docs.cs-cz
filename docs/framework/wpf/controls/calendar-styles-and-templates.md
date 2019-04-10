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
ms.openlocfilehash: 18bef548b11f1a680c1361027b86f6952bedaad0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227108"
---
# <a name="calendar-styles-and-templates"></a>Styly a šablony kalendáře
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Calendar> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Části kalendáře  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Calendar> ovládacího prvku.  
  
|Část|Type|Popis|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Aktuálně zobrazený měsíc nebo rok v <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Na panelu, který obsahuje <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Stavy kalendáře  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Calendar> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendaritem-parts"></a>CalendarItem částí  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Primitives.CalendarItem> ovládacího prvku.  
  
|Část|Type|Popis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Kořenový adresář ovládacího prvku.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Tlačítko, které při kliknutí se zobrazí na předchozí stránku kalendáře.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Tlačítko, které při kliknutí zobrazí další stránky v kalendáři.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Tlačítko, které umožňuje přepínání mezi režimem měsíc, rok režimu a režimu deset let.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Hostuje obsah v režimu měsíc.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Hostuje obsah v režimu rok nebo deset let.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Překrytí pro zakázaném stavu.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> , Který popisuje vizuální struktury.|  
  
## <a name="calendaritem-states"></a>Stavy CalendarItem  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.CalendarItem> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální stavu|CommonStates|Ve výchozím stavu.|  
|Stav vypnuto|CommonStates|Stav kalendáře při <xref:System.Windows.UIElement.IsEnabled%2A> vlastnost `false`.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton částí  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> Ovládací prvek nemá žádné pojmenované součásti.  
  
## <a name="calendardaybutton-states"></a>Stavy CalendarDayButton  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.CalendarDayButton> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Je zakázaná.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Stisknutí|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Stisknutí.|  
|Vybráno|SelectionStates|Výběru tlačítka.|  
|Nevybrané|SelectionStates|Tlačítko není vybrané.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Tlačítko má fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Tlačítko nemá fokus.|  
|Fokus|FocusStates|Tlačítko má fokus.|  
|Bez fokusu|FocusStates|Tlačítko nemá fokus.|  
|Aktivní|ActiveStates|Tlačítko je aktivní.|  
|Neaktivní|ActiveStates|Je tlačítko neaktivní.|  
|RegularDay|DayStates|Nepředstavuje tlačítko <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Dnes|DayStates|Představuje tlačítko <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Tlačítko představuje den, který je možné vybrat.|  
|BlackoutDay|BlackoutDayStates|Tlačítko představuje den, který nelze vybrat.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendarbutton-parts"></a>CalendarButton částí  
 <xref:System.Windows.Controls.Primitives.CalendarButton> Ovládací prvek nemá žádné pojmenované součásti.  
  
## <a name="calendarbutton-states"></a>Stavy CalendarButton  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.CalendarButton> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Je zakázaná.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Stisknutí|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Stisknutí.|  
|Vybráno|SelectionStates|Výběru tlačítka.|  
|Nevybrané|SelectionStates|Tlačítko není vybrané.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Tlačítko má fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Tlačítko nemá fokus.|  
|Fokus|FocusStates|Tlačítko má fokus.|  
|Bez fokusu|FocusStates|Tlačítko nemá fokus.|  
|Aktivní|ActiveStates|Tlačítko je aktivní.|  
|Neaktivní|ActiveStates|Je tlačítko neaktivní.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="calendar-controltemplate-example"></a>Příklad šablony ControlTemplate kalendáře  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Calendar> ovládacího prvku a přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](styling-and-templating.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
