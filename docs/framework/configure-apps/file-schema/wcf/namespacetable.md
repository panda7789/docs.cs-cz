---
title: '&lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28bbeae9d1dbe43ad787c391ae461b44a8e85147
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="11b9d-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="11b9d-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="11b9d-103">Představuje konfigurační oddíl pro definování sady elementů, které obsahují obor názvů pro mapování předpony, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="11b9d-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="11b9d-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="11b9d-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="11b9d-105">&nbsp;&nbsp;**\<směrování >** </span><span class="sxs-lookup"><span data-stu-id="11b9d-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="11b9d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="11b9d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="11b9d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11b9d-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="11b9d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11b9d-108">Attributes and elements</span></span>

<span data-ttu-id="11b9d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11b9d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="11b9d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="11b9d-110">Attributes</span></span>

<span data-ttu-id="11b9d-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="11b9d-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="11b9d-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="11b9d-112">Child elements</span></span>

|     | <span data-ttu-id="11b9d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="11b9d-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="11b9d-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="11b9d-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="11b9d-115">Definuje mapování předpony oboru názvů používá pro výrazech XPath.</span><span class="sxs-lookup"><span data-stu-id="11b9d-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="11b9d-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="11b9d-116">Parent elements</span></span>

|     | <span data-ttu-id="11b9d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="11b9d-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="11b9d-118">**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="11b9d-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="11b9d-119">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="11b9d-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="11b9d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="11b9d-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
