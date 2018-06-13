---
title: '&lt;Záhlaví&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747148"
---
# <a name="ltheadersgt"></a><span data-ttu-id="c23de-102">&lt;Záhlaví&gt;</span><span class="sxs-lookup"><span data-stu-id="c23de-102">&lt;headers&gt;</span></span>
<span data-ttu-id="c23de-103">Koncový bod lze řešit nejméně jedno záhlaví SOAP kromě jeho základní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="c23de-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="c23de-104">Jednu sadu scénáře, kde to je užitečné je sada SOAP zprostředkující scénáře, kde koncového bodu vyžaduje klientům tohoto koncového bodu patří zaměřený na prostředníci hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="c23de-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="c23de-105">Tento element konfigurace slouží k definování takových hlavičky vlastní adresu.</span><span class="sxs-lookup"><span data-stu-id="c23de-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="c23de-106">Položky v kolekci hlaviček koncový bod se vlastní elementy XML.</span><span class="sxs-lookup"><span data-stu-id="c23de-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="c23de-107">Každý prvek musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="c23de-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="c23de-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c23de-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="c23de-109">\<klient ></span><span class="sxs-lookup"><span data-stu-id="c23de-109">\<client></span></span>  
<span data-ttu-id="c23de-110">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="c23de-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c23de-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c23de-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c23de-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c23de-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c23de-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c23de-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c23de-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="c23de-114">Attributes</span></span>  
 <span data-ttu-id="c23de-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="c23de-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c23de-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c23de-116">Child Elements</span></span>  
  
|<span data-ttu-id="c23de-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="c23de-117">Element</span></span>|<span data-ttu-id="c23de-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c23de-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c23de-119">Oblast</span><span class="sxs-lookup"><span data-stu-id="c23de-119">Region</span></span>||  
|<span data-ttu-id="c23de-120">Člen</span><span class="sxs-lookup"><span data-stu-id="c23de-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="c23de-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c23de-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c23de-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="c23de-122">Element</span></span>|<span data-ttu-id="c23de-123">Popis</span><span class="sxs-lookup"><span data-stu-id="c23de-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c23de-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="c23de-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="c23de-125">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c23de-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c23de-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c23de-126">Remarks</span></span>  
 <span data-ttu-id="c23de-127">Volitelné záhlaví obsahují podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="c23de-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="c23de-128">Například záhlaví můžete určit, jak zpracovávat příchozí zprávy, kde má koncový bod odeslat zprávu odpovědi nebo které instanci služby pro použití ke zpracování příchozí zprávy z určitého uživatele, když jsou k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="c23de-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23de-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c23de-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="c23de-130">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="c23de-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
