---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399965"
---
# \<routing>

<span data-ttu-id="bc0c8-101">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který se <xref:System.ServiceModel.Dispatcher.MessageFilter> má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky definující cílové koncové body, na které se odesílají zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="bc0c8-101">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="bc0c8-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc0c8-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc0c8-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc0c8-103">Attributes and elements</span></span>

<span data-ttu-id="bc0c8-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc0c8-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc0c8-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc0c8-105">Attributes</span></span>

<span data-ttu-id="bc0c8-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="bc0c8-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc0c8-107">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="bc0c8-107">Child elements</span></span>

|     | <span data-ttu-id="bc0c8-108">Description</span><span class="sxs-lookup"><span data-stu-id="bc0c8-108">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="bc0c8-109">Obsahuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) MessageFilter bude použit při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="bc0c8-109">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="bc0c8-110">Obsahuje mapování mezi směrovacími filtry a cílovými koncovými body k určení koncového bodu, který se má použít, když filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="bc0c8-110">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="bc0c8-111">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="bc0c8-111">Parent elements</span></span>

|     | <span data-ttu-id="bc0c8-112">Description</span><span class="sxs-lookup"><span data-stu-id="bc0c8-112">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="bc0c8-113">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="bc0c8-113">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="bc0c8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc0c8-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
