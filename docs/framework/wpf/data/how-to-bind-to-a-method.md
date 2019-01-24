---
title: 'Postupy: Připojení k metodě'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: afa7801709d733ed40389f240fa5d92a2557c7a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732073"
---
# <a name="how-to-bind-to-a-method"></a>Postupy: Připojení k metodě
Následující příklad ukazuje, jak vytvořit vazbu na metodu pomocí <xref:System.Windows.Data.ObjectDataProvider>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `TemperatureScale` je třída, která obsahuje metodu `ConvertTemp`, který přebírá dva parametry (jeden z `double` a jeden z `enum` typ `TempType)` a převede zadanou hodnotu z jednoho teploty škálování. V následujícím příkladu <xref:System.Windows.Data.ObjectDataProvider> slouží k vytvoření instance `TemperatureScale` objektu. `ConvertTemp` Metoda je volána pomocí dvou zadaných parametrů.  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Teď, když metoda je k dispozici jako prostředek, můžete vázat na jeho výsledky. V následujícím příkladu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z <xref:System.Windows.Controls.ComboBox> jsou vázány na dva parametry metody. To umožňuje uživatelům zadat teploty pro převod a teploty škálování pro převod z. Všimněte si, že <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> je nastavena na `true` vzhledem k tomu, že jsme připojujete <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> vlastnost <xref:System.Windows.Data.ObjectDataProvider> instance a nikoli vlastnosti objektu zabalený nástrojem <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` objekt).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> Posledního <xref:System.Windows.Controls.Label> aktualizuje, když uživatel upraví obsah <xref:System.Windows.Controls.TextBox> nebo výběr <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Převaděč `DoubleToString` přijímá typ double a převede ji na řetězec v <xref:System.Windows.Data.IValueConverter.Convert%2A> směr (ze zdroje vazby na cíl vazby, který je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost) a převede `string` k `double` v <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> směr.  
  
 `InvalidationCharacterRule` Je <xref:System.Windows.Controls.ValidationRule> , která zkontroluje neobsahuje neplatné znaky. Chyba šablony výchozí, což je červené ohraničení kolem <xref:System.Windows.Controls.TextBox>, zobrazí se oznámení uživatelům, pokud vstupní hodnota není hodnotu double.  
  
## <a name="see-also"></a>Viz také:
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
- [Vytvoření vazby k vyčíslení](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
