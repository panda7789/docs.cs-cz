---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 3c3c3a3d747a1338e2db3afa92c735af4a588642
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288025"
---
# <a name="headers"></a><span data-ttu-id="73cef-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="73cef-101">\<headers></span></span>
<span data-ttu-id="73cef-102">Koncový bod vyřešíte tak, že jednu nebo víc hlaviček SOAP kromě svůj základní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="73cef-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="73cef-103">Jedna sada scénáře, kde je to užitečné je sada SOAP zprostředkující scénáře, kdy vyžaduje, aby koncový bod klientům tohoto koncového bodu zahrnout záhlaví SOAP určenou pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="73cef-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="73cef-104">Tento prvek konfigurace je možné definovat tyto hlavičky vlastní adresu.</span><span class="sxs-lookup"><span data-stu-id="73cef-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="73cef-105">Položky v kolekci hlaviček koncového bodu jsou uživatelem definované elementy XML.</span><span class="sxs-lookup"><span data-stu-id="73cef-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="73cef-106">Každý prvek musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="73cef-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="73cef-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="73cef-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="73cef-108">\<client></span><span class="sxs-lookup"><span data-stu-id="73cef-108">\<client></span></span>  
<span data-ttu-id="73cef-109">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="73cef-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73cef-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73cef-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73cef-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="73cef-111">Attributes and Elements</span></span>  
 <span data-ttu-id="73cef-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="73cef-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73cef-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="73cef-113">Attributes</span></span>  
 <span data-ttu-id="73cef-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="73cef-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73cef-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="73cef-115">Child Elements</span></span>  
 <span data-ttu-id="73cef-116">Uživatelem definované elementy XML.</span><span class="sxs-lookup"><span data-stu-id="73cef-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73cef-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="73cef-117">Parent Elements</span></span>  
  
|<span data-ttu-id="73cef-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="73cef-118">Element</span></span>|<span data-ttu-id="73cef-119">Popis</span><span class="sxs-lookup"><span data-stu-id="73cef-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73cef-120">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="73cef-120">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="73cef-121">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="73cef-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73cef-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73cef-122">Remarks</span></span>  
 <span data-ttu-id="73cef-123">Volitelná záhlaví poskytují podrobnější informace o adresování k identifikaci a k interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="73cef-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="73cef-124">Záhlaví může například signalizovat zpracování příchozí zprávy, kde koncový bod má odeslat zpráva s odpovědí nebo které instanci služby pro použití ke zpracování příchozí zprávy z konkrétního uživatele, když jsou k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="73cef-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cef-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73cef-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="73cef-126">Koncové body: Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="73cef-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
