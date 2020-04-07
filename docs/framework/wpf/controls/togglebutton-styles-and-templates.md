---
title: ToggleButton – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805920"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton – styly a šablony

Toto téma popisuje styly a <xref:System.Windows.Controls.Primitives.ToggleButton> šablony ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> prvek, aby ovládací prvek jedinečný vzhled. Další informace naleznete [v tématu Vytvoření šablony ovládacího prvku](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="togglebutton-parts"></a>Součásti přepínačů

Ovládací <xref:System.Windows.Controls.Primitives.ToggleButton> prvek nemá žádné pojmenované části.

## <a name="togglebutton-states"></a>Stavy přepínacích tlačítek

V následující tabulce jsou uvedeny stavy vizuálu ovládacího <xref:System.Windows.Controls.Primitives.ToggleButton> prvku.

|Název VisualState|Název visualstategroup|Popis|
|-|-|-|
|Normální|Běžné státy|Výchozí stav.|
|Mouseover|Běžné státy|Ukazatel myši je umístěn nad ovládacím prvkem.|
|Pressed|Běžné státy|Ovládací prvek je stisknut.|
|Zakázáno|Běžné státy|Ovládací prvek je zakázán.|
|Focused|FocusStates|Ovládací prvek má fokus.|
|Rozostřený|FocusStates|Ovládací prvek nemá fokus.|
|Zaškrtnuté|Zkontrolovat stavy|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `true`.|
|Nekontrolovaná|Zkontrolovat stavy|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `false`.|
|Neurčitý|Zkontrolovat stavy|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>je `true`a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`je .|
|Platné|Stavy ověření|Ovládací prvek <xref:System.Windows.Controls.Validation> používá třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `false`připojené vlastnosti je .|
|Neplatnéfocené|Stavy ověření|Připojená <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnost `true` je a ovládací prvek má fokus.|
|Neplatnýnezaostřený|Stavy ověření|Připojené <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnosti `true` je a ovládací prvek nemá fokus.|

> [!NOTE]
> Pokud neurčitý vizuální stav neexistuje v šabloně ovládacího prvku, bude jako výchozí vizuální stav použit nekontrolovaný vizuální stav.

## <a name="togglebutton-controltemplate-example"></a>Příklad šablony ovládacího prvku togglebutton

Následující příklad ukazuje, jak <xref:System.Windows.Controls.ControlTemplate> definovat <xref:System.Windows.Controls.Primitives.ToggleButton> pro ovládací prvek.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

Předchozí příklad používá jeden nebo více z následujících zdrojů.

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

Kompletní ukázku naleznete [v tématu Styling s ukázkou řídicích šablon](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
