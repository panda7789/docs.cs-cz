---
title: "Postupy: Určení zdroje připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05f77e8939b9b81a9e3861df6a44bc3585a0a504
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="e2651-102">Postupy: Určení zdroje připojení</span><span class="sxs-lookup"><span data-stu-id="e2651-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="e2651-103">V datové vazbě zdrojového objektu vazby odkazuje na objekt, který je získat data z.</span><span class="sxs-lookup"><span data-stu-id="e2651-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="e2651-104">Toto téma popisuje různé způsoby zadávání zdroji vazby.</span><span class="sxs-lookup"><span data-stu-id="e2651-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2651-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2651-105">Example</span></span>  
 <span data-ttu-id="e2651-106">Pokud vytváříte několik vlastností vazbu na běžné zdroj, kterou chcete použít `DataContext` vlastnosti, která nabízí pohodlný způsob, jak vytvořit obor, ve kterém všechny vlastnosti vázané na data dědit společný zdroj.</span><span class="sxs-lookup"><span data-stu-id="e2651-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="e2651-107">V následujícím příkladu je vytvořeno kontextu dat v kořenovém elementu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2651-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="e2651-108">To umožňuje všechny podřízené elementy pro tento kontext dat dědění.</span><span class="sxs-lookup"><span data-stu-id="e2651-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="e2651-109">Data pro vazbu pochází od třídy vlastních dat `NetIncome`, odkazuje přímo prostřednictvím mapování a zadané prostředků klíč `incomeDataSource`.</span><span class="sxs-lookup"><span data-stu-id="e2651-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="e2651-110">Následující příklad zobrazuje definici `NetIncome` třídy.</span><span class="sxs-lookup"><span data-stu-id="e2651-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  <span data-ttu-id="e2651-111">Výše uvedený příklad inicializuje objekt v značek a používá jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="e2651-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="e2651-112">Pokud chcete vytvořit vazbu na objekt, který má již byly vytvořeny v kódu, je nutné nastavit `DataContext` vlastnost prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="e2651-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="e2651-113">Příklad, naleznete v části [zkontrolujte Data k dispozici pro vazbu v jazyce XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="e2651-113">For an example, see [Make Data Available for Binding in XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="e2651-114">Případně pokud chcete určit zdroj na jednotlivé vazby explicitně, máte následující možnosti.</span><span class="sxs-lookup"><span data-stu-id="e2651-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="e2651-115">Tyto mají přednost před zděděné data kontextu.</span><span class="sxs-lookup"><span data-stu-id="e2651-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="e2651-116">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e2651-116">Property</span></span>|<span data-ttu-id="e2651-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e2651-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="e2651-118">Pomocí této vlastnosti lze nastavit zdroj instance objektu.</span><span class="sxs-lookup"><span data-stu-id="e2651-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="e2651-119">Pokud nepotřebujete funkce vytvoření oboru ve vlastnosti, které několik dědění stejné kontextu dat, můžete použít <xref:System.Windows.Data.Binding.Source%2A> vlastnost místo `DataContext` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e2651-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="e2651-120">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2651-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="e2651-121">To je užitečné, pokud chcete určit zdroj relativně k, kde je váš cíl vazby.</span><span class="sxs-lookup"><span data-stu-id="e2651-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="e2651-122">Některé běžné scénáře, kde může používat tato vlastnost je, když chcete vytvořit vazbu jednu vlastnost vaší elementu na jinou vlastnost stejného elementu nebo pokud definování vazbu v styl nebo šabloně.</span><span class="sxs-lookup"><span data-stu-id="e2651-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="e2651-123">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2651-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="e2651-124">Zadáte řetězec, který reprezentuje element, který chcete vytvořit vazbu na.</span><span class="sxs-lookup"><span data-stu-id="e2651-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="e2651-125">To je užitečné, pokud chcete vytvořit vazbu na vlastnost jiný element ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e2651-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="e2651-126">Například, pokud chcete použít <xref:System.Windows.Controls.Slider> řídit výšku jiného ovládacího prvku ve vaší aplikaci, nebo pokud chcete vytvořit vazbu <xref:System.Windows.Controls.ContentControl.Content%2A> ovládacího prvku na <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost vaší <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2651-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="e2651-127">Další informace naleznete v tématu <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2651-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2651-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2651-128">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e2651-129">Hodnota dědičnost vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e2651-129">Property Value Inheritance</span></span>](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)  
 [<span data-ttu-id="e2651-130">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="e2651-130">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="e2651-131">Přehled deklarace vazby</span><span class="sxs-lookup"><span data-stu-id="e2651-131">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="e2651-132">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="e2651-132">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
