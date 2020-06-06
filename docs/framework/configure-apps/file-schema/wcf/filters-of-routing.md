---
title: <filters> z <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855246"
---
# <a name="filters-of-routing"></a><span data-ttu-id="3a22e-102">\<filters> z \<routing></span><span class="sxs-lookup"><span data-stu-id="3a22e-102">\<filters> of \<routing></span></span>

<span data-ttu-id="3a22e-103">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který se <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="3a22e-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="3a22e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a22e-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a22e-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3a22e-105">Attributes and elements</span></span>

<span data-ttu-id="3a22e-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3a22e-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a22e-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3a22e-107">Attributes</span></span>

<span data-ttu-id="3a22e-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="3a22e-108">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a22e-109">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="3a22e-109">Child elements</span></span>

|     | <span data-ttu-id="3a22e-110">Description</span><span class="sxs-lookup"><span data-stu-id="3a22e-110">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="3a22e-111">Obsahuje filtr směrování, který určuje typ Windows Communication Foundation (WCF), který <xref:System.ServiceModel.Dispatcher.MessageFilter> se použije při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="3a22e-111">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="3a22e-112">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="3a22e-112">Parent elements</span></span>

|     | <span data-ttu-id="3a22e-113">Description</span><span class="sxs-lookup"><span data-stu-id="3a22e-113">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="3a22e-114">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který se <xref:System.ServiceModel.Dispatcher.MessageFilter> má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky definující cílové koncové body, na které se odesílají zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="3a22e-114">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3a22e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a22e-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
