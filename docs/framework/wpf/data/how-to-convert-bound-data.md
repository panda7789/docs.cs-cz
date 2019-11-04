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
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458867"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="18e5c-102">Postupy: Převod připojených dat</span><span class="sxs-lookup"><span data-stu-id="18e5c-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="18e5c-103">Tento příklad ukazuje, jak použít převod na data, která se používají ve vazbách.</span><span class="sxs-lookup"><span data-stu-id="18e5c-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="18e5c-104">Chcete-li převést data během vytváření vazby, je nutné vytvořit třídu, která implementuje rozhraní <xref:System.Windows.Data.IValueConverter>, které zahrnuje metody <xref:System.Windows.Data.IValueConverter.Convert%2A> a <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.</span><span class="sxs-lookup"><span data-stu-id="18e5c-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18e5c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="18e5c-105">Example</span></span>  
 <span data-ttu-id="18e5c-106">Následující příklad ukazuje implementaci převaděče data, který převede hodnotu data předaného, aby zobrazila pouze rok, měsíc a den.</span><span class="sxs-lookup"><span data-stu-id="18e5c-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="18e5c-107">Při implementaci rozhraní <xref:System.Windows.Data.IValueConverter> je vhodné sezpůsobovat implementaci pomocí atributu <xref:System.Windows.Data.ValueConversionAttribute>, aby označoval vývojové nástroje jako datové typy, které jsou součástí převodu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="18e5c-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="18e5c-108">Po vytvoření převaděče ho můžete přidat jako prostředek do souboru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18e5c-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="18e5c-109">V následujícím příkladu *Src* mapuje na obor názvů, ve kterém je definována *DateConverter* .</span><span class="sxs-lookup"><span data-stu-id="18e5c-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="18e5c-110">Nakonec můžete použít převodník ve vazbě pomocí následující syntaxe.</span><span class="sxs-lookup"><span data-stu-id="18e5c-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="18e5c-111">V následujícím příkladu je textový obsah <xref:System.Windows.Controls.TextBlock> svázán s *StartDate*, což je vlastnost externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="18e5c-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="18e5c-112">Prostředky stylu, na které je odkazováno v předchozím příkladu, jsou definovány v oddílu prostředků, který není zobrazen v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="18e5c-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e5c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18e5c-113">See also</span></span>

- [<span data-ttu-id="18e5c-114">Implementace ověření vazby</span><span class="sxs-lookup"><span data-stu-id="18e5c-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="18e5c-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="18e5c-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="18e5c-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="18e5c-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
