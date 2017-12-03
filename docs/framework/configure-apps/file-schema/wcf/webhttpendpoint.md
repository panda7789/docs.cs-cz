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
ms.openlocfilehash: ee055be8c4d2e53dc22a101529e5521add9b54a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="09769-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="09769-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="09769-103">Tento element konfigurace definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="09769-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="09769-104">Při zápisu služby REST, použijte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="09769-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="09769-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="09769-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="09769-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="09769-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09769-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09769-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09769-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09769-108">Attributes and Elements</span></span>  
 <span data-ttu-id="09769-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="09769-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09769-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="09769-110">Attributes</span></span>  
  
|<span data-ttu-id="09769-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="09769-111">Attribute</span></span>|<span data-ttu-id="09769-112">Popis</span><span class="sxs-lookup"><span data-stu-id="09769-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09769-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="09769-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="09769-114">Logická hodnota, která označuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="09769-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="09769-115">Pokud je povolen automatický výběr formátu, analyzuje infrastruktury `Accept` záhlaví zprávy požadavku a určuje nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="09769-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="09769-116">Pokud `Accept` záhlaví neurčuje formát vhodný odpovědi, používá infrastrukturu `Content-Type` zprávu požadavku nebo formát odpovědi výchozí operace.</span><span class="sxs-lookup"><span data-stu-id="09769-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="09769-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="09769-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="09769-118">Atribut, který určuje výchozí formát pro odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="09769-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="09769-119">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="09769-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="09769-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="09769-120">helpEnabled</span></span>|<span data-ttu-id="09769-121">Logická hodnota, která určuje, zda je povoleno na stránce nápovědy HTTP pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="09769-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="09769-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="09769-122">webEndpointType</span></span>|<span data-ttu-id="09769-123">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="09769-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09769-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09769-124">Child Elements</span></span>  
 <span data-ttu-id="09769-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="09769-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09769-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09769-126">Parent Elements</span></span>  
  
|<span data-ttu-id="09769-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="09769-127">Element</span></span>|<span data-ttu-id="09769-128">Popis</span><span class="sxs-lookup"><span data-stu-id="09769-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09769-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="09769-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="09769-130">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="09769-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09769-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="09769-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
