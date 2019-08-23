---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 866be522cb1c64142227a8d6a1a8f88551ca9105
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940474"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="a1edd-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="a1edd-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="a1edd-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<vazbou WebHttpBinding >](webhttpbinding.md) [ \<](webhttp.md) , která automaticky přidá chování > protokolu WebHttp.</span><span class="sxs-lookup"><span data-stu-id="a1edd-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="a1edd-103">Tento koncový bod použijte při psaní služby REST.</span><span class="sxs-lookup"><span data-stu-id="a1edd-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="a1edd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a1edd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a1edd-105">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a1edd-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1edd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1edd-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1edd-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a1edd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a1edd-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a1edd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1edd-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a1edd-109">Attributes</span></span>  
  
|<span data-ttu-id="a1edd-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="a1edd-110">Attribute</span></span>|<span data-ttu-id="a1edd-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a1edd-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1edd-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="a1edd-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="a1edd-113">Logická hodnota, která určuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="a1edd-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="a1edd-114">Pokud je povolen automatický formát výběru, infrastruktura analyzuje `Accept` hlavičku zprávy požadavku a určí nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a1edd-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="a1edd-115">Pokud hlavička neurčuje vhodný formát odpovědi, `Content-Type` používá infrastruktura zprávu požadavku nebo výchozí formát odpovědi této operace. `Accept`</span><span class="sxs-lookup"><span data-stu-id="a1edd-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="a1edd-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="a1edd-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="a1edd-117">Atribut, který určuje výchozí formát odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a1edd-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="a1edd-118">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="a1edd-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="a1edd-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="a1edd-119">helpEnabled</span></span>|<span data-ttu-id="a1edd-120">Logická hodnota, která označuje, zda je pro koncový bod povolena stránka Help HTTP.</span><span class="sxs-lookup"><span data-stu-id="a1edd-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="a1edd-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="a1edd-121">webEndpointType</span></span>|<span data-ttu-id="a1edd-122">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a1edd-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1edd-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a1edd-123">Child Elements</span></span>  
 <span data-ttu-id="a1edd-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1edd-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1edd-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a1edd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a1edd-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="a1edd-126">Element</span></span>|<span data-ttu-id="a1edd-127">Popis</span><span class="sxs-lookup"><span data-stu-id="a1edd-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1edd-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="a1edd-128">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="a1edd-129">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="a1edd-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1edd-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1edd-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
