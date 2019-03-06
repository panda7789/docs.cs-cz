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
ms.openlocfilehash: c98f8e4e5c837e6fbbe836a9eb2f228d2d689542
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352293"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="d3f47-102">Postupy: Převod připojených dat</span><span class="sxs-lookup"><span data-stu-id="d3f47-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="d3f47-103">Tento příklad ukazuje, jak použít převod na data, která se používá ve vazbách.</span><span class="sxs-lookup"><span data-stu-id="d3f47-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="d3f47-104">K převodu dat při vytváření vazby, musíte vytvořit třídu, která implementuje <xref:System.Windows.Data.IValueConverter> rozhraní, která zahrnuje <xref:System.Windows.Data.IValueConverter.Convert%2A> a <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d3f47-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f47-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3f47-105">Example</span></span>  
 <span data-ttu-id="d3f47-106">Následující příklad ukazuje implementaci konvertor data, která převede datum hodnoty předané v tak, aby se zobrazí pouze roku, měsíce a dne.</span><span class="sxs-lookup"><span data-stu-id="d3f47-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="d3f47-107">Při implementaci <xref:System.Windows.Data.IValueConverter> rozhraní, je vhodné k vyplnění implementaci <xref:System.Windows.Data.ValueConversionAttribute> atribut skutečnost vývoj nástrojů typy dat zapojených do převodu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d3f47-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="d3f47-108">Jakmile vytvoříte konvertor, můžete ji přidat jako prostředek v vaše [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="d3f47-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="d3f47-109">V následujícím příkladu *src* mapuje na obor názvů, ve kterém *DateConverter* je definována.</span><span class="sxs-lookup"><span data-stu-id="d3f47-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="d3f47-110">Nakonec můžete použít převaděč ve vaší vazbě pomocí následující syntaxe.</span><span class="sxs-lookup"><span data-stu-id="d3f47-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="d3f47-111">V následujícím příkladu, obsah textu <xref:System.Windows.Controls.TextBlock> je vázán na *StartDate*, což je vlastnost z externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="d3f47-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="d3f47-112">Prostředků stylu odkazuje v předchozím příkladu jsou definovány v oddílu prostředků není zobrazené v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d3f47-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f47-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3f47-113">See also</span></span>
- [<span data-ttu-id="d3f47-114">Implementace ověření vazby</span><span class="sxs-lookup"><span data-stu-id="d3f47-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="d3f47-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="d3f47-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="d3f47-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="d3f47-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
