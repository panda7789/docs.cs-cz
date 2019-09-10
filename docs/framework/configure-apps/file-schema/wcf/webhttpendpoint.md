---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854795"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="e4ad2-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="e4ad2-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="e4ad2-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<vazbou WebHttpBinding >](webhttpbinding.md) [ \<](webhttp.md) , která automaticky přidá chování > protokolu WebHttp.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="e4ad2-103">Tento koncový bod použijte při psaní služby REST.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="e4ad2-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e4ad2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e4ad2-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e4ad2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e4ad2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="e4ad2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="e4ad2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="e4ad2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ad2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4ad2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4ad2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4ad2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e4ad2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4ad2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4ad2-111">Attributes</span></span>  
  
|<span data-ttu-id="e4ad2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ad2-112">Attribute</span></span>|<span data-ttu-id="e4ad2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ad2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4ad2-114">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="e4ad2-114">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="e4ad2-115">Logická hodnota, která určuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-115">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="e4ad2-116">Pokud je povolen automatický formát výběru, infrastruktura analyzuje `Accept` hlavičku zprávy požadavku a určí nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-116">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="e4ad2-117">Pokud hlavička neurčuje vhodný formát odpovědi, `Content-Type` používá infrastruktura zprávu požadavku nebo výchozí formát odpovědi této operace. `Accept`</span><span class="sxs-lookup"><span data-stu-id="e4ad2-117">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="e4ad2-118">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="e4ad2-118">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="e4ad2-119">Atribut, který určuje výchozí formát odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-119">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="e4ad2-120">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="e4ad2-120">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="e4ad2-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="e4ad2-121">helpEnabled</span></span>|<span data-ttu-id="e4ad2-122">Logická hodnota, která označuje, zda je pro koncový bod povolena stránka Help HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-122">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="e4ad2-123">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="e4ad2-123">webEndpointType</span></span>|<span data-ttu-id="e4ad2-124">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-124">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4ad2-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4ad2-125">Child Elements</span></span>  
 <span data-ttu-id="e4ad2-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="e4ad2-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4ad2-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4ad2-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e4ad2-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4ad2-128">Element</span></span>|<span data-ttu-id="e4ad2-129">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ad2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4ad2-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e4ad2-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e4ad2-131">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="e4ad2-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4ad2-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4ad2-132">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
