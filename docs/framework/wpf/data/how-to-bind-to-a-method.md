---
title: 'Postupy: Vytvoření vazby k metodě'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 6cdad46fd6d9ef3bc4ce1a13fedb6ff1d639d93e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123237"
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="be73f-102">Postupy: Vytvoření vazby k metodě</span><span class="sxs-lookup"><span data-stu-id="be73f-102">How to: Bind to a Method</span></span>
<span data-ttu-id="be73f-103">Následující příklad ukazuje, jak vytvořit vazbu na metodu pomocí <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="be73f-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be73f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="be73f-104">Example</span></span>  
 <span data-ttu-id="be73f-105">V tomto příkladu `TemperatureScale` je třída, která obsahuje metodu `ConvertTemp`, který přebírá dva parametry (jeden z `double` a jeden z `enum` typ `TempType)` a převede zadanou hodnotu z jednoho teploty škálování.</span><span class="sxs-lookup"><span data-stu-id="be73f-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="be73f-106">V následujícím příkladu <xref:System.Windows.Data.ObjectDataProvider> slouží k vytvoření instance `TemperatureScale` objektu.</span><span class="sxs-lookup"><span data-stu-id="be73f-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="be73f-107">`ConvertTemp` Metoda je volána pomocí dvou zadaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="be73f-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="be73f-108">Teď, když metoda je k dispozici jako prostředek, můžete vázat na jeho výsledky.</span><span class="sxs-lookup"><span data-stu-id="be73f-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="be73f-109">V následujícím příkladu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z <xref:System.Windows.Controls.ComboBox> jsou vázány na dva parametry metody.</span><span class="sxs-lookup"><span data-stu-id="be73f-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="be73f-110">To umožňuje uživatelům zadat teploty pro převod a teploty škálování pro převod z.</span><span class="sxs-lookup"><span data-stu-id="be73f-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="be73f-111">Všimněte si, že <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> je nastavena na `true` vzhledem k tomu, že jsme připojujete <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> vlastnost <xref:System.Windows.Data.ObjectDataProvider> instance a nikoli vlastnosti objektu zabalený nástrojem <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` objekt).</span><span class="sxs-lookup"><span data-stu-id="be73f-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="be73f-112"><xref:System.Windows.Controls.ContentControl.Content%2A> Posledního <xref:System.Windows.Controls.Label> aktualizuje, když uživatel upraví obsah <xref:System.Windows.Controls.TextBox> nebo výběr <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="be73f-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="be73f-113">Převaděč `DoubleToString` přijímá typ double a převede ji na řetězec v <xref:System.Windows.Data.IValueConverter.Convert%2A> směr (ze zdroje vazby na cíl vazby, který je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost) a převede `string` k `double` v <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> směr.</span><span class="sxs-lookup"><span data-stu-id="be73f-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="be73f-114">`InvalidationCharacterRule` Je <xref:System.Windows.Controls.ValidationRule> , která zkontroluje neobsahuje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="be73f-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="be73f-115">Chyba šablony výchozí, což je červené ohraničení kolem <xref:System.Windows.Controls.TextBox>, zobrazí se oznámení uživatelům, pokud vstupní hodnota není hodnotu double.</span><span class="sxs-lookup"><span data-stu-id="be73f-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be73f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be73f-116">See also</span></span>

- [<span data-ttu-id="be73f-117">– postupy</span><span class="sxs-lookup"><span data-stu-id="be73f-117">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="be73f-118">Vytvoření vazby k výčtu</span><span class="sxs-lookup"><span data-stu-id="be73f-118">Bind to an Enumeration</span></span>](how-to-bind-to-an-enumeration.md)
