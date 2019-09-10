---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855182"
---
# <a name="headers"></a><span data-ttu-id="238d4-101">\<> hlaviček</span><span class="sxs-lookup"><span data-stu-id="238d4-101">\<headers></span></span>
<span data-ttu-id="238d4-102">Kromě základního identifikátoru URI může koncový bod adresovat jedna nebo více hlaviček SOAP.</span><span class="sxs-lookup"><span data-stu-id="238d4-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="238d4-103">Jedna sada scénářů, kde je to užitečné, je sada zprostředkujících scénářů SOAP, kdy koncový bod vyžaduje, aby klienti tohoto koncového bodu zahrnuli hlavičky SOAP cílené na zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="238d4-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="238d4-104">Tento prvek konfigurace lze použít k definování vlastních hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="238d4-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="238d4-105">Položky v kolekci hlaviček koncového bodu jsou uživatelsky definované prvky XML.</span><span class="sxs-lookup"><span data-stu-id="238d4-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="238d4-106">Každý element musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="238d4-106">Each element has to be well-formed XML.</span></span>  
  
<span data-ttu-id="238d4-107">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="238d4-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="238d4-108">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="238d4-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="238d4-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="238d4-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="238d4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="238d4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="238d4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> hlaviček**</span><span class="sxs-lookup"><span data-stu-id="238d4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="238d4-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="238d4-112">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="238d4-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="238d4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="238d4-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="238d4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="238d4-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="238d4-115">Attributes</span></span>  
 <span data-ttu-id="238d4-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="238d4-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="238d4-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="238d4-117">Child Elements</span></span>  
 <span data-ttu-id="238d4-118">Uživatelsky definované prvky XML.</span><span class="sxs-lookup"><span data-stu-id="238d4-118">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="238d4-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="238d4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="238d4-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="238d4-120">Element</span></span>|<span data-ttu-id="238d4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="238d4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="238d4-122">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="238d4-122">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="238d4-123">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="238d4-123">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="238d4-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="238d4-124">Remarks</span></span>  
 <span data-ttu-id="238d4-125">Volitelná záhlaví poskytují podrobnější informace adresování pro identifikaci nebo interakci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="238d4-125">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="238d4-126">Například hlavičky mohou označovat, jak zpracovat příchozí zprávu, kde koncový bod by měl poslat zprávu odpovědi, nebo kterou instanci služby použít ke zpracování příchozí zprávy od určitého uživatele, pokud je k dispozici více instancí.</span><span class="sxs-lookup"><span data-stu-id="238d4-126">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238d4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="238d4-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="238d4-128">Bod Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="238d4-128">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
