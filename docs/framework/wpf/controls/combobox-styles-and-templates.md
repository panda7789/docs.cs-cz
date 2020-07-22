---
title: ComboBox – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: af7f8a544af5e9892a8f3f059048bbfd113d2491
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865356"
---
# <a name="combobox-styles-and-templates"></a>ComboBox – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ComboBox> ovládací prvek. Můžete změnit výchozí nastavení <xref:System.Windows.Controls.ControlTemplate> a dát ovládacímu prvku jedinečný vzhled. Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="combobox-parts"></a>Části pole se seznamem  
 V následující tabulce jsou uvedeny pojmenované části <xref:System.Windows.Controls.ComboBox> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Obsahuje text <xref:System.Windows.Controls.ComboBox> .|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Rozevírací seznam, který obsahuje položky v poli se seznamem.|  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ComboBox> , může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v <xref:System.Windows.Controls.ScrollViewer> . ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí všechny položky v <xref:System.Windows.Controls.ComboBox> ; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným prvku, je <xref:System.Windows.Controls.ScrollViewer> nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter` .  
  
## <a name="combobox-states"></a>Stavy pole se seznamem  
 V následující tabulce je uveden seznam stavů pro <xref:System.Windows.Controls.ComboBox> ovládací prvek.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Výchozí stav.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázán.|  
|MouseOver|CommonStates|Ukazatel myši je nad <xref:System.Windows.Controls.ComboBox> ovládacím prvkem.|  
|Focused|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|FocusedDropDown|FocusStates|Rozevírací seznam <xref:System.Windows.Controls.ComboBox> má fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojenou vlastnost je `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost je `true` a ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost je `true` a ovládací prvek nemá fokus.|  
|Možno|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A>Vlastnost je `true` .|  
|Nedá editovat|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A>Vlastnost je `false` .|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem části  
 <xref:System.Windows.Controls.ComboBoxItem>Ovládací prvek nemá žádné pojmenované části.  
  
## <a name="comboboxitem-states"></a>ComboBoxItem stavy  
 V následující tabulce je uveden seznam stavů pro <xref:System.Windows.Controls.ComboBoxItem> ovládací prvek.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Výchozí stav.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázán.|  
|MouseOver|CommonStates|Ukazatel myši je nad <xref:System.Windows.Controls.ComboBoxItem> ovládacím prvkem.|  
|Focused|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Vybráno|SelectionStates|Položka je aktuálně vybrána.|  
|Nevybrané|SelectionStates|Položka není vybrána.|  
|SelectedUnfocused|SelectionStates|Položka je vybrána, ale nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojenou vlastnost je `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost je `true` a ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost je `true` a ovládací prvek nemá fokus.|  
  
## <a name="combobox-controltemplate-example"></a>Příklad pole se seznamem ControlTemplate  
 Následující příklad ukazuje, jak definovat a <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ComboBox> ovládací prvek a přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
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
