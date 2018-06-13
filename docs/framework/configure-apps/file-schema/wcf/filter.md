---
title: '&lt;Filtr&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 93d47fc6b25a75eedae43cd70582abc863a74e6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747207"
---
# <a name="ltfiltergt"></a><span data-ttu-id="24b88-102">&lt;Filtr&gt;</span><span class="sxs-lookup"><span data-stu-id="24b88-102">&lt;filter&gt;</span></span>

<span data-ttu-id="24b88-103">Definuje filtr, směrování, která určuje typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jako a všechny podpůrné data nebo parametrů požadovaných filtr.</span><span class="sxs-lookup"><span data-stu-id="24b88-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="24b88-104">\<system.serviceModel > \<směrování > \<filtry > \<filtru ></span><span class="sxs-lookup"><span data-stu-id="24b88-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="24b88-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24b88-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="24b88-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="24b88-106">Attributes and elements</span></span>

<span data-ttu-id="24b88-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="24b88-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="24b88-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="24b88-108">Attributes</span></span>

| <span data-ttu-id="24b88-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="24b88-109">Attribute</span></span>  | <span data-ttu-id="24b88-110">Popis</span><span class="sxs-lookup"><span data-stu-id="24b88-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="24b88-111">customType</span><span class="sxs-lookup"><span data-stu-id="24b88-111">customType</span></span> | <span data-ttu-id="24b88-112">Řetězec obsahující typ plně kvalifikovaný název vlastního typu, který se má použít jako filtr.</span><span class="sxs-lookup"><span data-stu-id="24b88-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="24b88-113">Pokud `filterType` je nastaven na `custom`, tento atribut obsahuje typ plně kvalifikovaný název třídy pro vytvoření.</span><span class="sxs-lookup"><span data-stu-id="24b88-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="24b88-114">`filterData` může také obsahovat hodnot použitých během vyhodnocení vlastního typu filtru.</span><span class="sxs-lookup"><span data-stu-id="24b88-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="24b88-115">fulltextových dat filtru</span><span class="sxs-lookup"><span data-stu-id="24b88-115">filterData</span></span> | <span data-ttu-id="24b88-116">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="24b88-116">A string containing the filter data.</span></span> <span data-ttu-id="24b88-117">Další informace o tom, jak zadat Tento atribut najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="24b88-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="24b88-118">filterType</span><span class="sxs-lookup"><span data-stu-id="24b88-118">filterType</span></span> | <span data-ttu-id="24b88-119">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="24b88-119">A string containing the filter type.</span></span> <span data-ttu-id="24b88-120">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="24b88-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="24b88-121">Další informace o tom, jak to funguje s `filterData` atributů najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="24b88-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="24b88-122">name</span><span class="sxs-lookup"><span data-stu-id="24b88-122">name</span></span>       | <span data-ttu-id="24b88-123">Řetězec obsahující jedinečný název tohoto elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="24b88-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="24b88-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="24b88-124">Child elements</span></span>

<span data-ttu-id="24b88-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="24b88-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="24b88-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="24b88-126">Parent elements</span></span>

| <span data-ttu-id="24b88-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="24b88-127">Element</span></span> | <span data-ttu-id="24b88-128">Popis</span><span class="sxs-lookup"><span data-stu-id="24b88-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="24b88-129">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="24b88-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="24b88-130">Konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="24b88-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="24b88-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="24b88-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
