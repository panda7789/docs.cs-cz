---
title: '&lt;Filtr&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 86ae428eb29750a348c353a998116f8965b9bb41
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltergt"></a><span data-ttu-id="6d409-102">&lt;Filtr&gt;</span><span class="sxs-lookup"><span data-stu-id="6d409-102">&lt;filter&gt;</span></span>

<span data-ttu-id="6d409-103">Definuje filtr, směrování, která určuje typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jako a všechny podpůrné data nebo parametrů požadovaných filtr.</span><span class="sxs-lookup"><span data-stu-id="6d409-103">Defines a routing filter, which determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="6d409-104">\<system.serviceModel > \<směrování > \<filtry > \<filtru ></span><span class="sxs-lookup"><span data-stu-id="6d409-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="6d409-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d409-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="6d409-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d409-106">Attributes and elements</span></span>

<span data-ttu-id="6d409-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d409-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d409-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d409-108">Attributes</span></span>

| <span data-ttu-id="6d409-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="6d409-109">Attribute</span></span>  | <span data-ttu-id="6d409-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6d409-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="6d409-111">customType</span><span class="sxs-lookup"><span data-stu-id="6d409-111">customType</span></span> | <span data-ttu-id="6d409-112">Řetězec obsahující typ plně kvalifikovaný název vlastního typu, který se má použít jako filtr.</span><span class="sxs-lookup"><span data-stu-id="6d409-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="6d409-113">Pokud `filterType` je nastaven na `custom`, tento atribut obsahuje typ plně kvalifikovaný název třídy pro vytvoření.</span><span class="sxs-lookup"><span data-stu-id="6d409-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="6d409-114">`filterData`může také obsahovat hodnot použitých během vyhodnocení vlastního typu filtru.</span><span class="sxs-lookup"><span data-stu-id="6d409-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="6d409-115">fulltextových dat filtru</span><span class="sxs-lookup"><span data-stu-id="6d409-115">filterData</span></span> | <span data-ttu-id="6d409-116">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="6d409-116">A string containing the filter data.</span></span> <span data-ttu-id="6d409-117">Další informace o tom, jak zadat Tento atribut najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d409-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="6d409-118">filterType</span><span class="sxs-lookup"><span data-stu-id="6d409-118">filterType</span></span> | <span data-ttu-id="6d409-119">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="6d409-119">A string containing the filter type.</span></span> <span data-ttu-id="6d409-120">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="6d409-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="6d409-121">Další informace o tom, jak to funguje s `filterData` atributů najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d409-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="6d409-122">name</span><span class="sxs-lookup"><span data-stu-id="6d409-122">name</span></span>       | <span data-ttu-id="6d409-123">Řetězec obsahující jedinečný název tohoto elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="6d409-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="6d409-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6d409-124">Child elements</span></span>

<span data-ttu-id="6d409-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d409-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6d409-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6d409-126">Parent elements</span></span>

| <span data-ttu-id="6d409-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d409-127">Element</span></span> | <span data-ttu-id="6d409-128">Popis</span><span class="sxs-lookup"><span data-stu-id="6d409-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="6d409-129">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="6d409-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="6d409-130">Konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="6d409-130">A configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6d409-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d409-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
