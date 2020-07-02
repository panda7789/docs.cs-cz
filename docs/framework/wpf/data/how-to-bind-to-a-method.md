---
title: 'Postupy: Připojení k metodě'
description: Podle tohoto příkladu se dozvíte, jak vytvořit vazby k metodě objektu v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619595"
---
# <a name="how-to-bind-to-a-method"></a>Postupy: Připojení k metodě
Následující příklad ukazuje, jak vytvořit spojení s metodou pomocí <xref:System.Windows.Data.ObjectDataProvider> .  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `TemperatureScale` je třída, která má metodu `ConvertTemp` , která má dva parametry (jeden z těchto `double` typů a jeden z nich `enum` `TempType)` a převádí danou hodnotu z jednoho měřítka teploty na jiný). V následujícím příkladu <xref:System.Windows.Data.ObjectDataProvider> se používá pro vytvoření instance `TemperatureScale` objektu. `ConvertTemp`Metoda je volána se dvěma zadanými parametry.  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Teď, když je metoda k dispozici jako prostředek, můžete vytvořit vazby na její výsledky. V následujícím příkladu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost třídy <xref:System.Windows.Controls.TextBox> a je <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> svázána s dvěma parametry metody. Díky tomu mohou uživatelé určit teplotu, která se má převést, a škála teploty pro převod. Všimněte si, že <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> je nastavena na, protože je vytvořena `true` vazba na <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> vlastnost <xref:System.Windows.Data.ObjectDataProvider> instance a nikoli vlastnosti objektu zabaleného <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` objekt).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>Poslední <xref:System.Windows.Controls.Label> aktualizace, pokud uživatel upraví obsah <xref:System.Windows.Controls.TextBox> nebo výběru <xref:System.Windows.Controls.ComboBox> .  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Konvertor `DoubleToString` přebírá dvojitou hodnotu a převede ji na řetězec ve <xref:System.Windows.Data.IValueConverter.Convert%2A> směru (od zdroje vazby k cíli vazby, který je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost) a převádí `string` na a `double` ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> směru.  
  
 `InvalidationCharacterRule`Je a <xref:System.Windows.Controls.ValidationRule> , který kontroluje neplatné znaky. Výchozí šablona chyby, která je červeným ohraničením kolem <xref:System.Windows.Controls.TextBox> , se zobrazí uživateli s informací o tom, že vstupní hodnota není dvojitá hodnota.  
  
## <a name="see-also"></a>Viz také:

- [– postupy](data-binding-how-to-topics.md)
- [Vazba na výčet](how-to-bind-to-an-enumeration.md)
