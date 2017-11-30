---
title: "x:XData – vnitřní typ jazyka XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: "17"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 3e448c28be6515748254e267b70f3c898b9226a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="1e4e5-102">x:XData – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="1e4e5-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="1e4e5-103">Umožňuje umístění XML datové ostrůvky v produkční XAML.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="1e4e5-104">Elementy XML v rámci `x:XData` by neměla být zpracována XAML procesorů, jako by byly součástí výchozí funguje oboru názvů jazyka XAML nebo jakékoli jiné oboru názvů jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="1e4e5-105">`x:XData`může obsahovat libovolný ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="1e4e5-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="1e4e5-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1e4e5-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="1e4e5-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="1e4e5-108">Jeden kořenový element island závorkách data.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="1e4e5-109">Pro většinu případné příjemci považuje za neplatný kód XML, který nemá jeden kořenový.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="1e4e5-110">Konkrétně je jeden kořenový povinný, pokud `x:XData` slouží jako zdroj dat XML pro WPF nebo mnoha jiných technologií, využívající zdroje XML pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="1e4e5-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-111">Optional.</span></span> <span data-ttu-id="1e4e5-112">Soubor XML, který představuje XML data.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-112">XML that represents the XML data.</span></span> <span data-ttu-id="1e4e5-113">Jako datový element může obsahovat libovolný počet elementů a vnořených elementů může obsahovat další prvky; Obecná pravidla XML však použít.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e4e5-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e4e5-114">Remarks</span></span>  
 <span data-ttu-id="1e4e5-115">Elementy XML v rámci `x:XData` objekt lze znovu deklarovat všechny možné obory názvů a předpony obsahující XMLDOM v rámci data.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="1e4e5-116">Programový přístup k datům XML a `x:XData` vnitřní typ jazyka XAML je možné v rozhraní .NET Framework XAML Services prostřednictvím <xref:System.Windows.Markup.XData> třídy.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="1e4e5-117">Poznámky pro použití WPF</span><span class="sxs-lookup"><span data-stu-id="1e4e5-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="1e4e5-118">`x:XData` Objekt primárně slouží jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider>, nebo případně jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> vlastnost (v jazyce XAML, to je obvykle vyjádřena v syntaxi element vlastnost).</span><span class="sxs-lookup"><span data-stu-id="1e4e5-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="1e4e5-119">Data by měl obvykle znovu definovat základní obor názvů XML v rámci island data jako novou výchozí obor názvů XML (nastavit na prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="1e4e5-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="1e4e5-120">Toto je nejjednodušší pro jednoduché datové ostrovy, protože <xref:System.Windows.Data.Binding.XPath%2A> výrazy, které se používají k odkazu a vytvoření vazby na data se můžete vyhnout zahrnutí předpony.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="1e4e5-121">Komplexnější datové ostrůvky může definovat více předpon pro data a používat konkrétní předponu pro obor názvů XML v kořenovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="1e4e5-122">V takovém případě všechny <xref:System.Windows.Data.Binding.XPath%2A> výraz odkazy by měla obsahovat předponu odpovídající mapované na obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="1e4e5-123">Další informace najdete v tématu [přehled vazby dat](../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e4e5-123">For more information, see [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="1e4e5-124">Technicky `x:XData` lze použít jako obsah žádnou vlastnost typu <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="1e4e5-125">Ale <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> je pouze viditelného implementace.</span><span class="sxs-lookup"><span data-stu-id="1e4e5-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4e5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e4e5-126">See Also</span></span>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [<span data-ttu-id="1e4e5-127">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="1e4e5-127">Data Binding Overview</span></span>](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="1e4e5-128">Vazby – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="1e4e5-128">Binding Markup Extension</span></span>](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
