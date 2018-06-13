---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 46691a36b62898583132b5668b06de5659926d66
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767086"
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="aa68d-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="aa68d-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="aa68d-103">Tento element konfigurace definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="aa68d-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="aa68d-104">Při zápisu služby REST, použijte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="aa68d-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="aa68d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aa68d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="aa68d-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="aa68d-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa68d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa68d-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa68d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aa68d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa68d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aa68d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa68d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="aa68d-110">Attributes</span></span>  
  
|<span data-ttu-id="aa68d-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="aa68d-111">Attribute</span></span>|<span data-ttu-id="aa68d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aa68d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa68d-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="aa68d-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="aa68d-114">Logická hodnota, která označuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="aa68d-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="aa68d-115">Pokud je povolen automatický výběr formátu, analyzuje infrastruktury `Accept` záhlaví zprávy požadavku a určuje nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="aa68d-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="aa68d-116">Pokud `Accept` záhlaví neurčuje formát vhodný odpovědi, používá infrastrukturu `Content-Type` zprávu požadavku nebo formát odpovědi výchozí operace.</span><span class="sxs-lookup"><span data-stu-id="aa68d-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="aa68d-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="aa68d-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="aa68d-118">Atribut, který určuje výchozí formát pro odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="aa68d-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="aa68d-119">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="aa68d-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="aa68d-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="aa68d-120">helpEnabled</span></span>|<span data-ttu-id="aa68d-121">Logická hodnota, která určuje, zda je povoleno na stránce nápovědy HTTP pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="aa68d-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="aa68d-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="aa68d-122">webEndpointType</span></span>|<span data-ttu-id="aa68d-123">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="aa68d-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa68d-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aa68d-124">Child Elements</span></span>  
 <span data-ttu-id="aa68d-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="aa68d-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa68d-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aa68d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="aa68d-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa68d-127">Element</span></span>|<span data-ttu-id="aa68d-128">Popis</span><span class="sxs-lookup"><span data-stu-id="aa68d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa68d-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="aa68d-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="aa68d-130">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="aa68d-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa68d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa68d-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
