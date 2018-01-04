---
title: "ProgressBar – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6809ce2f51af8a1baf535afa8fe80f4e5b5f53e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="progressbar-parts"></a>ProgressBar – součásti  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|Objekt, který označuje průběh.|  
|PART_Track|<xref:System.Windows.FrameworkElement>|Objekt, který definuje cestu indikátoru průběhu.|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|Objekt, který embellishes indikátor průběhu.|  
  
## <a name="progressbar-states"></a>ProgressBar – stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Determinate|CommonStates|<xref:System.Windows.Controls.ProgressBar>sestavy průběhu na základě <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastnost.|  
|Neurčitém|CommonStates|<xref:System.Windows.Controls.ProgressBar>sestavy obecný postup s opakující se vzorek.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="progressbar-controltemplate-example"></a>Příklad ControlTemplate ProgressBar  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
