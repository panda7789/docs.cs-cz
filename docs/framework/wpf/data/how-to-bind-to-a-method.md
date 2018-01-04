---
title: "Postupy: Připojení k metodě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45f2a141b09c52085c13803b8d338fdc9eebf135
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-method"></a>Postupy: Připojení k metodě
Následující příklad ukazuje, jak vytvořit vazbu k metoda pomocí <xref:System.Windows.Data.ObjectDataProvider>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `TemperatureScale` je třída, která má metodu `ConvertTemp`, který přebírá dva parametry (jeden z `double` a jedno z `enum` typu `TempType)` a převede danou hodnotu z teploty jeden škálování. V následujícím příkladu se <xref:System.Windows.Data.ObjectDataProvider> slouží k vytváření instancí `TemperatureScale` objektu. `ConvertTemp` Metoda je volána se dvěma zadanými parametry.  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Teď, když metoda je k dispozici jako prostředek, můžete vázat na své výsledky. V následujícím příkladu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z <xref:System.Windows.Controls.ComboBox> je vázána na dva parametry metody. To umožňuje uživatelům zadat teploty převést a škálování teploty převést z. Všimněte si, že <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> je nastaven na `true` vzhledem k tomu, že jsme vazbu k <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> vlastnost <xref:System.Windows.Data.ObjectDataProvider> instance a není vlastnosti objektu zabalen <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` objekt).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> Posledního <xref:System.Windows.Controls.Label> aktualizuje, když uživatel změní obsah <xref:System.Windows.Controls.TextBox> nebo výběr <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Převaděč `DoubleToString` trvá dvojitou a převede ji na řetězec v <xref:System.Windows.Data.IValueConverter.Convert%2A> směr (ze zdroje vazba vazby cíl, který je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnosti) a převede `string` k `double` v <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> směr.  
  
 `InvalidationCharacterRule` Je <xref:System.Windows.Controls.ValidationRule> , zkontroluje neplatné znaky. Výchozí šablony chyby, což je červené ohraničení kolem <xref:System.Windows.Controls.TextBox>, se zobrazí upozornění uživatelům, pokud vstupní hodnota není hodnota typu double.  
  
## <a name="see-also"></a>Viz také  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Vytvoření vazby k vyčíslení](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
