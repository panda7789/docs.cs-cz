---
title: '&lt;Směrování&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltroutinggt"></a><span data-ttu-id="fa436-102">&lt;Směrování&gt;</span><span class="sxs-lookup"><span data-stu-id="fa436-102">&lt;routing&gt;</span></span>

<span data-ttu-id="fa436-103">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k Pokud filtr odpovídá odesílat zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa436-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="fa436-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="fa436-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="fa436-105">&nbsp;&nbsp;**\<směrování >**</span><span class="sxs-lookup"><span data-stu-id="fa436-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fa436-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa436-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="fa436-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fa436-107">Attributes and elements</span></span>

<span data-ttu-id="fa436-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fa436-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa436-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="fa436-109">Attributes</span></span>

<span data-ttu-id="fa436-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="fa436-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa436-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="fa436-111">Child elements</span></span>

|     | <span data-ttu-id="fa436-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fa436-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fa436-113">**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="fa436-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="fa436-114">Obsahuje sadu směrování filtry, které určují, že typ MessageFilter Windows Communication Foundation (WCF) se použije při vyhodnocení příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa436-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="fa436-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="fa436-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="fa436-116">Obsahuje mapování mezi směrování filtry a cílové koncové body k určení kterému koncovému bodu pro použití při odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="fa436-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="fa436-117">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="fa436-117">Parent elements</span></span>

|     | <span data-ttu-id="fa436-118">Popis</span><span class="sxs-lookup"><span data-stu-id="fa436-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="fa436-119">**\<systém. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="fa436-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="fa436-120">Kořenový element všechny konfigurační prvky WCF.</span><span class="sxs-lookup"><span data-stu-id="fa436-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fa436-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa436-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
