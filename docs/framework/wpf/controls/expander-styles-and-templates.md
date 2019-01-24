---
title: Styly a šablony rozšíření
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
ms.openlocfilehash: 99d11b599d79c9f0d998f49cc0f12fee9c83c39a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551966"
---
# <a name="expander-styles-and-templates"></a>Styly a šablony rozšíření
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Expander> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="expander-parts"></a>Rozšíření částí  
 <xref:System.Windows.Controls.Expander> Ovládací prvek nemá žádné pojmenované součásti.  
  
## <a name="expander-states"></a>Stavy rozšíření  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Expander> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad ovládací prvek.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Fokus|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Rozbalení|ExpansionStates|Ovládací prvek je rozbalený.|  
|Sbalení|ExpansionStates|Ovládací prvek není rozbalen.|  
|ExpandDown|ExpandDirectionStates|Rozšíří ovládací prvek dolů.|  
|ExpandUp|ExpandDirectionStates|Rozšíří ovládací prvek nahoru.|  
|ExpandLeft|ExpandDirectionStates|Ovládací prvek vlevo rozšíří.|  
|ExpandRight|ExpandDirectionStates|Ovládací prvek rozšíří vpravo.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="expander-controltemplate-example"></a>Příklad šablony ControlTemplate rozšíření  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Expander> ovládacího prvku.  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
