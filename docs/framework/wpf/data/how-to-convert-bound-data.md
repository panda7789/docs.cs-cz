---
title: 'Postupy: Převod připojených dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556637"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="fbf3d-102">Postupy: Převod připojených dat</span><span class="sxs-lookup"><span data-stu-id="fbf3d-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="fbf3d-103">Tento příklad ukazuje, jak se má použít převod na data, která se používá v vazby.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="fbf3d-104">Převést data během vazby, je nutné vytvořit třídu, která implementuje <xref:System.Windows.Data.IValueConverter> rozhraní, což zahrnuje <xref:System.Windows.Data.IValueConverter.Convert%2A> a <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbf3d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbf3d-105">Example</span></span>  
 <span data-ttu-id="fbf3d-106">Následující příklad ukazuje implementaci převaděč datum, který převádí hodnoty date předaná tak, aby se zobrazí pouze rok, měsíc a den.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="fbf3d-107">Při implementaci <xref:System.Windows.Data.IValueConverter> rozhraní, je vhodné pro uspořádání implementace s <xref:System.Windows.Data.ValueConversionAttribute> atribut a informuje vývoj nástrojů pro datové typy zahrnutých v převodu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fbf3d-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="fbf3d-108">Po vytvoření převaděč, můžete jej přidat jako prostředek v vaší [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="fbf3d-109">V následujícím příkladu *src* se mapuje na obor názvů, ve kterém *DateConverter* je definována.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="fbf3d-110">Nakonec můžete převaděč ve vašem vazbu pomocí následující syntaxe.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="fbf3d-111">V následujícím příkladu, obsah textu <xref:System.Windows.Controls.TextBlock> je vázán k *počátečním*, což je vlastnost externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="fbf3d-112">Styl prostředky, kterou se odkazuje v předchozím příkladu jsou definovány v oddílu prostředků není znázorněné v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="fbf3d-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf3d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbf3d-113">See Also</span></span>  
 [<span data-ttu-id="fbf3d-114">Implementace ověření vazby</span><span class="sxs-lookup"><span data-stu-id="fbf3d-114">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="fbf3d-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="fbf3d-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="fbf3d-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="fbf3d-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
