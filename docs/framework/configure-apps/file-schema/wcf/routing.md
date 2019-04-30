---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: cc7c1a64f9481a7ab41cf35241ade04bd690dae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786383"
---
# <a name="routing"></a><span data-ttu-id="e6308-101">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e6308-101">\<routing></span></span>

<span data-ttu-id="e6308-102">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="e6308-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="e6308-103">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e6308-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="e6308-104">&nbsp;&nbsp;**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="e6308-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e6308-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6308-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6308-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e6308-106">Attributes and elements</span></span>

<span data-ttu-id="e6308-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e6308-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6308-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e6308-108">Attributes</span></span>

<span data-ttu-id="e6308-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="e6308-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6308-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e6308-110">Child elements</span></span>

|     | <span data-ttu-id="e6308-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e6308-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e6308-112">**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="e6308-112">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="e6308-113">Obsahuje sady směrovacích filtrů, které určují, že typ MessageFilter Windows Communication Foundation (WCF) se použije při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="e6308-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="e6308-114">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="e6308-114">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="e6308-115">Obsahuje mapování mezi směrovacími filtry a cílovými koncovými body k určení, který koncový bod používat, pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="e6308-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="e6308-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e6308-116">Parent elements</span></span>

|     | <span data-ttu-id="e6308-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e6308-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="e6308-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="e6308-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="e6308-119">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="e6308-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e6308-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6308-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
