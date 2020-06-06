---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854795"
---
# \<webHttpEndpoint>
<span data-ttu-id="87d51-101">Tento prvek konfigurace definuje standardní koncový bod s pevnou [\<webHttpBinding>](webhttpbinding.md) vazbou, která automaticky přidá [\<webHttp>](webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="87d51-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="87d51-102">Tento koncový bod použijte při psaní služby REST.</span><span class="sxs-lookup"><span data-stu-id="87d51-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="87d51-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87d51-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87d51-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87d51-104">Attributes and Elements</span></span>  
 <span data-ttu-id="87d51-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87d51-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87d51-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="87d51-106">Attributes</span></span>  
  
|<span data-ttu-id="87d51-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="87d51-107">Attribute</span></span>|<span data-ttu-id="87d51-108">Popis</span><span class="sxs-lookup"><span data-stu-id="87d51-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87d51-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="87d51-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="87d51-110">Logická hodnota, která určuje, zda je povolen automatický výběr formátu.</span><span class="sxs-lookup"><span data-stu-id="87d51-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="87d51-111">Pokud je povolen automatický formát výběru, infrastruktura analyzuje `Accept` hlavičku zprávy požadavku a určí nejvhodnější formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="87d51-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="87d51-112">Pokud `Accept` Hlavička neurčuje vhodný formát odpovědi, používá infrastruktura `Content-Type` zprávu požadavku nebo výchozí formát odpovědi této operace.</span><span class="sxs-lookup"><span data-stu-id="87d51-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="87d51-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="87d51-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="87d51-114">Atribut, který určuje výchozí formát odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="87d51-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="87d51-115">Tento atribut je <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="87d51-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="87d51-116">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="87d51-116">helpEnabled</span></span>|<span data-ttu-id="87d51-117">Logická hodnota, která označuje, zda je pro koncový bod povolena stránka Help HTTP.</span><span class="sxs-lookup"><span data-stu-id="87d51-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="87d51-118">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="87d51-118">webEndpointType</span></span>|<span data-ttu-id="87d51-119">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="87d51-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87d51-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87d51-120">Child Elements</span></span>  
 <span data-ttu-id="87d51-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="87d51-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87d51-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87d51-122">Parent Elements</span></span>  
  
|<span data-ttu-id="87d51-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="87d51-123">Element</span></span>|<span data-ttu-id="87d51-124">Description</span><span class="sxs-lookup"><span data-stu-id="87d51-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="87d51-125">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="87d51-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87d51-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="87d51-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
