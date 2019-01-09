---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 55b5565ffe9d3e9e7ea41d2a2e2f380490be1781
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151420"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="33f58-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="33f58-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="33f58-103">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="33f58-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="33f58-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="33f58-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="33f58-105">&nbsp;&nbsp;**\<směrování >** </span><span class="sxs-lookup"><span data-stu-id="33f58-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="33f58-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="33f58-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="33f58-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33f58-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33f58-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33f58-108">Attributes and elements</span></span>

<span data-ttu-id="33f58-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="33f58-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="33f58-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="33f58-110">Attributes</span></span>

<span data-ttu-id="33f58-111">Žádná</span><span class="sxs-lookup"><span data-stu-id="33f58-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="33f58-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="33f58-112">Child elements</span></span>

|     | <span data-ttu-id="33f58-113">Popis</span><span class="sxs-lookup"><span data-stu-id="33f58-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="33f58-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="33f58-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="33f58-115">Definuje mapování předpony oboru názvů pro výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="33f58-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="33f58-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="33f58-116">Parent elements</span></span>

|     | <span data-ttu-id="33f58-117">Popis</span><span class="sxs-lookup"><span data-stu-id="33f58-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="33f58-118">**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="33f58-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="33f58-119">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="33f58-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="33f58-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33f58-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
