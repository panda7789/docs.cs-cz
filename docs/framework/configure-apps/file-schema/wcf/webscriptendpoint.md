---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: cc69029d9830fd12df5a4070f11847fadf4c60bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940406"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="875a9-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="875a9-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="875a9-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<vazbou WebHttpBinding >](webhttpbinding.md) [ \<](enablewebscript.md) , která automaticky přidá chování enableWebScript >.</span><span class="sxs-lookup"><span data-stu-id="875a9-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="875a9-103">Tento koncový bod použijte při psaní služby, která se volá z aplikace ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="875a9-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="875a9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="875a9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="875a9-105">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="875a9-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="875a9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="875a9-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="875a9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="875a9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="875a9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="875a9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="875a9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="875a9-109">Attributes</span></span>  
  
|<span data-ttu-id="875a9-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="875a9-110">Attribute</span></span>|<span data-ttu-id="875a9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="875a9-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="875a9-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="875a9-112">webEndpointType</span></span>|<span data-ttu-id="875a9-113">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="875a9-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="875a9-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="875a9-114">Child Elements</span></span>  
 <span data-ttu-id="875a9-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="875a9-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="875a9-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="875a9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="875a9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="875a9-117">Element</span></span>|<span data-ttu-id="875a9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="875a9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="875a9-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="875a9-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="875a9-120">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="875a9-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="875a9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="875a9-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
