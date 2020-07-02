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
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="01d2e-103">Postupy: Připojení k metodě</span><span class="sxs-lookup"><span data-stu-id="01d2e-103">How to: Bind to a Method</span></span>
<span data-ttu-id="01d2e-104">Následující příklad ukazuje, jak vytvořit spojení s metodou pomocí <xref:System.Windows.Data.ObjectDataProvider> .</span><span class="sxs-lookup"><span data-stu-id="01d2e-104">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d2e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d2e-105">Example</span></span>  
 <span data-ttu-id="01d2e-106">V tomto příkladu `TemperatureScale` je třída, která má metodu `ConvertTemp` , která má dva parametry (jeden z těchto `double` typů a jeden z nich `enum` `TempType)` a převádí danou hodnotu z jednoho měřítka teploty na jiný).</span><span class="sxs-lookup"><span data-stu-id="01d2e-106">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="01d2e-107">V následujícím příkladu <xref:System.Windows.Data.ObjectDataProvider> se používá pro vytvoření instance `TemperatureScale` objektu.</span><span class="sxs-lookup"><span data-stu-id="01d2e-107">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="01d2e-108">`ConvertTemp`Metoda je volána se dvěma zadanými parametry.</span><span class="sxs-lookup"><span data-stu-id="01d2e-108">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="01d2e-109">Teď, když je metoda k dispozici jako prostředek, můžete vytvořit vazby na její výsledky.</span><span class="sxs-lookup"><span data-stu-id="01d2e-109">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="01d2e-110">V následujícím příkladu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost třídy <xref:System.Windows.Controls.TextBox> a je <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> svázána s dvěma parametry metody.</span><span class="sxs-lookup"><span data-stu-id="01d2e-110">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="01d2e-111">Díky tomu mohou uživatelé určit teplotu, která se má převést, a škála teploty pro převod.</span><span class="sxs-lookup"><span data-stu-id="01d2e-111">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="01d2e-112">Všimněte si, že <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> je nastavena na, protože je vytvořena `true` vazba na <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> vlastnost <xref:System.Windows.Data.ObjectDataProvider> instance a nikoli vlastnosti objektu zabaleného <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` objekt).</span><span class="sxs-lookup"><span data-stu-id="01d2e-112">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="01d2e-113"><xref:System.Windows.Controls.ContentControl.Content%2A>Poslední <xref:System.Windows.Controls.Label> aktualizace, pokud uživatel upraví obsah <xref:System.Windows.Controls.TextBox> nebo výběru <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="01d2e-113">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="01d2e-114">Konvertor `DoubleToString` přebírá dvojitou hodnotu a převede ji na řetězec ve <xref:System.Windows.Data.IValueConverter.Convert%2A> směru (od zdroje vazby k cíli vazby, který je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost) a převádí `string` na a `double` ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> směru.</span><span class="sxs-lookup"><span data-stu-id="01d2e-114">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="01d2e-115">`InvalidationCharacterRule`Je a <xref:System.Windows.Controls.ValidationRule> , který kontroluje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="01d2e-115">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="01d2e-116">Výchozí šablona chyby, která je červeným ohraničením kolem <xref:System.Windows.Controls.TextBox> , se zobrazí uživateli s informací o tom, že vstupní hodnota není dvojitá hodnota.</span><span class="sxs-lookup"><span data-stu-id="01d2e-116">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d2e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01d2e-117">See also</span></span>

- [<span data-ttu-id="01d2e-118">– postupy</span><span class="sxs-lookup"><span data-stu-id="01d2e-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="01d2e-119">Vazba na výčet</span><span class="sxs-lookup"><span data-stu-id="01d2e-119">Bind to an Enumeration</span></span>](how-to-bind-to-an-enumeration.md)
