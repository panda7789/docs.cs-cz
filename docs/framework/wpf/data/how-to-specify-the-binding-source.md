---
title: 'Postupy: Určení zdroje vazby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 8c866502300c50e00f1393b9e3fb64099f027c43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222299"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="1d5ec-102">Postupy: Určení zdroje vazby</span><span class="sxs-lookup"><span data-stu-id="1d5ec-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="1d5ec-103">V datové vazbě objekt zdroj vazby odkazuje na objekt, který je získat data z.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="1d5ec-104">Toto téma popisuje různé způsoby určení zdroje připojení.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d5ec-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d5ec-105">Example</span></span>  
 <span data-ttu-id="1d5ec-106">Pokud vytváříte několik vlastností vazbu na společný zdroj, kterou chcete použít `DataContext` vlastnost, která poskytuje pohodlný způsob, jak vytvořit obor, ve kterém zdědí všechny vlastnosti vázané na data společný zdroj.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="1d5ec-107">V následujícím příkladu se naváže kontext dat v kořenovém elementu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="1d5ec-108">To umožňuje všechny podřízené prvky dědit daného datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="1d5ec-109">Data pro vazbu pocházejí z vlastní datové třídy `NetIncome`, odkazuje přímo prostřednictvím mapování a daný klíč prostředku `incomeDataSource`.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="1d5ec-110">Následující příklad ukazuje definici `NetIncome` třídy.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  <span data-ttu-id="1d5ec-111">Výše uvedený příklad vytvoří instanci objektu ve značkách a použije ho jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="1d5ec-112">Pokud chcete vytvořit vazbu na objekt, který se už vytvářejí instance v kódu, je nutné nastavit `DataContext` vlastnost prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="1d5ec-113">Příklad najdete v tématu [zkontrolujte Data k dispozici pro vazbu v XAML](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1d5ec-113">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="1d5ec-114">Případně pokud chcete zadat zdroj na jednotlivé vazby explicitně, máte následující možnosti.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="1d5ec-115">Tyto přednost zděděné datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="1d5ec-116">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1d5ec-116">Property</span></span>|<span data-ttu-id="1d5ec-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1d5ec-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="1d5ec-118">Pomocí této vlastnosti se nastavit zdroj na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="1d5ec-119">Pokud nepotřebujete funkce pro vytváření oboru v několika vlastnosti, které dědí stejný datový kontext, můžete použít <xref:System.Windows.Data.Binding.Source%2A> vlastnost místo `DataContext` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="1d5ec-120">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="1d5ec-121">To je užitečné, pokud chcete zadat zdroj relativně vzhledem k, ve kterém je váš cíl vazby.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="1d5ec-122">Některé běžné scénáře, ve kterém může pomocí této vlastnosti je, když chcete svázat vlastnost jednoho prvku na jinou vlastnost stejného elementu nebo pokud definujete vazby ve stylu nebo šablony.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="1d5ec-123">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="1d5ec-124">Při zadání řetězce, který reprezentuje element, který chcete svázat.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="1d5ec-125">To je užitečné, pokud chcete vytvořit vazbu na vlastnost jiný element ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="1d5ec-126">Například, pokud chcete použít <xref:System.Windows.Controls.Slider> řídit výšku jiný ovládací prvek ve vaší aplikaci, nebo pokud chcete vytvořit vazbu <xref:System.Windows.Controls.ContentControl.Content%2A> ovládacího prvku na <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost vaše <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="1d5ec-127">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d5ec-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d5ec-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d5ec-128">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1d5ec-129">Dědičnost hodnoty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1d5ec-129">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="1d5ec-130">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="1d5ec-130">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="1d5ec-131">Přehled deklarací připojení</span><span class="sxs-lookup"><span data-stu-id="1d5ec-131">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="1d5ec-132">– postupy</span><span class="sxs-lookup"><span data-stu-id="1d5ec-132">How-to Topics</span></span>](data-binding-how-to-topics.md)
