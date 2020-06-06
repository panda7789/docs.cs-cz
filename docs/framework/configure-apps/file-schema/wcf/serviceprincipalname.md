---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854989"
---
# \<servicePrincipalName>
<span data-ttu-id="fc187-101">Určuje identitu služby podle hlavního názvu služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="fc187-101">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="fc187-102">Další informace o nastavení hlavního názvu služby (SPN) najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fc187-102">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="fc187-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc187-103">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc187-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc187-104">Attributes and Elements</span></span>  
 <span data-ttu-id="fc187-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc187-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc187-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc187-106">Attributes</span></span>  
  
|<span data-ttu-id="fc187-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="fc187-107">Attribute</span></span>|<span data-ttu-id="fc187-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fc187-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc187-109">hodnota</span><span class="sxs-lookup"><span data-stu-id="fc187-109">value</span></span>|<span data-ttu-id="fc187-110">Název, kterým klient jednoznačně identifikuje instanci služby.</span><span class="sxs-lookup"><span data-stu-id="fc187-110">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="fc187-111">Pokud instalujete více instancí služby na počítačích v rámci doménové struktury, každá instance musí mít vlastní hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="fc187-111">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="fc187-112">Pokud existuje více názvů, které mohou klienti použít k ověřování, může mít daná instance služby více názvů SPN.</span><span class="sxs-lookup"><span data-stu-id="fc187-112">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc187-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc187-113">Child Elements</span></span>  
 <span data-ttu-id="fc187-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc187-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc187-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc187-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fc187-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc187-116">Element</span></span>|<span data-ttu-id="fc187-117">Description</span><span class="sxs-lookup"><span data-stu-id="fc187-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="fc187-118">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="fc187-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc187-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc187-119">Remarks</span></span>  
 <span data-ttu-id="fc187-120">Klient zabezpečeného Windows Communication Foundation (WCF), který se připojuje ke koncovému bodu s touto identitou, používá hlavní název služby (SPN) při provádění ověřování SSPI s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="fc187-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc187-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc187-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="fc187-122">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="fc187-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
