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
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="db490-102">Postupy: Připojení k metodě</span><span class="sxs-lookup"><span data-stu-id="db490-102">How to: Bind to a Method</span></span>
<span data-ttu-id="db490-103">Následující příklad ukazuje, jak vytvořit vazbu k metoda pomocí <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="db490-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db490-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="db490-104">Example</span></span>  
 <span data-ttu-id="db490-105">V tomto příkladu `TemperatureScale` je třída, která má metodu `ConvertTemp`, který přebírá dva parametry (jeden z `double` a jedno z `enum` typu `TempType)` a převede danou hodnotu z teploty jeden škálování.</span><span class="sxs-lookup"><span data-stu-id="db490-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="db490-106">V následujícím příkladu se <xref:System.Windows.Data.ObjectDataProvider> slouží k vytváření instancí `TemperatureScale` objektu.</span><span class="sxs-lookup"><span data-stu-id="db490-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="db490-107">`ConvertTemp` Metoda je volána se dvěma zadanými parametry.</span><span class="sxs-lookup"><span data-stu-id="db490-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="db490-108">Teď, když metoda je k dispozici jako prostředek, můžete vázat na své výsledky.</span><span class="sxs-lookup"><span data-stu-id="db490-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="db490-109">V následujícím příkladu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z <xref:System.Windows.Controls.ComboBox> je vázána na dva parametry metody.</span><span class="sxs-lookup"><span data-stu-id="db490-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="db490-110">To umožňuje uživatelům zadat teploty převést a škálování teploty převést z.</span><span class="sxs-lookup"><span data-stu-id="db490-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="db490-111">Všimněte si, že <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> je nastaven na `true` vzhledem k tomu, že jsme vazbu k <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> vlastnost <xref:System.Windows.Data.ObjectDataProvider> instance a není vlastnosti objektu zabalen <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` objekt).</span><span class="sxs-lookup"><span data-stu-id="db490-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="db490-112"><xref:System.Windows.Controls.ContentControl.Content%2A> Posledního <xref:System.Windows.Controls.Label> aktualizuje, když uživatel změní obsah <xref:System.Windows.Controls.TextBox> nebo výběr <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="db490-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="db490-113">Převaděč `DoubleToString` trvá dvojitou a převede ji na řetězec v <xref:System.Windows.Data.IValueConverter.Convert%2A> směr (ze zdroje vazba vazby cíl, který je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnosti) a převede `string` k `double` v <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> směr.</span><span class="sxs-lookup"><span data-stu-id="db490-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="db490-114">`InvalidationCharacterRule` Je <xref:System.Windows.Controls.ValidationRule> , zkontroluje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="db490-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="db490-115">Výchozí šablony chyby, což je červené ohraničení kolem <xref:System.Windows.Controls.TextBox>, se zobrazí upozornění uživatelům, pokud vstupní hodnota není hodnota typu double.</span><span class="sxs-lookup"><span data-stu-id="db490-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db490-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="db490-116">See Also</span></span>  
 [<span data-ttu-id="db490-117">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="db490-117">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [<span data-ttu-id="db490-118">Vytvoření vazby k vyčíslení</span><span class="sxs-lookup"><span data-stu-id="db490-118">Bind to an Enumeration</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
