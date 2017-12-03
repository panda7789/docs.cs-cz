---
title: "&lt;filters&gt; – &lt;routing&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9dd9faf63ade725bb8bea12b40390fd30c91973
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="6e5f1-102">&lt;filters&gt; – &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="6e5f1-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="6e5f1-103">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="6e5f1-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="6e5f1-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6e5f1-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="6e5f1-105">&nbsp;&nbsp;[**\<směrování >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="6e5f1-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="6e5f1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="6e5f1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6e5f1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e5f1-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="6e5f1-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e5f1-108">Attributes and elements</span></span>

<span data-ttu-id="6e5f1-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e5f1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e5f1-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e5f1-110">Attributes</span></span>

<span data-ttu-id="6e5f1-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e5f1-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e5f1-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6e5f1-112">Child elements</span></span>

|     | <span data-ttu-id="6e5f1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6e5f1-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6e5f1-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="6e5f1-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="6e5f1-115">Obsahuje směrování filtr, který určuje typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> se použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="6e5f1-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6e5f1-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6e5f1-116">Parent elements</span></span>

|     | <span data-ttu-id="6e5f1-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6e5f1-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6e5f1-118">**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="6e5f1-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="6e5f1-119">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="6e5f1-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6e5f1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e5f1-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
