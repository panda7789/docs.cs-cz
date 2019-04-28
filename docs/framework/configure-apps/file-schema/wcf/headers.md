---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670674"
---
# <a name="headers"></a><span data-ttu-id="5f889-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="5f889-101">\<headers></span></span>
<span data-ttu-id="5f889-102">Koncový bod vyřešíte tak, že jednu nebo víc hlaviček SOAP kromě svůj základní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="5f889-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="5f889-103">Jedna sada scénáře, kde je to užitečné je sada SOAP zprostředkující scénáře, kdy vyžaduje, aby koncový bod klientům tohoto koncového bodu zahrnout záhlaví SOAP určenou pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="5f889-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="5f889-104">Tento prvek konfigurace je možné definovat tyto hlavičky vlastní adresu.</span><span class="sxs-lookup"><span data-stu-id="5f889-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="5f889-105">Položky v kolekci hlaviček koncového bodu jsou uživatelem definované elementy XML.</span><span class="sxs-lookup"><span data-stu-id="5f889-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="5f889-106">Každý prvek musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="5f889-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="5f889-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5f889-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="5f889-108">\<client></span><span class="sxs-lookup"><span data-stu-id="5f889-108">\<client></span></span>  
<span data-ttu-id="5f889-109">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="5f889-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f889-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f889-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f889-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5f889-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5f889-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5f889-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f889-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5f889-113">Attributes</span></span>  
 <span data-ttu-id="5f889-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="5f889-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f889-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5f889-115">Child Elements</span></span>  
 <span data-ttu-id="5f889-116">Uživatelem definované elementy XML.</span><span class="sxs-lookup"><span data-stu-id="5f889-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f889-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5f889-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5f889-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="5f889-118">Element</span></span>|<span data-ttu-id="5f889-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5f889-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f889-120">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="5f889-120">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="5f889-121">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="5f889-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f889-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f889-122">Remarks</span></span>  
 <span data-ttu-id="5f889-123">Volitelná záhlaví poskytují podrobnější informace o adresování k identifikaci a k interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="5f889-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="5f889-124">Záhlaví může například signalizovat zpracování příchozí zprávy, kde koncový bod má odeslat zpráva s odpovědí nebo které instanci služby pro použití ke zpracování příchozí zprávy z konkrétního uživatele, když jsou k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="5f889-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f889-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f889-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="5f889-126">Koncové body: Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="5f889-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
