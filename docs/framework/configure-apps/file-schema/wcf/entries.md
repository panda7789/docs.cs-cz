---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855275"
---
# \<entries>
<span data-ttu-id="c89c7-101">Záznam směrování obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se odesílají zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="c89c7-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="c89c7-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c89c7-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c89c7-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c89c7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c89c7-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c89c7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c89c7-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="c89c7-105">Attributes</span></span>  
 <span data-ttu-id="c89c7-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="c89c7-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c89c7-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c89c7-107">Child Elements</span></span>  
  
|<span data-ttu-id="c89c7-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="c89c7-108">Element</span></span>|<span data-ttu-id="c89c7-109">Description</span><span class="sxs-lookup"><span data-stu-id="c89c7-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="c89c7-110">Mapuje filtr na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="c89c7-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="c89c7-111">Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="c89c7-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c89c7-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c89c7-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c89c7-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="c89c7-113">Element</span></span>|<span data-ttu-id="c89c7-114">Description</span><span class="sxs-lookup"><span data-stu-id="c89c7-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="c89c7-115">Konfigurační oddíl, který obsahuje směrovací tabulku.</span><span class="sxs-lookup"><span data-stu-id="c89c7-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c89c7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c89c7-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
