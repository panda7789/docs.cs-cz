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
ms.openlocfilehash: 323768b6221061d46446ab18f85555f5f7415e74
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460365"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker – styly a šablony
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.DatePicker>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>DatePicker části  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.DatePicker>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Kořen ovládacího prvku|  
|PART_Button|<xref:System.Windows.Controls.Button>|Tlačítko, které se otevře a zavře <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Textové pole, které umožňuje zadat datum.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Místní nabídka pro ovládací prvek <xref:System.Windows.Controls.DatePicker>.|  
  
## <a name="datepicker-states"></a>DatePicker stavy  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.DatePicker>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|Zabezpečen|CommonStates|<xref:System.Windows.Controls.DatePicker> je zakázaný.|  
|Platné|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox části  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|Element, který obsahuje počáteční text v <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>. Text <xref:System.Windows.Controls.TextBox> se zobrazí v tomto elementu.|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox stavy  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|Zabezpečen|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> je zakázaný.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn na <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Uživatel nemůže měnit text v <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Zaměřil|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Vodoznakem|WatermarkStates|Ovládací prvek zobrazí svůj úvodní text.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> je ve stavu, kdy uživatel nezadal text nebo datum nevybralo.|  
|Nevodoznak|WatermarkStates|Uživatel zadal text do <xref:System.Windows.Controls.Primitives.DatePickerTextBox> nebo vybral datum v <xref:System.Windows.Controls.DatePicker>.|  
|Platné|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek nemá fokus.|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate – příklad  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.DatePicker>.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 Předchozí příklad používá jeden nebo více následujících zdrojů.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
