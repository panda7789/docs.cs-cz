---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 3c7e9cb1284ab55c8dd199d9fb47a223698814f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934128"
---
# <a name="routing"></a><span data-ttu-id="aac06-101">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="aac06-101">\<routing></span></span>

<span data-ttu-id="aac06-102">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr.</span><span class="sxs-lookup"><span data-stu-id="aac06-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="aac06-103">[ **\<system.serviceModel>** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="aac06-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="aac06-104">&nbsp;&nbsp; **\<> směrování**</span><span class="sxs-lookup"><span data-stu-id="aac06-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="aac06-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aac06-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aac06-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aac06-106">Attributes and elements</span></span>

<span data-ttu-id="aac06-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aac06-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="aac06-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="aac06-108">Attributes</span></span>

<span data-ttu-id="aac06-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="aac06-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="aac06-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="aac06-110">Child elements</span></span>

|     | <span data-ttu-id="aac06-111">Popis</span><span class="sxs-lookup"><span data-stu-id="aac06-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="aac06-112"> **\<> filtrů**</span><span class="sxs-lookup"><span data-stu-id="aac06-112">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="aac06-113">Obsahuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) MessageFilter bude použit při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="aac06-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="aac06-114"> **\<filterTables >** </span><span class="sxs-lookup"><span data-stu-id="aac06-114">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="aac06-115">Obsahuje mapování mezi směrovacími filtry a cílovými koncovými body k určení koncového bodu, který se má použít, když filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="aac06-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="aac06-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="aac06-116">Parent elements</span></span>

|     | <span data-ttu-id="aac06-117">Popis</span><span class="sxs-lookup"><span data-stu-id="aac06-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="aac06-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="aac06-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="aac06-119">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="aac06-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="aac06-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aac06-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
