---
title: Ovládací prvek DatePicker styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: b50716cc83114fea5120b12659668437ac9bd6da
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457722"
---
# <a name="datepicker-styles-and-templates"></a>Ovládací prvek DatePicker styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Ovládací prvek DatePicker částí  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Kořen ovládacího prvku.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Tlačítko, které se otevře a zavření <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Textové pole, které umožňuje vstupní datum.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Místní nabídka pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.|  
  
## <a name="datepicker-states"></a>Ovládací prvek DatePicker stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|zakázáno|CommonStates|<xref:System.Windows.Controls.DatePicker> Je zakázána.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox částí  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|Element, který obsahuje počáteční text v <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>. Text <xref:System.Windows.Controls.TextBox> se zobrazí v tomto elementu.|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|zakázáno|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> Je zakázána.|  
|Myš nad|CommonStates|Umístění ukazatele myši nad <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Uživatel nemůže změnit text v <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Zaměřuje|FocusStates|Ovládací prvek má právě fokus.|  
|Nezaostřená|FocusStates|Ovládací prvek nemá fokus.|  
|Mezí|WatermarkStates|Ovládací prvek zobrazí jeho počáteční text.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> Je ve stavu, pokud uživatel nebyl zadaný text nebo vybrané datum.|  
|Unwatermarked|WatermarkStates|Uživatel zadal text do <xref:System.Windows.Controls.Primitives.DatePickerTextBox> nebo vybrat datum v <xref:System.Windows.Controls.DatePicker>.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="datepicker-controltemplate-example"></a>Ovládací prvek DatePicker ControlTemplate příklad  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DatePicker> ovládacího prvku.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
