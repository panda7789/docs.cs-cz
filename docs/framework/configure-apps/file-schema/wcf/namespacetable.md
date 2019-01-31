---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: ee7a0c23adca883af279addf9d1f221bd4056d00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269572"
---
# <a name="namespacetable"></a><span data-ttu-id="dced2-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="dced2-101">\<namespaceTable></span></span>

<span data-ttu-id="dced2-102">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="dced2-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="dced2-103">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="dced2-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="dced2-104">&nbsp;&nbsp;**\<směrování >** </span><span class="sxs-lookup"><span data-stu-id="dced2-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="dced2-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="dced2-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="dced2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dced2-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dced2-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dced2-107">Attributes and elements</span></span>

<span data-ttu-id="dced2-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dced2-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dced2-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="dced2-109">Attributes</span></span>

<span data-ttu-id="dced2-110">Žádná</span><span class="sxs-lookup"><span data-stu-id="dced2-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="dced2-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="dced2-111">Child elements</span></span>

|     | <span data-ttu-id="dced2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dced2-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="dced2-113">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="dced2-113">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="dced2-114">Definuje mapování předpony oboru názvů pro výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="dced2-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="dced2-115">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="dced2-115">Parent elements</span></span>

|     | <span data-ttu-id="dced2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="dced2-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="dced2-117">**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="dced2-117">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="dced2-118">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="dced2-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="dced2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dced2-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
