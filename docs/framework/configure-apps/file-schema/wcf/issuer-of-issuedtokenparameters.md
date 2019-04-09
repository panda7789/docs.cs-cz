---
title: <issuer> of <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 690ab14ea33ba9bef29788b2eb35f86ed945ce2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113539"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="4b0da-102">\<Issuer > z \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="4b0da-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="4b0da-103">Určuje Token služba zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4b0da-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="4b0da-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4b0da-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4b0da-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4b0da-105">\<bindings></span></span>  
<span data-ttu-id="4b0da-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4b0da-106">\<customBinding></span></span>  
<span data-ttu-id="4b0da-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4b0da-107">\<binding></span></span>  
<span data-ttu-id="4b0da-108">\<security></span><span class="sxs-lookup"><span data-stu-id="4b0da-108">\<security></span></span>  
<span data-ttu-id="4b0da-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="4b0da-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="4b0da-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="4b0da-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0da-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b0da-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b0da-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b0da-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4b0da-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b0da-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b0da-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b0da-114">Attributes</span></span>  
  
|<span data-ttu-id="4b0da-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="4b0da-115">Attribute</span></span>|<span data-ttu-id="4b0da-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4b0da-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b0da-117">adresa</span><span class="sxs-lookup"><span data-stu-id="4b0da-117">address</span></span>|<span data-ttu-id="4b0da-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="4b0da-118">Required string.</span></span> <span data-ttu-id="4b0da-119">Adresa URL služby STS.</span><span class="sxs-lookup"><span data-stu-id="4b0da-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b0da-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b0da-120">Child Elements</span></span>  
  
|<span data-ttu-id="4b0da-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b0da-121">Element</span></span>|<span data-ttu-id="4b0da-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4b0da-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b0da-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="4b0da-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="4b0da-124">Kolekce záhlaví adres pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="4b0da-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="4b0da-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="4b0da-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4b0da-126">Při použití vydaný token, určuje nastavení, které povoluje klient k ověření tohoto serveru.</span><span class="sxs-lookup"><span data-stu-id="4b0da-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b0da-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b0da-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4b0da-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b0da-128">Element</span></span>|<span data-ttu-id="4b0da-129">Popis</span><span class="sxs-lookup"><span data-stu-id="4b0da-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b0da-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="4b0da-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="4b0da-131">Určuje aktuální vydaný token.</span><span class="sxs-lookup"><span data-stu-id="4b0da-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b0da-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b0da-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4b0da-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="4b0da-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4b0da-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="4b0da-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4b0da-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="4b0da-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="4b0da-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="4b0da-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4b0da-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="4b0da-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4b0da-138">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="4b0da-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4b0da-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4b0da-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4b0da-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4b0da-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="4b0da-141">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4b0da-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="4b0da-142">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="4b0da-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
