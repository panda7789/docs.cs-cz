---
title: "Postupy: Vygenerování hodnoty na základě seznamu připojených položek"
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
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d16a198ed78c1ffd9dcaad595e9cc9be3cb2de0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="eed6d-102">Postupy: Vygenerování hodnoty na základě seznamu připojených položek</span><span class="sxs-lookup"><span data-stu-id="eed6d-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="eed6d-103"><xref:System.Windows.Data.MultiBinding>Umožňuje vytvořit vazbu cílovou vlastnost vazby na seznamu vlastností zdroje a pak použít logiku k vytvoření hodnoty s danou vstupy.</span><span class="sxs-lookup"><span data-stu-id="eed6d-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="eed6d-104">Tento příklad ukazuje, jak používat <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="eed6d-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed6d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="eed6d-105">Example</span></span>  
 <span data-ttu-id="eed6d-106">V následujícím příkladu `NameListData` odkazuje na kolekci `PersonName` objekty, které jsou objekty, které obsahují dvě vlastnosti, `firstName` a `lastName`.</span><span class="sxs-lookup"><span data-stu-id="eed6d-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="eed6d-107">Následující příklad vytvoří <xref:System.Windows.Controls.TextBlock> který ukazuje první a poslední jméno osoby s příjmení první.</span><span class="sxs-lookup"><span data-stu-id="eed6d-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="eed6d-108">Abyste pochopili, jak se vytvářejí ve formátu poslední název první, Podívejme se na provádění `NameConverter`:</span><span class="sxs-lookup"><span data-stu-id="eed6d-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="eed6d-109">`NameConverter`implementuje <xref:System.Windows.Data.IMultiValueConverter> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eed6d-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="eed6d-110">`NameConverter`přijímá hodnoty z jednotlivých vazby a ukládá je v poli hodnoty objektu.</span><span class="sxs-lookup"><span data-stu-id="eed6d-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="eed6d-111">V jakém pořadí <xref:System.Windows.Data.Binding> prvky se zobrazí v části <xref:System.Windows.Data.MultiBinding> elementu je v tom pořadí, ve kterém jsou tyto hodnoty uloženy v poli.</span><span class="sxs-lookup"><span data-stu-id="eed6d-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="eed6d-112">Hodnota <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> atribut se odkazuje parametr argument <xref:System.Windows.Data.MultiBinding.Converter%2A> metodu, která provádí přepínač parametr k určení postupu pro název formátu.</span><span class="sxs-lookup"><span data-stu-id="eed6d-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed6d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="eed6d-113">See Also</span></span>  
 [<span data-ttu-id="eed6d-114">Převést vázaných dat</span><span class="sxs-lookup"><span data-stu-id="eed6d-114">Convert Bound Data</span></span>](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [<span data-ttu-id="eed6d-115">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="eed6d-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="eed6d-116">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="eed6d-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
