---
title: TabControl – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TabControl
- TabControl [WPF], styles and templates [WPF]
- parts [WPF], TabControl
- styles [WPF], TabControl
- states [WPF], TabControl
- templates [WPF], TabControl
ms.assetid: f6b19a30-f10e-4fa1-96ce-f17a54092ab6
ms.openlocfilehash: ac8349453eaef2167746de639a7e2c111a019b86
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356309"
---
# <a name="tabcontrol-styles-and-templates"></a>TabControl – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TabControl> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="tabcontrol-parts"></a>TabControl – částí  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.TabControl> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_SelectedContentHost|<xref:System.Windows.Controls.ContentPresenter>|Objekt, který zobrazí obsah aktuálně vybraného <xref:System.Windows.Controls.TabItem>.|  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TabControl>, šablona může obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazuje každou položku v <xref:System.Windows.Controls.TabControl>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není za přímé podřízeného člena <xref:System.Windows.Controls.ScrollViewer>, je třeba zadat <xref:System.Windows.Controls.ItemsPresenter> názvu, `ItemsPresenter`.  
  
## <a name="tabcontrol-states"></a>TabControl – stavy  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.TabControl> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="tabitem-parts"></a>Části TabItem  
 <xref:System.Windows.Controls.TabItem> Ovládací prvek nemá žádné pojmenované součásti.  
  
## <a name="tabitem-states"></a>Stavy TabItem  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.TabItem> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad ovládací prvek.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Fokus|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Vybráno|SelectionStates|Ovládací prvek je vybrán.|  
|Nevybrané|SelectionStates|Ovládací prvek není vybrán.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="tabcontrol-controltemplate-example"></a>TabControl – příklad šablony ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TabControl> a <xref:System.Windows.Controls.TabItem> ovládací prvky.  
  
 [!code-xaml[ControlTemplateExamples#TabControl](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tabcontrol.xaml#tabcontrol)]  
  
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
