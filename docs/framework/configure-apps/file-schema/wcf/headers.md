---
title: '&lt;headers&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: f47462ba63b9bd8868420ee9d3a320ba18c83c65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557822"
---
# <a name="ltheadersgt"></a><span data-ttu-id="2cf9b-102">&lt;headers&gt;</span><span class="sxs-lookup"><span data-stu-id="2cf9b-102">&lt;headers&gt;</span></span>
<span data-ttu-id="2cf9b-103">Koncový bod vyřešíte tak, že jednu nebo víc hlaviček SOAP kromě svůj základní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="2cf9b-104">Jedna sada scénáře, kde je to užitečné je sada SOAP zprostředkující scénáře, kdy vyžaduje, aby koncový bod klientům tohoto koncového bodu zahrnout záhlaví SOAP určenou pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="2cf9b-105">Tento prvek konfigurace je možné definovat tyto hlavičky vlastní adresu.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="2cf9b-106">Položky v kolekci hlaviček koncového bodu jsou uživatelem definované elementy XML.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="2cf9b-107">Každý prvek musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="2cf9b-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2cf9b-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="2cf9b-109">\<client></span><span class="sxs-lookup"><span data-stu-id="2cf9b-109">\<client></span></span>  
<span data-ttu-id="2cf9b-110">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2cf9b-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf9b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cf9b-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cf9b-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2cf9b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2cf9b-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cf9b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="2cf9b-114">Attributes</span></span>  
 <span data-ttu-id="2cf9b-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="2cf9b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2cf9b-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2cf9b-116">Child Elements</span></span>  
 <span data-ttu-id="2cf9b-117">Uživatelem definované elementy XML.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-117">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cf9b-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2cf9b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2cf9b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2cf9b-119">Element</span></span>|<span data-ttu-id="2cf9b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2cf9b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cf9b-121">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2cf9b-121">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="2cf9b-122">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-122">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cf9b-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cf9b-123">Remarks</span></span>  
 <span data-ttu-id="2cf9b-124">Volitelná záhlaví poskytují podrobnější informace o adresování k identifikaci a k interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-124">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="2cf9b-125">Záhlaví může například signalizovat zpracování příchozí zprávy, kde koncový bod má odeslat zpráva s odpovědí nebo které instanci služby pro použití ke zpracování příchozí zprávy z konkrétního uživatele, když jsou k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="2cf9b-125">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf9b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cf9b-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="2cf9b-127">Koncové body: Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="2cf9b-127">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
