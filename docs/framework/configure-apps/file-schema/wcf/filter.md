---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855260"
---
# <a name="filter"></a><span data-ttu-id="12d47-101">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="12d47-101">\<filter></span></span>

<span data-ttu-id="12d47-102">Definuje filtr směrování, který určuje typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, a také všechna podpůrná data nebo parametry, které filtr vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="12d47-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="12d47-103">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="12d47-103">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="12d47-104">&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="12d47-104">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="12d47-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtrů**](filters-of-routing.md)</span><span class="sxs-lookup"><span data-stu-id="12d47-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)</span></span>\
<span data-ttu-id="12d47-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtrovat >**</span><span class="sxs-lookup"><span data-stu-id="12d47-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d47-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12d47-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12d47-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12d47-108">Attributes and elements</span></span>

<span data-ttu-id="12d47-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="12d47-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="12d47-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="12d47-110">Attributes</span></span>

| <span data-ttu-id="12d47-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="12d47-111">Attribute</span></span>  | <span data-ttu-id="12d47-112">Popis</span><span class="sxs-lookup"><span data-stu-id="12d47-112">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="12d47-113">customType</span><span class="sxs-lookup"><span data-stu-id="12d47-113">customType</span></span> | <span data-ttu-id="12d47-114">Řetězec obsahující plně kvalifikovaný název typu vlastního typu, který má být použit jako filtr.</span><span class="sxs-lookup"><span data-stu-id="12d47-114">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="12d47-115">Pokud `filterType` je nastaven na `custom`, tento atribut obsahuje plně kvalifikovaný název třídy, která se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="12d47-115">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="12d47-116">`filterData`může také obsahovat hodnoty, které mají být použity během hodnocení vlastního filtru typu.</span><span class="sxs-lookup"><span data-stu-id="12d47-116">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="12d47-117">filterData</span><span class="sxs-lookup"><span data-stu-id="12d47-117">filterData</span></span> | <span data-ttu-id="12d47-118">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="12d47-118">A string containing the filter data.</span></span> <span data-ttu-id="12d47-119">Další informace o tom, jak zadat tento atribut, naleznete <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="12d47-119">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="12d47-120">filterType</span><span class="sxs-lookup"><span data-stu-id="12d47-120">filterType</span></span> | <span data-ttu-id="12d47-121">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="12d47-121">A string containing the filter type.</span></span> <span data-ttu-id="12d47-122">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="12d47-122">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="12d47-123">Další informace o tom, jak to funguje s `filterData` atributem, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="12d47-123">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="12d47-124">name</span><span class="sxs-lookup"><span data-stu-id="12d47-124">name</span></span>       | <span data-ttu-id="12d47-125">Řetězec obsahující jedinečný název tohoto prvku filtru.</span><span class="sxs-lookup"><span data-stu-id="12d47-125">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="12d47-126">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="12d47-126">Child elements</span></span>

<span data-ttu-id="12d47-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="12d47-127">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12d47-128">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="12d47-128">Parent elements</span></span>

| <span data-ttu-id="12d47-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="12d47-129">Element</span></span> | <span data-ttu-id="12d47-130">Popis</span><span class="sxs-lookup"><span data-stu-id="12d47-130">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="12d47-131">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="12d47-131">\<routing></span></span>](routing.md) | <span data-ttu-id="12d47-132">Konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="12d47-132">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="12d47-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12d47-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
