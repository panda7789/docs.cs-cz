---
title: '&lt;Směrování&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 220c18ab8ea6222fcf7d9fb8a93950281c9de796
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145143"
---
# <a name="ltroutinggt"></a><span data-ttu-id="67fab-102">&lt;Směrování&gt;</span><span class="sxs-lookup"><span data-stu-id="67fab-102">&lt;routing&gt;</span></span>

<span data-ttu-id="67fab-103">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="67fab-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="67fab-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="67fab-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="67fab-105">&nbsp;&nbsp;**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="67fab-105">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="67fab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67fab-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67fab-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="67fab-107">Attributes and elements</span></span>

<span data-ttu-id="67fab-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="67fab-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="67fab-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="67fab-109">Attributes</span></span>

<span data-ttu-id="67fab-110">Žádná</span><span class="sxs-lookup"><span data-stu-id="67fab-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="67fab-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="67fab-111">Child elements</span></span>

|     | <span data-ttu-id="67fab-112">Popis</span><span class="sxs-lookup"><span data-stu-id="67fab-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="67fab-113">**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="67fab-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="67fab-114">Obsahuje sady směrovacích filtrů, které určují, že typ MessageFilter Windows Communication Foundation (WCF) se použije při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="67fab-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="67fab-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="67fab-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="67fab-116">Obsahuje mapování mezi směrovacími filtry a cílovými koncovými body k určení, který koncový bod používat, pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="67fab-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="67fab-117">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="67fab-117">Parent elements</span></span>

|     | <span data-ttu-id="67fab-118">Popis</span><span class="sxs-lookup"><span data-stu-id="67fab-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="67fab-119">**\<systém. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="67fab-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="67fab-120">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="67fab-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="67fab-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67fab-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
