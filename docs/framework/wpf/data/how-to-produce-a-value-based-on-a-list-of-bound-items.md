---
title: 'Postupy: Vygenerování hodnoty na základě seznamu vázaných položek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: c2ec5ff26c89649294df266e790445e5aa5d08ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200516"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="740e8-102">Postupy: Vygenerování hodnoty na základě seznamu vázaných položek</span><span class="sxs-lookup"><span data-stu-id="740e8-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<xref:System.Windows.Data.MultiBinding> <span data-ttu-id="740e8-103">Umožňuje vytvoření vazby vlastnosti cílové vazby na seznam vlastností zdroje a pak použít logiku k vytvoření hodnoty se dané vstupy.</span><span class="sxs-lookup"><span data-stu-id="740e8-103">allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="740e8-104">Tento příklad ukazuje, jak používat <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="740e8-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="740e8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="740e8-105">Example</span></span>  
 <span data-ttu-id="740e8-106">V následujícím příkladu `NameListData` odkazuje na kolekci `PersonName` objekty, které jsou objekty, které obsahují dvě vlastnosti, `firstName` a `lastName`.</span><span class="sxs-lookup"><span data-stu-id="740e8-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="740e8-107">Následující příklad vytvoří <xref:System.Windows.Controls.TextBlock> , která zobrazuje jména a příjmení osoby s příjmení první.</span><span class="sxs-lookup"><span data-stu-id="740e8-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="740e8-108">Informace o tom vytváření formátu poslední název first, Pojďme se podívat na provádění `NameConverter`:</span><span class="sxs-lookup"><span data-stu-id="740e8-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` <span data-ttu-id="740e8-109">Implementuje <xref:System.Windows.Data.IMultiValueConverter> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="740e8-109">implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> `NameConverter` <span data-ttu-id="740e8-110">přijímá hodnoty od jednotlivých vazeb a ukládá je v objektu pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="740e8-110">takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="740e8-111">Pořadí, ve kterém <xref:System.Windows.Data.Binding> prvky se zobrazí pod <xref:System.Windows.Data.MultiBinding> elementu je v tom pořadí, ve kterém jsou tyto hodnoty uloženy v poli.</span><span class="sxs-lookup"><span data-stu-id="740e8-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="740e8-112">Hodnota <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> atribut odkazuje argument parametru <xref:System.Windows.Data.MultiBinding.Converter%2A> metodu, která provádí přepínač parametru lze určit, jak se formát názvu.</span><span class="sxs-lookup"><span data-stu-id="740e8-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740e8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="740e8-113">See also</span></span>

- [<span data-ttu-id="740e8-114">Převod vázaných dat</span><span class="sxs-lookup"><span data-stu-id="740e8-114">Convert Bound Data</span></span>](how-to-convert-bound-data.md)
- [<span data-ttu-id="740e8-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="740e8-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="740e8-116">– postupy</span><span class="sxs-lookup"><span data-stu-id="740e8-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
