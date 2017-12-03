---
title: "&lt;směrování&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cbe682ef9f7bca25ab4f5089a295ada9a00a8bc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="7d2a8-102">&lt;směrování&gt;</span><span class="sxs-lookup"><span data-stu-id="7d2a8-102">&lt;routing&gt;</span></span>

<span data-ttu-id="7d2a8-103">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="7d2a8-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="7d2a8-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7d2a8-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="7d2a8-105">&nbsp;&nbsp;**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="7d2a8-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7d2a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d2a8-106">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String" 
               filterName="String" 
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d2a8-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d2a8-107">Attributes and elements</span></span>

<span data-ttu-id="7d2a8-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d2a8-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d2a8-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d2a8-109">Attributes</span></span>

<span data-ttu-id="7d2a8-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d2a8-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d2a8-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7d2a8-111">Child elements</span></span>

|     | <span data-ttu-id="7d2a8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7d2a8-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7d2a8-113">**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="7d2a8-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="7d2a8-114">Obsahuje sadu směrování filtry, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter se použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="7d2a8-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="7d2a8-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="7d2a8-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="7d2a8-116">Obsahuje mapování mezi směrování filtry a cílové koncové body k určení kterému koncovému bodu pro použití při odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="7d2a8-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="7d2a8-117">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="7d2a8-117">Parent elements</span></span>

|     | <span data-ttu-id="7d2a8-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7d2a8-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="7d2a8-119">**\<systém. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="7d2a8-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="7d2a8-120">Kořenový element všechny konfigurační prvky WCF.</span><span class="sxs-lookup"><span data-stu-id="7d2a8-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="7d2a8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d2a8-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
