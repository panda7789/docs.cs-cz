---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399965"
---
# <a name="routing"></a><span data-ttu-id="d16ea-101">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="d16ea-101">\<routing></span></span>

<span data-ttu-id="d16ea-102">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr.</span><span class="sxs-lookup"><span data-stu-id="d16ea-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="d16ea-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d16ea-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d16ea-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d16ea-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d16ea-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> směrování**</span><span class="sxs-lookup"><span data-stu-id="d16ea-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d16ea-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d16ea-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d16ea-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d16ea-107">Attributes and elements</span></span>

<span data-ttu-id="d16ea-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d16ea-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d16ea-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="d16ea-109">Attributes</span></span>

<span data-ttu-id="d16ea-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="d16ea-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d16ea-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d16ea-111">Child elements</span></span>

|     | <span data-ttu-id="d16ea-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d16ea-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d16ea-113"> **\<> filtrů**</span><span class="sxs-lookup"><span data-stu-id="d16ea-113">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="d16ea-114">Obsahuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) MessageFilter bude použit při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="d16ea-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="d16ea-115"> **\<filterTables >** </span><span class="sxs-lookup"><span data-stu-id="d16ea-115">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="d16ea-116">Obsahuje mapování mezi směrovacími filtry a cílovými koncovými body k určení koncového bodu, který se má použít, když filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="d16ea-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="d16ea-117">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="d16ea-117">Parent elements</span></span>

|     | <span data-ttu-id="d16ea-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d16ea-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="d16ea-119">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="d16ea-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="d16ea-120">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="d16ea-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d16ea-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d16ea-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
