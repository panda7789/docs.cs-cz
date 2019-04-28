---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704034"
---
# <a name="filter"></a><span data-ttu-id="516f4-101">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="516f4-101">\<filter></span></span>

<span data-ttu-id="516f4-102">Definuje směrovací filtr, který určuje typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jako a libovolných podpůrných dat nebo parametrů vyžadovaných filtrem.</span><span class="sxs-lookup"><span data-stu-id="516f4-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="516f4-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="516f4-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="516f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="516f4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="516f4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="516f4-105">Attributes and elements</span></span>

<span data-ttu-id="516f4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="516f4-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="516f4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="516f4-107">Attributes</span></span>

| <span data-ttu-id="516f4-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="516f4-108">Attribute</span></span>  | <span data-ttu-id="516f4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="516f4-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="516f4-110">customType</span><span class="sxs-lookup"><span data-stu-id="516f4-110">customType</span></span> | <span data-ttu-id="516f4-111">Řetězec obsahující název plně kvalifikovaný typ vlastního typu, který má být použit jako filtr.</span><span class="sxs-lookup"><span data-stu-id="516f4-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="516f4-112">Pokud `filterType` je nastavena na `custom`, tento atribut obsahuje název plně kvalifikovaný typ třídy k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="516f4-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="516f4-113">`filterData` může také obsahovat hodnoty, které se použijí při vyhodnocení filtru vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="516f4-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="516f4-114">filterData</span><span class="sxs-lookup"><span data-stu-id="516f4-114">filterData</span></span> | <span data-ttu-id="516f4-115">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="516f4-115">A string containing the filter data.</span></span> <span data-ttu-id="516f4-116">Další informace o tom, jak tento atribut zadán, naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="516f4-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="516f4-117">filterType</span><span class="sxs-lookup"><span data-stu-id="516f4-117">filterType</span></span> | <span data-ttu-id="516f4-118">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="516f4-118">A string containing the filter type.</span></span> <span data-ttu-id="516f4-119">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="516f4-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="516f4-120">Další informace o tom, jak to funguje s `filterData` atributu naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="516f4-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="516f4-121">name</span><span class="sxs-lookup"><span data-stu-id="516f4-121">name</span></span>       | <span data-ttu-id="516f4-122">Řetězec obsahující jedinečný název tohoto prvku filtru.</span><span class="sxs-lookup"><span data-stu-id="516f4-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="516f4-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="516f4-123">Child elements</span></span>

<span data-ttu-id="516f4-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="516f4-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="516f4-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="516f4-125">Parent elements</span></span>

| <span data-ttu-id="516f4-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="516f4-126">Element</span></span> | <span data-ttu-id="516f4-127">Popis</span><span class="sxs-lookup"><span data-stu-id="516f4-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="516f4-128">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="516f4-128">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="516f4-129">Konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="516f4-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="516f4-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="516f4-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
