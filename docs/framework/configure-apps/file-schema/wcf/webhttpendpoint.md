---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: ee14ce23370675782f4c25385c1786fdce11eba0
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151966"
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="fabeb-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="fabeb-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="fabeb-103">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, která automaticky přidá [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="fabeb-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="fabeb-104">Při zápisu služby REST, používejte tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="fabeb-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="fabeb-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fabeb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fabeb-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fabeb-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fabeb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fabeb-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fabeb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fabeb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fabeb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fabeb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fabeb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fabeb-110">Attributes</span></span>  
  
|<span data-ttu-id="fabeb-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fabeb-111">Attribute</span></span>|<span data-ttu-id="fabeb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fabeb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fabeb-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="fabeb-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="fabeb-114">Logická hodnota, která určuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="fabeb-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="fabeb-115">Pokud je povolen automatický výběr formátu, infrastruktura analyzuje `Accept` záhlaví zprávy s požadavkem a určí nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="fabeb-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="fabeb-116">Pokud `Accept` záhlaví neurčuje formát vhodný odpovědi, využívá infrastrukturu `Content-Type` zprávy s požadavkem nebo výchozí formát odpovědi z operace.</span><span class="sxs-lookup"><span data-stu-id="fabeb-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="fabeb-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="fabeb-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="fabeb-118">Atribut, který určuje výchozí formát pro odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="fabeb-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="fabeb-119">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="fabeb-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="fabeb-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="fabeb-120">helpEnabled</span></span>|<span data-ttu-id="fabeb-121">Logická hodnota určující, zda je povoleno na stránce nápovědy HTTP pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="fabeb-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="fabeb-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="fabeb-122">webEndpointType</span></span>|<span data-ttu-id="fabeb-123">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fabeb-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fabeb-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fabeb-124">Child Elements</span></span>  
 <span data-ttu-id="fabeb-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="fabeb-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fabeb-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fabeb-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fabeb-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="fabeb-127">Element</span></span>|<span data-ttu-id="fabeb-128">Popis</span><span class="sxs-lookup"><span data-stu-id="fabeb-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fabeb-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fabeb-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="fabeb-130">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="fabeb-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fabeb-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="fabeb-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
