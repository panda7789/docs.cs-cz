---
title: GroupBox – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187482"
---
# <a name="groupbox-styles-and-templates"></a>GroupBox – styly a šablony
<a name="introduction"></a>Toto téma popisuje styly a <xref:System.Windows.Controls.GroupBox> šablony ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> prvek, aby ovládací prvek jedinečný vzhled. Další informace naleznete [v tématu Vytvoření šablony ovládacího prvku](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a>Součásti GroupBox  
 Ovládací <xref:System.Windows.Controls.GroupBox> prvek nemá žádné pojmenované části.  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a>Stavy GroupBox  
 V následující tabulce jsou uvedeny stavy vizuálu ovládacího <xref:System.Windows.Controls.GroupBox> prvku.  
  
|Název VisualState|Název visualstategroup|Popis|  
|-|-|-|  
|Platné|Stavy ověření|Ovládací prvek <xref:System.Windows.Controls.Validation> používá třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `false`připojené vlastnosti je .|  
|Neplatnéfocené|Stavy ověření|Připojená <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnost `true` má ovládací prvek má fokus.|  
|Neplatnýnezaostřený|Stavy ověření|Připojená <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnost `true` má ovládací prvek nemá fokus.|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a>Příklad šablony ovládacího prvku GroupBox  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.ControlTemplate> definovat <xref:System.Windows.Controls.GroupBox> pro ovládací prvek.  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 Používá <xref:System.Windows.Controls.ControlTemplate> jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Kompletní ukázku naleznete [v tématu Styling s ukázkou řídicích šablon](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
