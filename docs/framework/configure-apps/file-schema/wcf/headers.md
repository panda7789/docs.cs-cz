---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: a982fa87ab84725e36ee913f00200cd34f0b8f6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925580"
---
# <a name="headers"></a><span data-ttu-id="36f22-101">\<> hlaviček</span><span class="sxs-lookup"><span data-stu-id="36f22-101">\<headers></span></span>
<span data-ttu-id="36f22-102">Kromě základního identifikátoru URI může koncový bod adresovat jedna nebo více hlaviček SOAP.</span><span class="sxs-lookup"><span data-stu-id="36f22-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="36f22-103">Jedna sada scénářů, kde je to užitečné, je sada zprostředkujících scénářů SOAP, kdy koncový bod vyžaduje, aby klienti tohoto koncového bodu zahrnuli hlavičky SOAP cílené na zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="36f22-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="36f22-104">Tento prvek konfigurace lze použít k definování vlastních hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="36f22-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="36f22-105">Položky v kolekci hlaviček koncového bodu jsou uživatelsky definované prvky XML.</span><span class="sxs-lookup"><span data-stu-id="36f22-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="36f22-106">Každý element musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="36f22-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="36f22-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="36f22-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="36f22-108">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="36f22-108">\<client></span></span>  
<span data-ttu-id="36f22-109">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="36f22-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f22-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36f22-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36f22-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="36f22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="36f22-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="36f22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36f22-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="36f22-113">Attributes</span></span>  
 <span data-ttu-id="36f22-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="36f22-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36f22-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="36f22-115">Child Elements</span></span>  
 <span data-ttu-id="36f22-116">Uživatelsky definované prvky XML.</span><span class="sxs-lookup"><span data-stu-id="36f22-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36f22-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="36f22-117">Parent Elements</span></span>  
  
|<span data-ttu-id="36f22-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="36f22-118">Element</span></span>|<span data-ttu-id="36f22-119">Popis</span><span class="sxs-lookup"><span data-stu-id="36f22-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36f22-120">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="36f22-120">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="36f22-121">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="36f22-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36f22-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36f22-122">Remarks</span></span>  
 <span data-ttu-id="36f22-123">Volitelná záhlaví poskytují podrobnější informace adresování pro identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="36f22-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="36f22-124">Například hlavičky mohou označovat, jak zpracovat příchozí zprávu, kde koncový bod by měl poslat zprávu odpovědi, nebo kterou instanci služby použít ke zpracování příchozí zprávy od určitého uživatele, pokud je k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="36f22-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f22-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36f22-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="36f22-126">Bod Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="36f22-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
