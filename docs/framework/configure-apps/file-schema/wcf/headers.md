---
title: "&lt;záhlaví&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7fdd869553a672045c94a256b00638c9d0c4c24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltheadersgt"></a><span data-ttu-id="1a6ab-102">&lt;záhlaví&gt;</span><span class="sxs-lookup"><span data-stu-id="1a6ab-102">&lt;headers&gt;</span></span>
<span data-ttu-id="1a6ab-103">Koncový bod lze řešit nejméně jedno záhlaví SOAP kromě jeho základní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="1a6ab-104">Jednu sadu scénáře, kde to je užitečné je sada SOAP zprostředkující scénáře, kde koncového bodu vyžaduje klientům tohoto koncového bodu patří zaměřený na prostředníci hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="1a6ab-105">Tento element konfigurace slouží k definování takových hlavičky vlastní adresu.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="1a6ab-106">Položky v kolekci hlaviček koncový bod se vlastní elementy XML.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="1a6ab-107">Každý prvek musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="1a6ab-108">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a6ab-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a6ab-109">\<klient ></span><span class="sxs-lookup"><span data-stu-id="1a6ab-109">\<client></span></span>  
<span data-ttu-id="1a6ab-110">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="1a6ab-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6ab-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a6ab-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a6ab-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1a6ab-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1a6ab-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a6ab-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="1a6ab-114">Attributes</span></span>  
 <span data-ttu-id="1a6ab-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="1a6ab-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a6ab-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1a6ab-116">Child Elements</span></span>  
  
|<span data-ttu-id="1a6ab-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a6ab-117">Element</span></span>|<span data-ttu-id="1a6ab-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1a6ab-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a6ab-119">Oblast</span><span class="sxs-lookup"><span data-stu-id="1a6ab-119">Region</span></span>||  
|<span data-ttu-id="1a6ab-120">Člen</span><span class="sxs-lookup"><span data-stu-id="1a6ab-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="1a6ab-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1a6ab-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1a6ab-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a6ab-122">Element</span></span>|<span data-ttu-id="1a6ab-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1a6ab-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a6ab-124">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="1a6ab-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="1a6ab-125">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a6ab-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a6ab-126">Remarks</span></span>  
 <span data-ttu-id="1a6ab-127">Volitelné záhlaví obsahují podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="1a6ab-128">Například záhlaví můžete určit, jak zpracovávat příchozí zprávy, kde má koncový bod odeslat zprávu odpovědi nebo které instanci služby pro použití ke zpracování příchozí zprávy z určitého uživatele, když jsou k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6ab-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a6ab-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="1a6ab-130">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="1a6ab-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
