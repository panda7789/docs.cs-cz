---
title: "Postupy: Řazení a seskupení dat použitím zobrazení XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c219def87e258a2c9fc1bf4f4867287e6156c59a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="d3022-102">Postupy: Řazení a seskupení dat použitím zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="d3022-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="d3022-103">Tento příklad ukazuje, jak vytvořit zobrazení shromažďování dat v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3022-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="d3022-104">Zobrazení umožňují funkce seskupování, řazení a filtrování a představu o aktuální položky.</span><span class="sxs-lookup"><span data-stu-id="d3022-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3022-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3022-105">Example</span></span>  
 <span data-ttu-id="d3022-106">V následujícím příkladu, statické prostředků s názvem *umístí* je definována jako kolekce *místní* objekty, kde každá *místní* objekt se skládal z název města a stav.</span><span class="sxs-lookup"><span data-stu-id="d3022-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="d3022-107">Předpona *src* je namapovaný na obor názvů kde zdroj dat *místech* je definována.</span><span class="sxs-lookup"><span data-stu-id="d3022-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="d3022-108">Předpona *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` a *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="d3022-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="d3022-109">Následující příklad vytvoří zobrazení shromažďování dat, který je seřazené podle názvu města a seskupené podle stavu.</span><span class="sxs-lookup"><span data-stu-id="d3022-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="d3022-110">Zobrazení pak může být zdrojem vazby, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d3022-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="d3022-111">Pro vazby na data XML, které jsou definované v <xref:System.Windows.Data.XmlDataProvider> prostředků, zadejte před název XML @ symbol.</span><span class="sxs-lookup"><span data-stu-id="d3022-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="d3022-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3022-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="d3022-113">Získat výchozí zobrazení shromažďování dat</span><span class="sxs-lookup"><span data-stu-id="d3022-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="d3022-114">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="d3022-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="d3022-115">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="d3022-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
