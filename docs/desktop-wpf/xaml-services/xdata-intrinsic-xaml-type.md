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
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071540"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="89132-102">x:XData – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="89132-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="89132-103">Umožňuje umístění datových ostrovů XML v rámci výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="89132-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="89132-104">Xml prvky uvnitř `x:XData` by neměly být zpracovány procesory XAML, jako by byly součástí výchozího oboru názvů XAML nebo jiného oboru názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="89132-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="89132-105">`x:XData`může obsahovat libovolný dobře formátovaný XML.</span><span class="sxs-lookup"><span data-stu-id="89132-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="89132-106">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="89132-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="89132-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="89132-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="89132-108">Jediný kořenový prvek uzavřeného datového ostrova.</span><span class="sxs-lookup"><span data-stu-id="89132-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="89132-109">Pro většinu případných spotřebitelů xml, který nemá jeden kořen je považován za neplatný.</span><span class="sxs-lookup"><span data-stu-id="89132-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="89132-110">Zejména jeden kořen je vyžadován, `x:XData` pokud je určen jako zdroj dat XML pro WPF nebo mnoho dalších technologií, které používají zdroje XML pro datové vazby.</span><span class="sxs-lookup"><span data-stu-id="89132-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="89132-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="89132-111">Optional.</span></span> <span data-ttu-id="89132-112">XML, který představuje data XML.</span><span class="sxs-lookup"><span data-stu-id="89132-112">XML that represents the XML data.</span></span> <span data-ttu-id="89132-113">Libovolný počet prvků může být obsažen jako data prvku a vnořené prvky mohou být obsaženy v jiných prvcích; platí však obecná pravidla XML.</span><span class="sxs-lookup"><span data-stu-id="89132-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89132-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89132-114">Remarks</span></span>

<span data-ttu-id="89132-115">Elementy XML `x:XData` v objektu mohou znovu deklarovat všechny možné obory názvů a předpony obsahujícího objektu XMLDOM v rámci dat.</span><span class="sxs-lookup"><span data-stu-id="89132-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="89132-116">Programový přístup k datům XML a `x:XData` vnitřnímu typu XAML je možný <xref:System.Windows.Markup.XData> ve službách .NET XAML prostřednictvím třídy.</span><span class="sxs-lookup"><span data-stu-id="89132-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="89132-117">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="89132-117">WPF Usage Notes</span></span>

<span data-ttu-id="89132-118">Objekt `x:XData` se používá především jako podřízený <xref:System.Windows.Data.XmlDataProvider>objekt , nebo alternativně jako <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> podřízený objekt vlastnosti (v XAML, to je obvykle vyjádřeno v syntaxi elementu vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="89132-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="89132-119">Data by měla obvykle předefinovat základní obor názvů XML v rámci datového ostrova jako nový výchozí obor názvů XML (nastavený na prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="89132-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="89132-120">To je nejjednodušší pro jednoduché <xref:System.Windows.Data.Binding.XPath%2A> datové ostrovy, protože výrazy, které se používají k odkazování a vazbě na data, se mohou vyhnout zahrnutí předpon.</span><span class="sxs-lookup"><span data-stu-id="89132-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="89132-121">Složitější datové ostrovy mohou definovat více předpon pro data a použít určitou předponu pro obor názvů XML v kořenovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="89132-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="89132-122">V takovém případě <xref:System.Windows.Data.Binding.XPath%2A> by všechny odkazy na výrazy měly obsahovat příslušnou předponu mapovanou oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="89132-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="89132-123">Další informace naleznete v [tématu Přehled datových vazeb](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="89132-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="89132-124">Technicky, `x:XData` může být použit jako obsah <xref:System.Xml.Serialization.IXmlSerializable>jakékoliv vlastnosti typu .</span><span class="sxs-lookup"><span data-stu-id="89132-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="89132-125">Je <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> však jedinou významnou implementací.</span><span class="sxs-lookup"><span data-stu-id="89132-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="89132-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="89132-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="89132-127">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="89132-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="89132-128">Rozšíření značek připojení</span><span class="sxs-lookup"><span data-stu-id="89132-128">Binding Markup Extension</span></span>](../../framework/wpf/advanced/binding-markup-extension.md)
