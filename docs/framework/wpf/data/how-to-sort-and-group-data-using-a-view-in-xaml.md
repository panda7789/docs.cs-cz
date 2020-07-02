---
title: 'Postupy: Řazení a seskupení dat použitím zobrazení XAML'
description: Naučte se vytvořit zobrazení shromažďování dat pro seskupování, řazení a filtrování v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621675"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="bce11-103">Postupy: Řazení a seskupení dat použitím zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="bce11-103">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="bce11-104">Tento příklad ukazuje, jak vytvořit zobrazení shromažďování dat v nástroji [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bce11-104">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="bce11-105">Zobrazení umožňují funkce seskupování, řazení, filtrování a pojmu aktuální položky.</span><span class="sxs-lookup"><span data-stu-id="bce11-105">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bce11-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bce11-106">Example</span></span>  
 <span data-ttu-id="bce11-107">V následujícím příkladu je statický prostředek s názvem *místa* definován jako kolekce objektů typu *místo* , kde každý objekt *umístit* je sestávat z názvu města a stavu.</span><span class="sxs-lookup"><span data-stu-id="bce11-107">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="bce11-108">Předpona *Src* je namapována na obor názvů, ve kterém je definováno zdrojové *umístění* zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="bce11-108">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="bce11-109">Předpona *SCM* mapuje na `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` a *dat* mapuje na `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` .</span><span class="sxs-lookup"><span data-stu-id="bce11-109">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="bce11-110">Následující příklad vytvoří zobrazení kolekce dat, která je seřazena podle názvu města a seskupena podle stavu.</span><span class="sxs-lookup"><span data-stu-id="bce11-110">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="bce11-111">Zobrazení může být pak zdrojem vazby, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bce11-111">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="bce11-112">Pro vazby na data XML definovaná v <xref:System.Windows.Data.XmlDataProvider> prostředku předchází název XML symbolem @.</span><span class="sxs-lookup"><span data-stu-id="bce11-112">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="bce11-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bce11-113">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="bce11-114">Získat výchozí zobrazení shromažďování dat</span><span class="sxs-lookup"><span data-stu-id="bce11-114">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="bce11-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="bce11-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="bce11-116">– postupy</span><span class="sxs-lookup"><span data-stu-id="bce11-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
