---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: acafb5b6a5c4911dcf21a55cfb9e93883067e5ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566382"
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="53137-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="53137-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="53137-103">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, která automaticky přidá [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování.</span><span class="sxs-lookup"><span data-stu-id="53137-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="53137-104">Používejte tento koncový bod, když vytváříte službu, která je volána z aplikace technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="53137-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="53137-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="53137-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="53137-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="53137-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53137-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53137-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53137-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53137-108">Attributes and Elements</span></span>  
 <span data-ttu-id="53137-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53137-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53137-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="53137-110">Attributes</span></span>  
  
|<span data-ttu-id="53137-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="53137-111">Attribute</span></span>|<span data-ttu-id="53137-112">Popis</span><span class="sxs-lookup"><span data-stu-id="53137-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53137-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="53137-113">webEndpointType</span></span>|<span data-ttu-id="53137-114">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="53137-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53137-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53137-115">Child Elements</span></span>  
 <span data-ttu-id="53137-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="53137-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53137-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53137-117">Parent Elements</span></span>  
  
|<span data-ttu-id="53137-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="53137-118">Element</span></span>|<span data-ttu-id="53137-119">Popis</span><span class="sxs-lookup"><span data-stu-id="53137-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53137-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="53137-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="53137-121">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="53137-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53137-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53137-122">See also</span></span>
- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
