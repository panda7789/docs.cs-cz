---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855182"
---
# \<headers>
<span data-ttu-id="94c5d-101">Kromě základního identifikátoru URI může koncový bod adresovat jedna nebo více hlaviček SOAP.</span><span class="sxs-lookup"><span data-stu-id="94c5d-101">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="94c5d-102">Jedna sada scénářů, kde je to užitečné, je sada zprostředkujících scénářů SOAP, kdy koncový bod vyžaduje, aby klienti tohoto koncového bodu zahrnuli hlavičky SOAP cílené na zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="94c5d-102">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="94c5d-103">Tento prvek konfigurace lze použít k definování vlastních hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="94c5d-103">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="94c5d-104">Položky v kolekci hlaviček koncového bodu jsou uživatelsky definované prvky XML.</span><span class="sxs-lookup"><span data-stu-id="94c5d-104">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="94c5d-105">Každý element musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="94c5d-105">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="94c5d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94c5d-106">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94c5d-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94c5d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="94c5d-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94c5d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94c5d-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="94c5d-109">Attributes</span></span>  
 <span data-ttu-id="94c5d-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="94c5d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94c5d-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94c5d-111">Child Elements</span></span>  
 <span data-ttu-id="94c5d-112">Uživatelsky definované prvky XML.</span><span class="sxs-lookup"><span data-stu-id="94c5d-112">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94c5d-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94c5d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="94c5d-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="94c5d-114">Element</span></span>|<span data-ttu-id="94c5d-115">Description</span><span class="sxs-lookup"><span data-stu-id="94c5d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="94c5d-116">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="94c5d-116">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94c5d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94c5d-117">Remarks</span></span>  
 <span data-ttu-id="94c5d-118">Volitelná záhlaví poskytují podrobnější informace adresování pro identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="94c5d-118">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="94c5d-119">Například hlavičky mohou označovat, jak zpracovat příchozí zprávu, kde koncový bod by měl poslat zprávu odpovědi, nebo kterou instanci služby použít ke zpracování příchozí zprávy od určitého uživatele, pokud je k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="94c5d-119">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c5d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="94c5d-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="94c5d-121">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="94c5d-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
