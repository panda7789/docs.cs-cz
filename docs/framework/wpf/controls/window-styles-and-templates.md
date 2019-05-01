---
title: Styly a šablony oken
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: ebd21829591b8fefe87aeba0b86280f18eff4f06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62023829"
---
# <a name="window-styles-and-templates"></a>Styly a šablony oken
Toto téma popisuje styly a šablony pro <xref:System.Windows.Window> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="window-parts"></a>Součásti okna  
 <xref:System.Windows.Window> Ovládací prvek nemá žádné pojmenované součásti.  
  
## <a name="window-states"></a>Okno stavy  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Window> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="window-controltemplate-example"></a>Příklad okna ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Window> ovládacího prvku.  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](styling-and-templating.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
