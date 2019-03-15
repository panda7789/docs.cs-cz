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
ms.openlocfilehash: 68468c3c10fd884cf5fb92160e3cde41dbf7d529
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58030261"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="4211f-102">x:XData – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="4211f-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="4211f-103">Umožňuje umístění datové ostrůvky XML v rámci výrobní XAML.</span><span class="sxs-lookup"><span data-stu-id="4211f-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="4211f-104">Elementy XML v rámci `x:XData` by neměla být zpracována XAML procesorů, jako by šlo část funguje výchozí obor názvů XAML nebo libovolný jiný obor názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="4211f-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="4211f-105">`x:XData` může obsahovat libovolný XML ve správném formátu.</span><span class="sxs-lookup"><span data-stu-id="4211f-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="4211f-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="4211f-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4211f-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="4211f-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="4211f-108">Jeden kořenový element uzavřený dat ostrov.</span><span class="sxs-lookup"><span data-stu-id="4211f-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="4211f-109">Pro většinu konečné spotřebitele se považuje za neplatný kód XML, který nemá jeden kořenový.</span><span class="sxs-lookup"><span data-stu-id="4211f-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="4211f-110">Jeden kořenový je konkrétně vyžadováno, pokud `x:XData` je určený jako XML použitého jako zdroj dat pro WPF nebo mnoho technologií, které používají zdroje XML pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="4211f-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="4211f-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4211f-111">Optional.</span></span> <span data-ttu-id="4211f-112">Soubor XML, který představuje XML data.</span><span class="sxs-lookup"><span data-stu-id="4211f-112">XML that represents the XML data.</span></span> <span data-ttu-id="4211f-113">Libovolný počet prvků, které mohou být obsaženy jako prvek dat a vnořené elementy mohou být obsaženy v dalších prvků; však platí obecná pravidla XML.</span><span class="sxs-lookup"><span data-stu-id="4211f-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4211f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4211f-114">Remarks</span></span>  
 <span data-ttu-id="4211f-115">Elementy XML v rámci `x:XData` objekt lze znovu deklarovat všechny možné obory názvů a předpony obsahující XMLDOM v datech.</span><span class="sxs-lookup"><span data-stu-id="4211f-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="4211f-116">Programový přístup k datům XML a `x:XData` vnitřního typu XAML je možné v rozhraní .NET Framework XAML Services prostřednictvím <xref:System.Windows.Markup.XData> třídy.</span><span class="sxs-lookup"><span data-stu-id="4211f-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="4211f-117">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="4211f-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="4211f-118">`x:XData` Objektu se používá především jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider>, nebo jako podřízený objekt <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> vlastnost (v XAML, to je obvykle vyjádřeny syntax prvku vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="4211f-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="4211f-119">Data by měly předefinovat obvykle základního oboru názvů XML v rámci dat ostrov jako nové výchozí XML obor názvů (nastavenou na prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="4211f-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="4211f-120">Toto je nejjednodušší pro jednoduchou datovou ostrovy, protože <xref:System.Windows.Data.Binding.XPath%2A> výrazy, které se používají k odkazu a vytvořit vazbu na data se můžete vyhnout zahrnutí předpony.</span><span class="sxs-lookup"><span data-stu-id="4211f-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="4211f-121">Komplexnější datové ostrůvky může definovat více předpony pro data a použít konkrétní předponu pro obor názvů XML v kořenovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="4211f-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="4211f-122">V takovém případě všechny <xref:System.Windows.Data.Binding.XPath%2A> výraz odkazuje by měla zahrnovat příslušné mapované na obor názvů předponu.</span><span class="sxs-lookup"><span data-stu-id="4211f-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="4211f-123">Další informace najdete v tématu [přehled datových vazeb](../wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4211f-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="4211f-124">Technicky vzato `x:XData` může sloužit jako obsah libovolnou vlastnost typu <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="4211f-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="4211f-125">Ale <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> pouze viditelného implementaci.</span><span class="sxs-lookup"><span data-stu-id="4211f-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4211f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4211f-126">See also</span></span>
- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="4211f-127">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="4211f-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4211f-128">Rozšíření značek datové vazby</span><span class="sxs-lookup"><span data-stu-id="4211f-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
