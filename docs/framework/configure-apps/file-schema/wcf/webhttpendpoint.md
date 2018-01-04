---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc45511e0e7b4644704a834f0bc08d64ff3367f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="112fe-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="112fe-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="112fe-103">Tento element konfigurace definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="112fe-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="112fe-104">Při zápisu služby REST, použijte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="112fe-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="112fe-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="112fe-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="112fe-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="112fe-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112fe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="112fe-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="112fe-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="112fe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="112fe-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="112fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="112fe-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="112fe-110">Attributes</span></span>  
  
|<span data-ttu-id="112fe-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="112fe-111">Attribute</span></span>|<span data-ttu-id="112fe-112">Popis</span><span class="sxs-lookup"><span data-stu-id="112fe-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="112fe-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="112fe-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="112fe-114">Logická hodnota, která označuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="112fe-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="112fe-115">Pokud je povolen automatický výběr formátu, analyzuje infrastruktury `Accept` záhlaví zprávy požadavku a určuje nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="112fe-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="112fe-116">Pokud `Accept` záhlaví neurčuje formát vhodný odpovědi, používá infrastrukturu `Content-Type` zprávu požadavku nebo formát odpovědi výchozí operace.</span><span class="sxs-lookup"><span data-stu-id="112fe-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="112fe-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="112fe-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="112fe-118">Atribut, který určuje výchozí formát pro odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="112fe-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="112fe-119">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="112fe-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="112fe-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="112fe-120">helpEnabled</span></span>|<span data-ttu-id="112fe-121">Logická hodnota, která určuje, zda je povoleno na stránce nápovědy HTTP pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="112fe-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="112fe-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="112fe-122">webEndpointType</span></span>|<span data-ttu-id="112fe-123">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="112fe-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="112fe-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="112fe-124">Child Elements</span></span>  
 <span data-ttu-id="112fe-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="112fe-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="112fe-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="112fe-126">Parent Elements</span></span>  
  
|<span data-ttu-id="112fe-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="112fe-127">Element</span></span>|<span data-ttu-id="112fe-128">Popis</span><span class="sxs-lookup"><span data-stu-id="112fe-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="112fe-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="112fe-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="112fe-130">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="112fe-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="112fe-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="112fe-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
