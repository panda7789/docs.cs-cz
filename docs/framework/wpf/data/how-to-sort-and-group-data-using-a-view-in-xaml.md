---
title: 'Postupy: Řazení a seskupení dat pomocí zobrazení XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: ca4439b574264ebebfda745f0765f750099bc95f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020735"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="a9f25-102">Postupy: Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="a9f25-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="a9f25-103">Tento příklad ukazuje postup vytvoření zobrazení datové kolekce v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9f25-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="a9f25-104">Zobrazení umožňují funkce seskupení, řazení, filtrování a pojem s aktuální položkou.</span><span class="sxs-lookup"><span data-stu-id="a9f25-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9f25-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9f25-105">Example</span></span>  
 <span data-ttu-id="a9f25-106">V následujícím příkladu statický prostředek s názvem *umístí* je definována jako kolekce *místo* objekty, ve nichž každý *místo* objektu se skládal z název města a stav.</span><span class="sxs-lookup"><span data-stu-id="a9f25-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="a9f25-107">Předpona, která *src* je namapována na obor názvů kde zdroj dat *míst* je definována.</span><span class="sxs-lookup"><span data-stu-id="a9f25-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="a9f25-108">Předpona, která *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` a *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="a9f25-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="a9f25-109">Následující příklad vytvoří zobrazení shromažďování dat, který je seřazený podle název města a seskupených podle stavu.</span><span class="sxs-lookup"><span data-stu-id="a9f25-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="a9f25-110">Zobrazení pak může být zdrojem vazby, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a9f25-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="a9f25-111">U vazeb k datům XML s definovaný v <xref:System.Windows.Data.XmlDataProvider> prostředků, zadejte před název XML @ symbol.</span><span class="sxs-lookup"><span data-stu-id="a9f25-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="a9f25-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9f25-112">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="a9f25-113">Načtení výchozího zobrazení datové kolekce</span><span class="sxs-lookup"><span data-stu-id="a9f25-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="a9f25-114">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="a9f25-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="a9f25-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a9f25-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
