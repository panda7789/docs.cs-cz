---
title: '&lt;webScriptEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 855a0fc0727bf0559b922317d439f7550f18d9ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="9e9ec-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="9e9ec-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="9e9ec-103">Tento element konfigurace definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování.</span><span class="sxs-lookup"><span data-stu-id="9e9ec-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="9e9ec-104">Když vytváříte službu, která je volána z aplikace ASP.NET AJAX, použijte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9e9ec-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="9e9ec-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9e9ec-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e9ec-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9e9ec-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e9ec-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e9ec-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e9ec-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9e9ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9e9ec-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9e9ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e9ec-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9e9ec-110">Attributes</span></span>  
  
|<span data-ttu-id="9e9ec-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="9e9ec-111">Attribute</span></span>|<span data-ttu-id="9e9ec-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9e9ec-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e9ec-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="9e9ec-113">webEndpointType</span></span>|<span data-ttu-id="9e9ec-114">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9e9ec-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e9ec-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9e9ec-115">Child Elements</span></span>  
 <span data-ttu-id="9e9ec-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="9e9ec-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e9ec-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9e9ec-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9e9ec-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="9e9ec-118">Element</span></span>|<span data-ttu-id="9e9ec-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9e9ec-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e9ec-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9e9ec-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9e9ec-121">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="9e9ec-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e9ec-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e9ec-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
