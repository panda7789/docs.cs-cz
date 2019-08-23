---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 68de255b9f11dc4377159d1cc3efa575633db316
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918899"
---
# <a name="filter"></a><span data-ttu-id="65c60-101">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="65c60-101">\<filter></span></span>

<span data-ttu-id="65c60-102">Definuje filtr směrování, který určuje typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, a také všechna podpůrná data nebo parametry, které filtr vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="65c60-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="65c60-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="65c60-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="65c60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65c60-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65c60-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="65c60-105">Attributes and elements</span></span>

<span data-ttu-id="65c60-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="65c60-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="65c60-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="65c60-107">Attributes</span></span>

| <span data-ttu-id="65c60-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="65c60-108">Attribute</span></span>  | <span data-ttu-id="65c60-109">Popis</span><span class="sxs-lookup"><span data-stu-id="65c60-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="65c60-110">customType</span><span class="sxs-lookup"><span data-stu-id="65c60-110">customType</span></span> | <span data-ttu-id="65c60-111">Řetězec obsahující plně kvalifikovaný název typu vlastního typu, který má být použit jako filtr.</span><span class="sxs-lookup"><span data-stu-id="65c60-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="65c60-112">Pokud `filterType` je nastaven na `custom`, tento atribut obsahuje plně kvalifikovaný název třídy, která se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="65c60-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="65c60-113">`filterData`může také obsahovat hodnoty, které mají být použity během hodnocení vlastního filtru typu.</span><span class="sxs-lookup"><span data-stu-id="65c60-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="65c60-114">filterData</span><span class="sxs-lookup"><span data-stu-id="65c60-114">filterData</span></span> | <span data-ttu-id="65c60-115">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="65c60-115">A string containing the filter data.</span></span> <span data-ttu-id="65c60-116">Další informace o tom, jak zadat tento atribut, naleznete <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="65c60-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="65c60-117">filterType</span><span class="sxs-lookup"><span data-stu-id="65c60-117">filterType</span></span> | <span data-ttu-id="65c60-118">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="65c60-118">A string containing the filter type.</span></span> <span data-ttu-id="65c60-119">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="65c60-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="65c60-120">Další informace o tom, jak to funguje s `filterData` atributem, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="65c60-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="65c60-121">name</span><span class="sxs-lookup"><span data-stu-id="65c60-121">name</span></span>       | <span data-ttu-id="65c60-122">Řetězec obsahující jedinečný název tohoto prvku filtru.</span><span class="sxs-lookup"><span data-stu-id="65c60-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="65c60-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="65c60-123">Child elements</span></span>

<span data-ttu-id="65c60-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="65c60-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65c60-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="65c60-125">Parent elements</span></span>

| <span data-ttu-id="65c60-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="65c60-126">Element</span></span> | <span data-ttu-id="65c60-127">Popis</span><span class="sxs-lookup"><span data-stu-id="65c60-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="65c60-128">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="65c60-128">\<routing></span></span>](routing.md) | <span data-ttu-id="65c60-129">Konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="65c60-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="65c60-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65c60-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
