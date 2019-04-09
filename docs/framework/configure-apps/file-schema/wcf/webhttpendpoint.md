---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 6fb31fca6ac38f6cb92ef087cc277a4d5066521c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182452"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="230a8-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="230a8-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="230a8-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, která automaticky přidá [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="230a8-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="230a8-103">Při zápisu služby REST, používejte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="230a8-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="230a8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="230a8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="230a8-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="230a8-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="230a8-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="230a8-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="230a8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="230a8-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="230a8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="230a8-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="230a8-109">Attributes</span></span>  
  
|<span data-ttu-id="230a8-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="230a8-110">Attribute</span></span>|<span data-ttu-id="230a8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="230a8-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="230a8-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="230a8-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="230a8-113">Logická hodnota, která určuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="230a8-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="230a8-114">Pokud je povolen automatický výběr formátu, infrastruktura analyzuje `Accept` záhlaví zprávy s požadavkem a určí nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="230a8-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="230a8-115">Pokud `Accept` záhlaví neurčuje formát vhodný odpovědi, využívá infrastrukturu `Content-Type` zprávy s požadavkem nebo výchozí formát odpovědi z operace.</span><span class="sxs-lookup"><span data-stu-id="230a8-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="230a8-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="230a8-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="230a8-117">Atribut, který určuje výchozí formát pro odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="230a8-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="230a8-118">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="230a8-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="230a8-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="230a8-119">helpEnabled</span></span>|<span data-ttu-id="230a8-120">Logická hodnota určující, zda je povoleno na stránce nápovědy HTTP pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="230a8-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="230a8-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="230a8-121">webEndpointType</span></span>|<span data-ttu-id="230a8-122">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="230a8-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="230a8-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="230a8-123">Child Elements</span></span>  
 <span data-ttu-id="230a8-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="230a8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="230a8-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="230a8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="230a8-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="230a8-126">Element</span></span>|<span data-ttu-id="230a8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="230a8-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="230a8-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="230a8-128">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="230a8-129">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="230a8-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="230a8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="230a8-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
