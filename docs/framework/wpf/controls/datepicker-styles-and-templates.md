---
title: DatePicker – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: 013076fdac8666b974fdf0ce9b09740197031c15
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170543"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Ovládací prvek DatePicker částí  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.  
  
|Část|Type|Popis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Kořenový adresář ovládacího prvku.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Tlačítko, které se otevře a ukončí <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Textové pole, které umožňuje zadat datum.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Automaticky otevírané okno pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.|  
  
## <a name="datepicker-states"></a>DatePicker – stavy  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.DatePicker> Je zakázaná.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox částí  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ovládacího prvku.  
  
|Část|Type|Popis|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|Prvek, který obsahuje počáteční text <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>. Text <xref:System.Windows.Controls.TextBox> se zobrazí v tomto elementu.|  
  
## <a name="datepickertextbox-states"></a>Stavy DatePickerTextBox  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> Je zakázaná.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Uživatel nemůže změnit text <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Fokus|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Horní mezí|WatermarkStates|Ovládací prvek zobrazí počáteční text.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> Je ve stavu, když uživatel zadat text nebo vybral datum.|  
|Unwatermarked|WatermarkStates|Uživatel zadá text do <xref:System.Windows.Controls.Primitives.DatePickerTextBox> nebo vybrané datum v <xref:System.Windows.Controls.DatePicker>.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` a ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` a ovládací prvek nemá fokus.|  
  
## <a name="datepicker-controltemplate-example"></a>Příklad DatePicker ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](styling-and-templating.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
