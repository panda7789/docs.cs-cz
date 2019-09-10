---
title: <filters> z <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855246"
---
# <a name="filters-of-routing"></a><span data-ttu-id="cf45f-102">\<filtruje > \<> směrování.</span><span class="sxs-lookup"><span data-stu-id="cf45f-102">\<filters> of \<routing></span></span>

<span data-ttu-id="cf45f-103">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , který se použije při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="cf45f-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="cf45f-104">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cf45f-104">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cf45f-105">&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="cf45f-105">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="cf45f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> filtrů**</span><span class="sxs-lookup"><span data-stu-id="cf45f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf45f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf45f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf45f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cf45f-108">Attributes and elements</span></span>

<span data-ttu-id="cf45f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cf45f-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf45f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="cf45f-110">Attributes</span></span>

<span data-ttu-id="cf45f-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf45f-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf45f-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="cf45f-112">Child elements</span></span>

|     | <span data-ttu-id="cf45f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cf45f-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cf45f-114"> **\<Filtrovat >** </span><span class="sxs-lookup"><span data-stu-id="cf45f-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="cf45f-115">Obsahuje filtr směrování, který určuje typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se použije při vyhodnocování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="cf45f-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="cf45f-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="cf45f-116">Parent elements</span></span>

|     | <span data-ttu-id="cf45f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="cf45f-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cf45f-118"> **\<> směrování**</span><span class="sxs-lookup"><span data-stu-id="cf45f-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="cf45f-119">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr.</span><span class="sxs-lookup"><span data-stu-id="cf45f-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="cf45f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf45f-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
