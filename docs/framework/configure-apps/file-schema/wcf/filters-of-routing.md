---
title: '&lt;filters&gt; – &lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 9f0fa9bf51d264346738172f57a8efca7950fdb7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="e9c84-102">&lt;filters&gt; – &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="e9c84-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="e9c84-103">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="e9c84-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="e9c84-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e9c84-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="e9c84-105">&nbsp;&nbsp;[**\<směrování >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="e9c84-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="e9c84-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="e9c84-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e9c84-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9c84-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9c84-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9c84-108">Attributes and elements</span></span>

<span data-ttu-id="e9c84-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9c84-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9c84-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9c84-110">Attributes</span></span>

<span data-ttu-id="e9c84-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="e9c84-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9c84-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e9c84-112">Child elements</span></span>

|     | <span data-ttu-id="e9c84-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e9c84-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e9c84-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="e9c84-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="e9c84-115">Obsahuje směrování filtr, který určuje typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> se použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="e9c84-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="e9c84-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e9c84-116">Parent elements</span></span>

|     | <span data-ttu-id="e9c84-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e9c84-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e9c84-118">**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="e9c84-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="e9c84-119">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k Pokud filtr odpovídá odesílat zprávy.</span><span class="sxs-lookup"><span data-stu-id="e9c84-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e9c84-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9c84-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
