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
ms.openlocfilehash: 26989474f264161be12bcc14fed614fdc7f775b6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460328"
---
# <a name="expander-styles-and-templates"></a>Styly a šablony rozšíření
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Expander>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="expander-parts"></a>Části rozšíření  
 Ovládací prvek <xref:System.Windows.Controls.Expander> neobsahuje žádné pojmenované části.  
  
## <a name="expander-states"></a>Stavy rozšíření  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Expander>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn nad ovládacím prvkem.|  
|Zabezpečen|CommonStates|Ovládací prvek je zakázán.|  
|Zaměřil|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Rozbalil|ExpansionStates|Ovládací prvek je rozbalený.|  
|Sbalený|ExpansionStates|Ovládací prvek není rozbalen.|  
|ExpandDown|ExpandDirectionStates|Ovládací prvek se rozbalí dolů.|  
|ExpandUp|ExpandDirectionStates|Ovládací prvek se rozšíří nahoru.|  
|ExpandLeft|ExpandDirectionStates|Ovládací prvek se rozšíří doleva.|  
|ExpandRight|ExpandDirectionStates|Ovládací prvek se rozšíří doprava.|  
|Platné|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="expander-controltemplate-example"></a>Příklad rozšíření ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Expander>.  
  
 [!code-xaml[ControlTemplateExamples#Expander](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
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
