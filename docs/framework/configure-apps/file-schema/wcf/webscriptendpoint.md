---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 9619c27c8c6d41250eeaeccabebe611e94b7d874
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105648"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="2736c-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="2736c-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="2736c-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, která automaticky přidá [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování.</span><span class="sxs-lookup"><span data-stu-id="2736c-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="2736c-103">Používejte tento koncový bod, když vytváříte službu, která je volána z aplikace technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2736c-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="2736c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2736c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2736c-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="2736c-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2736c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2736c-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2736c-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2736c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2736c-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2736c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2736c-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="2736c-109">Attributes</span></span>  
  
|<span data-ttu-id="2736c-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="2736c-110">Attribute</span></span>|<span data-ttu-id="2736c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2736c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2736c-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="2736c-112">webEndpointType</span></span>|<span data-ttu-id="2736c-113">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2736c-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2736c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2736c-114">Child Elements</span></span>  
 <span data-ttu-id="2736c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="2736c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2736c-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2736c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2736c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="2736c-117">Element</span></span>|<span data-ttu-id="2736c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2736c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2736c-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="2736c-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="2736c-120">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="2736c-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2736c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2736c-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
