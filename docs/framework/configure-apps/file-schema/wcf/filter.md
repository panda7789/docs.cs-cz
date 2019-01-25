---
title: '&lt;Filtr&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 9fae9a599299fdd8cf1e996593514fc0ef38b6ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645506"
---
# <a name="ltfiltergt"></a><span data-ttu-id="e3a62-102">&lt;Filtr&gt;</span><span class="sxs-lookup"><span data-stu-id="e3a62-102">&lt;filter&gt;</span></span>

<span data-ttu-id="e3a62-103">Definuje směrovací filtr, který určuje typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jako a libovolných podpůrných dat nebo parametrů vyžadovaných filtrem.</span><span class="sxs-lookup"><span data-stu-id="e3a62-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="e3a62-104">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="e3a62-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="e3a62-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3a62-105">Syntax</span></span>  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3a62-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3a62-106">Attributes and elements</span></span>

<span data-ttu-id="e3a62-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3a62-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3a62-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3a62-108">Attributes</span></span>

| <span data-ttu-id="e3a62-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="e3a62-109">Attribute</span></span>  | <span data-ttu-id="e3a62-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e3a62-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="e3a62-111">customType</span><span class="sxs-lookup"><span data-stu-id="e3a62-111">customType</span></span> | <span data-ttu-id="e3a62-112">Řetězec obsahující název plně kvalifikovaný typ vlastního typu, který má být použit jako filtr.</span><span class="sxs-lookup"><span data-stu-id="e3a62-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="e3a62-113">Pokud `filterType` je nastavena na `custom`, tento atribut obsahuje název plně kvalifikovaný typ třídy k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="e3a62-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="e3a62-114">`filterData` může také obsahovat hodnoty, které se použijí při vyhodnocení filtru vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="e3a62-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="e3a62-115">filterData</span><span class="sxs-lookup"><span data-stu-id="e3a62-115">filterData</span></span> | <span data-ttu-id="e3a62-116">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="e3a62-116">A string containing the filter data.</span></span> <span data-ttu-id="e3a62-117">Další informace o tom, jak tento atribut zadán, naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3a62-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="e3a62-118">filterType</span><span class="sxs-lookup"><span data-stu-id="e3a62-118">filterType</span></span> | <span data-ttu-id="e3a62-119">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="e3a62-119">A string containing the filter type.</span></span> <span data-ttu-id="e3a62-120">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="e3a62-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="e3a62-121">Další informace o tom, jak to funguje s `filterData` atributu naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3a62-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="e3a62-122">name</span><span class="sxs-lookup"><span data-stu-id="e3a62-122">name</span></span>       | <span data-ttu-id="e3a62-123">Řetězec obsahující jedinečný název tohoto prvku filtru.</span><span class="sxs-lookup"><span data-stu-id="e3a62-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e3a62-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e3a62-124">Child elements</span></span>

<span data-ttu-id="e3a62-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="e3a62-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3a62-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e3a62-126">Parent elements</span></span>

| <span data-ttu-id="e3a62-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3a62-127">Element</span></span> | <span data-ttu-id="e3a62-128">Popis</span><span class="sxs-lookup"><span data-stu-id="e3a62-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="e3a62-129">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e3a62-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="e3a62-130">Konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="e3a62-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e3a62-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3a62-131">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
