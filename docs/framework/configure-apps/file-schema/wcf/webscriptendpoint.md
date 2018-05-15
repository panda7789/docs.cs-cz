---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b53b7cc3ce812b72830c0ad83c5cc2b42bfc25a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="a6cb0-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="a6cb0-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="a6cb0-103">Tento element konfigurace definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování.</span><span class="sxs-lookup"><span data-stu-id="a6cb0-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="a6cb0-104">Když vytváříte službu, která je volána z aplikace ASP.NET AJAX, použijte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a6cb0-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="a6cb0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6cb0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6cb0-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a6cb0-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6cb0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6cb0-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6cb0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6cb0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6cb0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6cb0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6cb0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6cb0-110">Attributes</span></span>  
  
|<span data-ttu-id="a6cb0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a6cb0-111">Attribute</span></span>|<span data-ttu-id="a6cb0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a6cb0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6cb0-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="a6cb0-113">webEndpointType</span></span>|<span data-ttu-id="a6cb0-114">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a6cb0-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6cb0-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6cb0-115">Child Elements</span></span>  
 <span data-ttu-id="a6cb0-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6cb0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6cb0-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6cb0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a6cb0-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6cb0-118">Element</span></span>|<span data-ttu-id="a6cb0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a6cb0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6cb0-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a6cb0-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="a6cb0-121">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="a6cb0-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6cb0-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6cb0-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
