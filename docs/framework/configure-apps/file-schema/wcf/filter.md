---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855260"
---
# \<filter>

<span data-ttu-id="28d1e-101">Definuje filtr směrování, který určuje typ Windows Communication Foundation (WCF), <xref:System.ServiceModel.Dispatcher.MessageFilter> který se má použít při vyhodnocování příchozích zpráv, a také všechna podpůrná data nebo parametry, které filtr vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="28d1e-101">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="28d1e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28d1e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28d1e-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28d1e-103">Attributes and elements</span></span>

<span data-ttu-id="28d1e-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28d1e-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="28d1e-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="28d1e-105">Attributes</span></span>

| <span data-ttu-id="28d1e-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="28d1e-106">Attribute</span></span>  | <span data-ttu-id="28d1e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="28d1e-107">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="28d1e-108">customType</span><span class="sxs-lookup"><span data-stu-id="28d1e-108">customType</span></span> | <span data-ttu-id="28d1e-109">Řetězec obsahující plně kvalifikovaný název typu vlastního typu, který má být použit jako filtr.</span><span class="sxs-lookup"><span data-stu-id="28d1e-109">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="28d1e-110">Pokud `filterType` je nastaven na `custom` , tento atribut obsahuje plně kvalifikovaný název třídy, která se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="28d1e-110">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="28d1e-111">`filterData`může také obsahovat hodnoty, které mají být použity během hodnocení vlastního filtru typu.</span><span class="sxs-lookup"><span data-stu-id="28d1e-111">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="28d1e-112">fulltextových</span><span class="sxs-lookup"><span data-stu-id="28d1e-112">filterData</span></span> | <span data-ttu-id="28d1e-113">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="28d1e-113">A string containing the filter data.</span></span> <span data-ttu-id="28d1e-114">Další informace o tom, jak zadat tento atribut, naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .</span><span class="sxs-lookup"><span data-stu-id="28d1e-114">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="28d1e-115">filterType</span><span class="sxs-lookup"><span data-stu-id="28d1e-115">filterType</span></span> | <span data-ttu-id="28d1e-116">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="28d1e-116">A string containing the filter type.</span></span> <span data-ttu-id="28d1e-117">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="28d1e-117">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="28d1e-118">Další informace o tom, jak to funguje s `filterData` atributem, naleznete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .</span><span class="sxs-lookup"><span data-stu-id="28d1e-118">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="28d1e-119">name</span><span class="sxs-lookup"><span data-stu-id="28d1e-119">name</span></span>       | <span data-ttu-id="28d1e-120">Řetězec obsahující jedinečný název tohoto prvku filtru.</span><span class="sxs-lookup"><span data-stu-id="28d1e-120">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="28d1e-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="28d1e-121">Child elements</span></span>

<span data-ttu-id="28d1e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="28d1e-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="28d1e-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="28d1e-123">Parent elements</span></span>

| <span data-ttu-id="28d1e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="28d1e-124">Element</span></span> | <span data-ttu-id="28d1e-125">Description</span><span class="sxs-lookup"><span data-stu-id="28d1e-125">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="28d1e-126">Konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který se <xref:System.ServiceModel.Dispatcher.MessageFilter> má použít při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="28d1e-126">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="28d1e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="28d1e-127">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
