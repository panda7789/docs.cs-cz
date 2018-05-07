---
title: Styly a šablony jezdce
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: a32049befa84eb079fce7d2773360dc67cdbb8ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="thumb-syles-and-templates"></a>Styly a šablony jezdce
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="thumb-parts"></a>Jezdec částí  
 <xref:System.Windows.Controls.Primitives.Thumb> Ovládací prvek nemá žádné pojmenované částí.  
  
## <a name="thumb-states"></a>Jezdec stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad ovládacího prvku.|  
|Stisknutí tlačítka|CommonStates|Stisknutí ovládacího prvku.|  
|zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Zaměřuje|FocusStates|Ovládací prvek má právě fokus.|  
|Nezaostřená|FocusStates|Ovládací prvek nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="thumb-controltemplate-example"></a>Příklad ControlTemplate jezdec  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
