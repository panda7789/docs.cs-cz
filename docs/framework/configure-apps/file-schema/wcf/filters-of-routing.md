---
title: '&lt;filters&gt; – &lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 468c10bc06b60f80ce93cf413c02582fe3861f70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704430"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="9064c-102">&lt;filters&gt; – &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="9064c-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="9064c-103">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="9064c-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="9064c-104">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9064c-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="9064c-105">&nbsp;&nbsp;[**\<směrování >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="9064c-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="9064c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="9064c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="9064c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9064c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9064c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9064c-108">Attributes and elements</span></span>

<span data-ttu-id="9064c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9064c-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9064c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9064c-110">Attributes</span></span>

<span data-ttu-id="9064c-111">Žádná</span><span class="sxs-lookup"><span data-stu-id="9064c-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9064c-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9064c-112">Child elements</span></span>

|     | <span data-ttu-id="9064c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9064c-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9064c-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="9064c-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="9064c-115">Obsahuje směrovací filtr, který určuje typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> se použije při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="9064c-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="9064c-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="9064c-116">Parent elements</span></span>

|     | <span data-ttu-id="9064c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9064c-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9064c-118">**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="9064c-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="9064c-119">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="9064c-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9064c-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9064c-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
