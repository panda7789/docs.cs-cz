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
ms.openlocfilehash: 09ddf4119b64229be7fcda7b29c80ca6122d65f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tabcontrol-styles-and-templates"></a>TabControl – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TabControl> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="tabcontrol-parts"></a>Části TabControl  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.TabControl> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_SelectedContentHost|<xref:System.Windows.Controls.ContentPresenter>|Objekt, který zobrazí obsah aktuálně vybrané <xref:System.Windows.Controls.TabItem>.|  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TabControl>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.TabControl>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.  
  
## <a name="tabcontrol-states"></a>Stavy TabControl  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.TabControl> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="tabitem-parts"></a>Části TabItem  
 <xref:System.Windows.Controls.TabItem> Ovládací prvek nemá žádné pojmenované částí.  
  
## <a name="tabitem-states"></a>Stavy TabItem  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.TabItem> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad ovládacího prvku.|  
|zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Zaměřuje|FocusStates|Ovládací prvek má právě fokus.|  
|Nezaostřená|FocusStates|Ovládací prvek nemá fokus.|  
|Vybrané|SelectionStates|Požadovaný ovládací prvek.|  
|Nezaškrtnuté|SelectionStates|Ovládací prvek není vybrán.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="tabcontrol-controltemplate-example"></a>Příklad ControlTemplate TabControl  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TabControl> a <xref:System.Windows.Controls.TabItem> ovládací prvky.  
  
 [!code-xaml[ControlTemplateExamples#TabControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tabcontrol.xaml#tabcontrol)]  
  
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
