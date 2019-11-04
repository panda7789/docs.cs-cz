---
title: ProgressBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459882"
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar – styly a šablony
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="progressbar-parts"></a>Součásti ProgressBar  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.ProgressBar>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|Objekt, který označuje průběh.|  
|PART_Track|<xref:System.Windows.FrameworkElement>|Objekt, který definuje cestu indikátoru průběhu.|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|Objekt, který embellishes indikátor průběhu.|  
  
## <a name="progressbar-states"></a>Stavy ProgressBar  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Zrušit ukončení|CommonStates|<xref:System.Windows.Controls.ProgressBar> sestaví průběh na základě vlastnosti <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.|  
|Definované|CommonStates|<xref:System.Windows.Controls.ProgressBar> sestavuje obecný průběh pomocí opakujícího se vzoru.|  
|Platné|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="progressbar-controltemplate-example"></a>Příklad ControlTemplate ProgressBar  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
