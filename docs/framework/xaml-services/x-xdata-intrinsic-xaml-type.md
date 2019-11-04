---
title: x:XData – vnitřní typ jazyka XAML
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459899"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="e21cb-102">x:XData – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="e21cb-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="e21cb-103">Umožňuje umístění datových ostrovů XML v rámci výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="e21cb-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="e21cb-104">Prvky XML v rámci `x:XData` by neměly být zpracovány pomocí procesorů XAML, jako by se jednalo o součást fungujícího výchozího oboru názvů jazyka XAML nebo jakýkoli jiný obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="e21cb-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="e21cb-105">`x:XData` mohou obsahovat libovolný kód XML ve správném formátu.</span><span class="sxs-lookup"><span data-stu-id="e21cb-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="e21cb-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="e21cb-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e21cb-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="e21cb-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="e21cb-108">Jeden kořenový prvek vloženého datového ostrova.</span><span class="sxs-lookup"><span data-stu-id="e21cb-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="e21cb-109">Pro většinu případných uživatelů se XML, který nemá jeden kořenový adresář, považuje za neplatnou.</span><span class="sxs-lookup"><span data-stu-id="e21cb-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="e21cb-110">Konkrétně je vyžadován jeden kořenový adresář, pokud je `x:XData` určena jako zdroj dat XML pro WPF nebo mnoho dalších technologií, které používají zdroje XML pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="e21cb-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="e21cb-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e21cb-111">Optional.</span></span> <span data-ttu-id="e21cb-112">XML, který představuje data XML.</span><span class="sxs-lookup"><span data-stu-id="e21cb-112">XML that represents the XML data.</span></span> <span data-ttu-id="e21cb-113">Libovolný počet prvků může být obsažen jako data elementu a vnořené prvky mohou být obsaženy v jiných prvcích; platí ale obecná pravidla XML.</span><span class="sxs-lookup"><span data-stu-id="e21cb-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e21cb-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e21cb-114">Remarks</span></span>  
 <span data-ttu-id="e21cb-115">Prvky XML v rámci objektu `x:XData` mohou znovu deklarovat všechny možné obory názvů a předpony obsahujícího XMLDOM v rámci dat.</span><span class="sxs-lookup"><span data-stu-id="e21cb-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="e21cb-116">Programový přístup k datům XML a `x:XData` vnitřní typ XAML je možný v .NET Framework služby XAML prostřednictvím třídy <xref:System.Windows.Markup.XData>.</span><span class="sxs-lookup"><span data-stu-id="e21cb-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="e21cb-117">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="e21cb-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="e21cb-118">Objekt `x:XData` je primárně použit jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider>nebo případně jako podřízený objekt vlastnosti <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (v jazyce XAML je obvykle vyjádřen v syntaxi elementu vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="e21cb-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="e21cb-119">Data by obvykle předefinovala základní obor názvů XML v datovém ostrůvku tak, aby byl nový výchozí obor názvů XML (nastavený na prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="e21cb-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="e21cb-120">To je nejjednodušší pro jednoduché datové ostrůvky, protože <xref:System.Windows.Data.Binding.XPath%2A> výrazy, které se používají k odkazování na data a vázání na ně, se můžou vyhnout zahrnutí předpon.</span><span class="sxs-lookup"><span data-stu-id="e21cb-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="e21cb-121">Složitější datové ostrůvky mohou definovat více předpon pro data a použít konkrétní předponu pro obor názvů XML v kořenu.</span><span class="sxs-lookup"><span data-stu-id="e21cb-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="e21cb-122">V tomto případě by měly všechny odkazy na výraz <xref:System.Windows.Data.Binding.XPath%2A> obsahovat příslušnou předponu mapovanou na obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e21cb-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="e21cb-123">Další informace najdete v tématu [Přehled datových vazeb](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e21cb-123">For more information, see [Data Binding Overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="e21cb-124">Technicky `x:XData` lze použít jako obsah libovolné vlastnosti typu <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="e21cb-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="e21cb-125"><xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> je ale jedinou významnou implementací.</span><span class="sxs-lookup"><span data-stu-id="e21cb-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21cb-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e21cb-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="e21cb-127">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="e21cb-127">Data Binding Overview</span></span>](../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e21cb-128">Rozšíření značek datové vazby</span><span class="sxs-lookup"><span data-stu-id="e21cb-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
