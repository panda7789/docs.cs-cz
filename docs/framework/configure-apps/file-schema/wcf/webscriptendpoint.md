---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854811"
---
# \<webScriptEndpoint>
<span data-ttu-id="3886f-101">Tento prvek konfigurace definuje standardní koncový bod s pevnou [\<webHttpBinding>](webhttpbinding.md) vazbou, která automaticky přidá [\<enableWebScript>](enablewebscript.md) chování.</span><span class="sxs-lookup"><span data-stu-id="3886f-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="3886f-102">Tento koncový bod použijte při psaní služby, která se volá z aplikace ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="3886f-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="3886f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3886f-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3886f-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3886f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3886f-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3886f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3886f-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="3886f-106">Attributes</span></span>  
  
|<span data-ttu-id="3886f-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="3886f-107">Attribute</span></span>|<span data-ttu-id="3886f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3886f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3886f-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="3886f-109">webEndpointType</span></span>|<span data-ttu-id="3886f-110">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3886f-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3886f-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3886f-111">Child Elements</span></span>  
 <span data-ttu-id="3886f-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="3886f-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3886f-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3886f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="3886f-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="3886f-114">Element</span></span>|<span data-ttu-id="3886f-115">Description</span><span class="sxs-lookup"><span data-stu-id="3886f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="3886f-116">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="3886f-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3886f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3886f-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
