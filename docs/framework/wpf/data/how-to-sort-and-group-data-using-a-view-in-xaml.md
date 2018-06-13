---
title: 'Postupy: Řazení a seskupení dat použitím zobrazení XAML'
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
ms.openlocfilehash: 80529420bcc5fdca473313e164b3d096732953f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555825"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="4e9d8-102">Postupy: Řazení a seskupení dat použitím zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="4e9d8-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="4e9d8-103">Tento příklad ukazuje, jak vytvořit zobrazení shromažďování dat v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e9d8-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="4e9d8-104">Zobrazení umožňují funkce seskupování, řazení a filtrování a představu o aktuální položky.</span><span class="sxs-lookup"><span data-stu-id="4e9d8-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e9d8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e9d8-105">Example</span></span>  
 <span data-ttu-id="4e9d8-106">V následujícím příkladu, statické prostředků s názvem *umístí* je definována jako kolekce *místní* objekty, kde každá *místní* objekt se skládal z název města a stav.</span><span class="sxs-lookup"><span data-stu-id="4e9d8-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="4e9d8-107">Předpona *src* je namapovaný na obor názvů kde zdroj dat *místech* je definována.</span><span class="sxs-lookup"><span data-stu-id="4e9d8-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="4e9d8-108">Předpona *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` a *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="4e9d8-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="4e9d8-109">Následující příklad vytvoří zobrazení shromažďování dat, který je seřazené podle názvu města a seskupené podle stavu.</span><span class="sxs-lookup"><span data-stu-id="4e9d8-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="4e9d8-110">Zobrazení pak může být zdrojem vazby, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4e9d8-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="4e9d8-111">Pro vazby na data XML, které jsou definované v <xref:System.Windows.Data.XmlDataProvider> prostředků, zadejte před název XML @ symbol.</span><span class="sxs-lookup"><span data-stu-id="4e9d8-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="4e9d8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e9d8-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="4e9d8-113">Načtení výchozího zobrazení datové kolekce</span><span class="sxs-lookup"><span data-stu-id="4e9d8-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="4e9d8-114">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="4e9d8-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="4e9d8-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="4e9d8-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
