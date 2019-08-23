---
title: <issuerMetadata> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: d9d7d41277eff1de43f717816b35fdc10d52192e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928879"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="84f13-102">\<issuerMetadata > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="84f13-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="84f13-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="84f13-103">\<system.serviceModel></span></span>  
<span data-ttu-id="84f13-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="84f13-104">\<bindings></span></span>  
<span data-ttu-id="84f13-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="84f13-105">\<customBinding></span></span>  
<span data-ttu-id="84f13-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="84f13-106">\<binding></span></span>  
<span data-ttu-id="84f13-107">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="84f13-107">\<security></span></span>  
<span data-ttu-id="84f13-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="84f13-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="84f13-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="84f13-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f13-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84f13-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84f13-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="84f13-111">Attributes and Elements</span></span>  
 <span data-ttu-id="84f13-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="84f13-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84f13-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="84f13-113">Attributes</span></span>  
  
|<span data-ttu-id="84f13-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="84f13-114">Attribute</span></span>|<span data-ttu-id="84f13-115">Popis</span><span class="sxs-lookup"><span data-stu-id="84f13-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84f13-116">adresa</span><span class="sxs-lookup"><span data-stu-id="84f13-116">address</span></span>|<span data-ttu-id="84f13-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="84f13-117">Required.</span></span> <span data-ttu-id="84f13-118">Řetězec, který určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="84f13-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="84f13-119">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="84f13-119">The address must be an absolute URI.</span></span> <span data-ttu-id="84f13-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="84f13-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84f13-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="84f13-121">Child Elements</span></span>  
  
|<span data-ttu-id="84f13-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="84f13-122">Element</span></span>|<span data-ttu-id="84f13-123">Popis</span><span class="sxs-lookup"><span data-stu-id="84f13-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84f13-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="84f13-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="84f13-125">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="84f13-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="84f13-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="84f13-126">\<identity></span></span>](identity.md)|<span data-ttu-id="84f13-127">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="84f13-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84f13-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="84f13-128">Parent Elements</span></span>  
  
|<span data-ttu-id="84f13-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="84f13-129">Element</span></span>|<span data-ttu-id="84f13-130">Popis</span><span class="sxs-lookup"><span data-stu-id="84f13-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84f13-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="84f13-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="84f13-132">Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="84f13-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84f13-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84f13-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="84f13-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="84f13-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="84f13-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="84f13-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="84f13-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="84f13-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="84f13-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="84f13-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="84f13-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="84f13-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="84f13-139">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="84f13-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="84f13-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="84f13-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="84f13-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="84f13-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="84f13-142">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="84f13-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="84f13-143">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="84f13-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
