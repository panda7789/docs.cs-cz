---
title: <issuerMetadata> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: e46e56c6285af24941a550b2c4f7dec3b441db69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764098"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="deead-102">\<issuerMetadata> of \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="deead-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="deead-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="deead-103">\<system.serviceModel></span></span>  
<span data-ttu-id="deead-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="deead-104">\<bindings></span></span>  
<span data-ttu-id="deead-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="deead-105">\<customBinding></span></span>  
<span data-ttu-id="deead-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="deead-106">\<binding></span></span>  
<span data-ttu-id="deead-107">\<security></span><span class="sxs-lookup"><span data-stu-id="deead-107">\<security></span></span>  
<span data-ttu-id="deead-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="deead-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="deead-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="deead-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deead-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="deead-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="deead-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="deead-111">Attributes and Elements</span></span>  
 <span data-ttu-id="deead-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="deead-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="deead-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="deead-113">Attributes</span></span>  
  
|<span data-ttu-id="deead-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="deead-114">Attribute</span></span>|<span data-ttu-id="deead-115">Popis</span><span class="sxs-lookup"><span data-stu-id="deead-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="deead-116">adresa</span><span class="sxs-lookup"><span data-stu-id="deead-116">address</span></span>|<span data-ttu-id="deead-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="deead-117">Required.</span></span> <span data-ttu-id="deead-118">Řetězec, který určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="deead-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="deead-119">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="deead-119">The address must be an absolute URI.</span></span> <span data-ttu-id="deead-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="deead-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="deead-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="deead-121">Child Elements</span></span>  
  
|<span data-ttu-id="deead-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="deead-122">Element</span></span>|<span data-ttu-id="deead-123">Popis</span><span class="sxs-lookup"><span data-stu-id="deead-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="deead-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="deead-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="deead-125">Kolekce záhlaví adres.</span><span class="sxs-lookup"><span data-stu-id="deead-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="deead-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="deead-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="deead-127">Identita, která umožňuje ověřování z koncového bodu jiné koncové body výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="deead-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="deead-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="deead-128">Parent Elements</span></span>  
  
|<span data-ttu-id="deead-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="deead-129">Element</span></span>|<span data-ttu-id="deead-130">Popis</span><span class="sxs-lookup"><span data-stu-id="deead-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="deead-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="deead-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="deead-132">Určuje parametry tokenu zabezpečení vydané ve scénáři federativní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="deead-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="deead-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="deead-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="deead-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="deead-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="deead-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="deead-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="deead-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="deead-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="deead-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="deead-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="deead-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="deead-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="deead-139">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="deead-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="deead-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="deead-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="deead-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="deead-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="deead-142">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="deead-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="deead-143">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="deead-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
