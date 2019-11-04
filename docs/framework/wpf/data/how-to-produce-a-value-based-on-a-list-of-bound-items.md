---
title: 'Postupy: Vygenerování hodnoty na základě seznamu připojených položek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459690"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="eff21-102">Postupy: Vygenerování hodnoty na základě seznamu připojených položek</span><span class="sxs-lookup"><span data-stu-id="eff21-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="eff21-103"><xref:System.Windows.Data.MultiBinding> umožňuje svázat vlastnost target vazby se seznamem vlastností zdroje a potom použít logiku pro vytvoření hodnoty s danými vstupy.</span><span class="sxs-lookup"><span data-stu-id="eff21-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="eff21-104">Tento příklad ukazuje, jak použít <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="eff21-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff21-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff21-105">Example</span></span>  
 <span data-ttu-id="eff21-106">V následujícím příkladu `NameListData` odkazuje na kolekci objektů `PersonName`, což jsou objekty, které obsahují dvě vlastnosti, `firstName` a `lastName`.</span><span class="sxs-lookup"><span data-stu-id="eff21-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="eff21-107">Následující příklad vytvoří <xref:System.Windows.Controls.TextBlock>, který zobrazuje jméno a příjmení osoby s posledním názvem.</span><span class="sxs-lookup"><span data-stu-id="eff21-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="eff21-108">Aby bylo možné pochopit, jak se vytvoří formát křestního jména, Podívejme se na implementaci `NameConverter`:</span><span class="sxs-lookup"><span data-stu-id="eff21-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="eff21-109">`NameConverter` implementuje rozhraní <xref:System.Windows.Data.IMultiValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="eff21-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="eff21-110">`NameConverter` přebírá hodnoty z jednotlivých vazeb a ukládá je do pole objektů hodnot.</span><span class="sxs-lookup"><span data-stu-id="eff21-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="eff21-111">Pořadí, ve kterém se <xref:System.Windows.Data.Binding> prvky zobrazí pod prvkem <xref:System.Windows.Data.MultiBinding>, je pořadí, ve kterém jsou tyto hodnoty uloženy v poli.</span><span class="sxs-lookup"><span data-stu-id="eff21-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="eff21-112">Hodnota atributu <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> je odkazována argumentem parametru metody <xref:System.Windows.Data.MultiBinding.Converter%2A>, která provádí přepínač na parametru pro určení způsobu formátování názvu.</span><span class="sxs-lookup"><span data-stu-id="eff21-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff21-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eff21-113">See also</span></span>

- [<span data-ttu-id="eff21-114">Převod vázaných dat</span><span class="sxs-lookup"><span data-stu-id="eff21-114">Convert Bound Data</span></span>](how-to-convert-bound-data.md)
- [<span data-ttu-id="eff21-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="eff21-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="eff21-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="eff21-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
