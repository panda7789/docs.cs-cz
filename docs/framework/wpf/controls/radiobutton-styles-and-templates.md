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
ms.openlocfilehash: 892b4bead6ef6db3a6c007e34fb333ebf1e39850
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459859"
---
# <a name="radiobutton-styles-and-templates"></a>RadioButton – styly a šablony
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.RadioButton>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="radiobutton-parts"></a>Části RadioButton  
 Ovládací prvek <xref:System.Windows.Controls.RadioButton> neobsahuje žádné pojmenované části.  
  
## <a name="radiobutton-states"></a>Stavy RadioButton  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.RadioButton>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Běžnou|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn nad ovládacím prvkem.|  
|Stisknete|CommonStates|Ovládací prvek se stiskne.|  
|Zabezpečen|CommonStates|Ovládací prvek je zakázán.|  
|Zaměřil|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Kontrolovaný|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `true`.|  
|Není zaškrtnuto|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `false`.|  
|Definované|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> je `true`a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`.|  
|Platné|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="radiobutton-controltemplate-example"></a>ControlTemplate – příklad pro přepínač  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.RadioButton>.  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
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
