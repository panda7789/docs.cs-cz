---
title: RadioButton – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
ms.openlocfilehash: 4f401c928db57a75bafa7fee0e59542b2eb8a3b6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377058"
---
# <a name="radiobutton-styles-and-templates"></a>RadioButton – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="radiobutton-parts"></a>Části ovládacího prvku RadioButton  
 <xref:System.Windows.Controls.RadioButton> Ovládací prvek nemá žádné pojmenované součásti.  
  
## <a name="radiobutton-states"></a>Stavy ovládacího prvku RadioButton  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad ovládací prvek.|  
|Stisknutí|CommonStates|Stisknutí ovládacího prvku.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Fokus|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Zaškrtnuto|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `true`.|  
|Není zaškrtnuto|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `false`.|  
|Neurčitá|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> je `true`, a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `null`.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="radiobutton-controltemplate-example"></a>Příklad šablony ControlTemplate ovládacího prvku RadioButton  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
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
