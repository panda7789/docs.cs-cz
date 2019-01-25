---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: fb2b324a2c128b470f1a9a21343408280c5e1862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743241"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="8c5bb-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="8c5bb-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="8c5bb-103">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="8c5bb-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="8c5bb-104">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="8c5bb-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="8c5bb-105">&nbsp;&nbsp;**\<směrování >** </span><span class="sxs-lookup"><span data-stu-id="8c5bb-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="8c5bb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="8c5bb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="8c5bb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c5bb-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c5bb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c5bb-108">Attributes and elements</span></span>

<span data-ttu-id="8c5bb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c5bb-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c5bb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c5bb-110">Attributes</span></span>

<span data-ttu-id="8c5bb-111">Žádná</span><span class="sxs-lookup"><span data-stu-id="8c5bb-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c5bb-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="8c5bb-112">Child elements</span></span>

|     | <span data-ttu-id="8c5bb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8c5bb-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8c5bb-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="8c5bb-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="8c5bb-115">Definuje mapování předpony oboru názvů pro výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="8c5bb-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="8c5bb-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="8c5bb-116">Parent elements</span></span>

|     | <span data-ttu-id="8c5bb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8c5bb-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8c5bb-118">**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="8c5bb-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="8c5bb-119">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="8c5bb-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="8c5bb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c5bb-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
