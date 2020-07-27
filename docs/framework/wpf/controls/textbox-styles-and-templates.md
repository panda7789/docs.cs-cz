---
title: TextBox – styly a šablony
description: Přečtěte si o stylech a šablonách ovládacího prvku TextBox Windows Presentation Foundation. Upravte ControlTemplate tak, aby měl ovládací prvek jedinečný vzhled.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164731"
---
# <a name="textbox-styles-and-templates"></a>TextBox – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TextBox> ovládací prvek. Můžete změnit výchozí nastavení <xref:System.Windows.Controls.ControlTemplate> a dát ovládacímu prvku jedinečný vzhled. Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="textbox-parts"></a>Části textového pole  
 V následující tabulce jsou uvedeny pojmenované části <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement> . Text <xref:System.Windows.Controls.TextBox> je zobrazen v tomto elementu.|  
  
## <a name="textbox-states"></a>Textové pole – stavy  
 V následující tabulce jsou uvedeny vizuální stavy <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn nad ovládacím prvkem.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázán.|  
|ReadOnly|CommonStates|Uživatel nemůže změnit text v <xref:System.Windows.Controls.TextBox> .|  
|Focused|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojenou vlastnost je `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost má `true` fokus na ovládací prvek.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="textbox-controltemplate-example"></a>Příklad textového ControlTemplateu  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TextBox> ovládací prvek.  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 Předchozí příklad používá jeden nebo více následujících zdrojů.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
