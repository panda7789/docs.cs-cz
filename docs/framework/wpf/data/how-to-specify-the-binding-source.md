---
title: 'Postupy: Určení zdroje připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 4fde66b22bac6b4a2cfeb4eceb50027daadee387
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454364"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="847de-102">Postupy: Určení zdroje připojení</span><span class="sxs-lookup"><span data-stu-id="847de-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="847de-103">V datové vazbě odkazuje zdrojový objekt vazby na objekt, ze kterého získáváte data.</span><span class="sxs-lookup"><span data-stu-id="847de-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="847de-104">Toto téma popisuje různé způsoby určení zdroje vazby.</span><span class="sxs-lookup"><span data-stu-id="847de-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="847de-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="847de-105">Example</span></span>  
 <span data-ttu-id="847de-106">Pokud vytváříte vazbu několika vlastností na společný zdroj, budete chtít použít vlastnost `DataContext`, která poskytuje pohodlný způsob, jak vytvořit obor, ve kterém všechny vlastnosti vázané na data dědí společný zdroj.</span><span class="sxs-lookup"><span data-stu-id="847de-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="847de-107">V následujícím příkladu je datový kontext vytvořen v kořenovém elementu aplikace.</span><span class="sxs-lookup"><span data-stu-id="847de-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="847de-108">To umožňuje všem podřízeným elementům dědit tento datový kontext.</span><span class="sxs-lookup"><span data-stu-id="847de-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="847de-109">Data pro vazbu pocházejí z vlastní třídy dat, `NetIncome`, na kterou odkazuje přímo prostřednictvím mapování a s použitím klíče prostředku `incomeDataSource`.</span><span class="sxs-lookup"><span data-stu-id="847de-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="847de-110">Následující příklad ukazuje definici třídy `NetIncome`.</span><span class="sxs-lookup"><span data-stu-id="847de-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> <span data-ttu-id="847de-111">Výše uvedený příklad vytvoří instanci objektu v kódu a použije ho jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="847de-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="847de-112">Pokud chcete vytvořit propojení s objektem, který již byl vytvořen v kódu, je nutné nastavit vlastnost `DataContext` programově.</span><span class="sxs-lookup"><span data-stu-id="847de-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="847de-113">Příklad naleznete [v tématu zpřístupnění dat pro vazbu v jazyce XAML](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="847de-113">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="847de-114">Případně, pokud chcete zadat zdroj pro jednotlivé vazby explicitně, máte následující možnosti.</span><span class="sxs-lookup"><span data-stu-id="847de-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="847de-115">Mají přednost před zděděným kontextem dat.</span><span class="sxs-lookup"><span data-stu-id="847de-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="847de-116">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="847de-116">Property</span></span>|<span data-ttu-id="847de-117">Popis</span><span class="sxs-lookup"><span data-stu-id="847de-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="847de-118">Tato vlastnost slouží k nastavení zdroje na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="847de-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="847de-119">Pokud nepotřebujete, aby bylo možné vytvořit obor, ve kterém několik vlastností dědí stejný kontext dat, můžete místo vlastnosti `DataContext` použít vlastnost <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="847de-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="847de-120">Další informace najdete v tématu <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="847de-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="847de-121">To je užitečné, pokud chcete určit zdroj relativní k umístění vazby na cíl.</span><span class="sxs-lookup"><span data-stu-id="847de-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="847de-122">Některé běžné scénáře, kdy můžete použít tuto vlastnost, je, když chcete svázat jednu vlastnost elementu s jinou vlastností stejného prvku nebo pokud definujete vazbu ve stylu nebo šabloně.</span><span class="sxs-lookup"><span data-stu-id="847de-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="847de-123">Další informace najdete v tématu <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="847de-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="847de-124">Zadejte řetězec, který představuje prvek, ke kterému se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="847de-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="847de-125">To je užitečné, pokud chcete vytvořit vazby na vlastnost jiného prvku v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="847de-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="847de-126">Například pokud chcete použít <xref:System.Windows.Controls.Slider> k řízení výšky jiného ovládacího prvku v aplikaci, nebo pokud chcete navazovat <xref:System.Windows.Controls.ContentControl.Content%2A> ovládacího prvku na vlastnost <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> ovládacího prvku <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="847de-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="847de-127">Další informace najdete v tématu <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="847de-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="847de-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="847de-128">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="847de-129">Dědičnost hodnoty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="847de-129">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="847de-130">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="847de-130">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="847de-131">Přehled deklarací vazeb</span><span class="sxs-lookup"><span data-stu-id="847de-131">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="847de-132">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="847de-132">How-to Topics</span></span>](data-binding-how-to-topics.md)
