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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5c8d75c457c4f8ec427480afd0e4d3e7335ff981
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="f0a8f-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="f0a8f-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="f0a8f-103">Tento element konfigurace definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="f0a8f-104">Při zápisu služby REST, použijte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="f0a8f-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f0a8f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f0a8f-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f0a8f-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0a8f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0a8f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0a8f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f0a8f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f0a8f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0a8f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f0a8f-110">Attributes</span></span>  
  
|<span data-ttu-id="f0a8f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f0a8f-111">Attribute</span></span>|<span data-ttu-id="f0a8f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f0a8f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0a8f-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="f0a8f-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="f0a8f-114">Logická hodnota, která označuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="f0a8f-115">Pokud je povolen automatický výběr formátu, analyzuje infrastruktury `Accept` záhlaví zprávy požadavku a určuje nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="f0a8f-116">Pokud `Accept` záhlaví neurčuje formát vhodný odpovědi, používá infrastrukturu `Content-Type` zprávu požadavku nebo formát odpovědi výchozí operace.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="f0a8f-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="f0a8f-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="f0a8f-118">Atribut, který určuje výchozí formát pro odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="f0a8f-119">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="f0a8f-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="f0a8f-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="f0a8f-120">helpEnabled</span></span>|<span data-ttu-id="f0a8f-121">Logická hodnota, která určuje, zda je povoleno na stránce nápovědy HTTP pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="f0a8f-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="f0a8f-122">webEndpointType</span></span>|<span data-ttu-id="f0a8f-123">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0a8f-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f0a8f-124">Child Elements</span></span>  
 <span data-ttu-id="f0a8f-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="f0a8f-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0a8f-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f0a8f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f0a8f-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="f0a8f-127">Element</span></span>|<span data-ttu-id="f0a8f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="f0a8f-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0a8f-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f0a8f-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f0a8f-130">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="f0a8f-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0a8f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0a8f-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
