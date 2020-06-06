---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855092"
---
# \<namespaceTable>

<span data-ttu-id="142ad-101">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="142ad-101">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="142ad-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="142ad-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="142ad-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="142ad-103">Attributes and elements</span></span>

<span data-ttu-id="142ad-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="142ad-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="142ad-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="142ad-105">Attributes</span></span>

<span data-ttu-id="142ad-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="142ad-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="142ad-107">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="142ad-107">Child elements</span></span>

|     | <span data-ttu-id="142ad-108">Description</span><span class="sxs-lookup"><span data-stu-id="142ad-108">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="142ad-109">Definuje mapování předpony oboru názvů používané pro výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="142ad-109">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="142ad-110">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="142ad-110">Parent elements</span></span>

|     | <span data-ttu-id="142ad-111">Description</span><span class="sxs-lookup"><span data-stu-id="142ad-111">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="142ad-112">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který se <xref:System.ServiceModel.Dispatcher.MessageFilter> má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky definující cílové koncové body, na které se odesílají zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="142ad-112">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="142ad-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="142ad-113">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
