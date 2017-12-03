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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af2095289d5f711733c71238b855c685114d1997
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltergt"></a><span data-ttu-id="7586f-102">&lt;Filtr&gt;</span><span class="sxs-lookup"><span data-stu-id="7586f-102">&lt;filter&gt;</span></span>

<span data-ttu-id="7586f-103">Definuje filtr, směrování, která určuje typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jako a všechny podpůrné data nebo parametrů požadovaných filtr.</span><span class="sxs-lookup"><span data-stu-id="7586f-103">Defines a routing filter, which determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="7586f-104">\<system.serviceModel > \<směrování > \<filtry > \<filtru ></span><span class="sxs-lookup"><span data-stu-id="7586f-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="7586f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7586f-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7586f-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7586f-106">Attributes and elements</span></span>

<span data-ttu-id="7586f-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7586f-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7586f-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="7586f-108">Attributes</span></span>

| <span data-ttu-id="7586f-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="7586f-109">Attribute</span></span>  | <span data-ttu-id="7586f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7586f-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="7586f-111">customType</span><span class="sxs-lookup"><span data-stu-id="7586f-111">customType</span></span> | <span data-ttu-id="7586f-112">Řetězec obsahující typ plně kvalifikovaný název vlastního typu, který se má použít jako filtr.</span><span class="sxs-lookup"><span data-stu-id="7586f-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="7586f-113">Pokud `filterType` je nastaven na `custom`, tento atribut obsahuje typ plně kvalifikovaný název třídy pro vytvoření.</span><span class="sxs-lookup"><span data-stu-id="7586f-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="7586f-114">`filterData`může také obsahovat hodnot použitých během vyhodnocení vlastního typu filtru.</span><span class="sxs-lookup"><span data-stu-id="7586f-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="7586f-115">fulltextových dat filtru</span><span class="sxs-lookup"><span data-stu-id="7586f-115">filterData</span></span> | <span data-ttu-id="7586f-116">Řetězec obsahující data filtru.</span><span class="sxs-lookup"><span data-stu-id="7586f-116">A string containing the filter data.</span></span> <span data-ttu-id="7586f-117">Další informace o tom, jak zadat Tento atribut najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="7586f-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="7586f-118">filterType</span><span class="sxs-lookup"><span data-stu-id="7586f-118">filterType</span></span> | <span data-ttu-id="7586f-119">Řetězec obsahující typ filtru.</span><span class="sxs-lookup"><span data-stu-id="7586f-119">A string containing the filter type.</span></span> <span data-ttu-id="7586f-120">Tento atribut je <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="7586f-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="7586f-121">Další informace o tom, jak to funguje s `filterData` atributů najdete v tématu <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="7586f-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="7586f-122">name</span><span class="sxs-lookup"><span data-stu-id="7586f-122">name</span></span>       | <span data-ttu-id="7586f-123">Řetězec obsahující jedinečný název tohoto elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="7586f-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="7586f-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7586f-124">Child elements</span></span>

<span data-ttu-id="7586f-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="7586f-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7586f-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="7586f-126">Parent elements</span></span>

| <span data-ttu-id="7586f-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="7586f-127">Element</span></span> | <span data-ttu-id="7586f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="7586f-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="7586f-129">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="7586f-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="7586f-130">Konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="7586f-130">A configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="7586f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="7586f-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
