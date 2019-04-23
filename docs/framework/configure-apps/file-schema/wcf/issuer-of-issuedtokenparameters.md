---
title: <issuer> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 690ab14ea33ba9bef29788b2eb35f86ed945ce2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113539"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="be7ec-102">\<Issuer > z \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="be7ec-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="be7ec-103">Určuje Token služba zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="be7ec-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="be7ec-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="be7ec-104">\<system.serviceModel></span></span>  
<span data-ttu-id="be7ec-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="be7ec-105">\<bindings></span></span>  
<span data-ttu-id="be7ec-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="be7ec-106">\<customBinding></span></span>  
<span data-ttu-id="be7ec-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="be7ec-107">\<binding></span></span>  
<span data-ttu-id="be7ec-108">\<security></span><span class="sxs-lookup"><span data-stu-id="be7ec-108">\<security></span></span>  
<span data-ttu-id="be7ec-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="be7ec-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="be7ec-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="be7ec-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7ec-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be7ec-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be7ec-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="be7ec-112">Attributes and Elements</span></span>  
 <span data-ttu-id="be7ec-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="be7ec-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be7ec-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="be7ec-114">Attributes</span></span>  
  
|<span data-ttu-id="be7ec-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="be7ec-115">Attribute</span></span>|<span data-ttu-id="be7ec-116">Popis</span><span class="sxs-lookup"><span data-stu-id="be7ec-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be7ec-117">adresa</span><span class="sxs-lookup"><span data-stu-id="be7ec-117">address</span></span>|<span data-ttu-id="be7ec-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="be7ec-118">Required string.</span></span> <span data-ttu-id="be7ec-119">Adresa URL služby STS.</span><span class="sxs-lookup"><span data-stu-id="be7ec-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be7ec-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="be7ec-120">Child Elements</span></span>  
  
|<span data-ttu-id="be7ec-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="be7ec-121">Element</span></span>|<span data-ttu-id="be7ec-122">Popis</span><span class="sxs-lookup"><span data-stu-id="be7ec-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be7ec-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="be7ec-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="be7ec-124">Kolekce záhlaví adres pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="be7ec-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="be7ec-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="be7ec-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="be7ec-126">Při použití vydaný token, určuje nastavení, které povoluje klient k ověření tohoto serveru.</span><span class="sxs-lookup"><span data-stu-id="be7ec-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be7ec-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="be7ec-127">Parent Elements</span></span>  
  
|<span data-ttu-id="be7ec-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="be7ec-128">Element</span></span>|<span data-ttu-id="be7ec-129">Popis</span><span class="sxs-lookup"><span data-stu-id="be7ec-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be7ec-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="be7ec-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="be7ec-131">Určuje aktuální vydaný token.</span><span class="sxs-lookup"><span data-stu-id="be7ec-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be7ec-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be7ec-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="be7ec-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="be7ec-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="be7ec-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="be7ec-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="be7ec-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="be7ec-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="be7ec-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="be7ec-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="be7ec-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="be7ec-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="be7ec-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="be7ec-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="be7ec-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="be7ec-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="be7ec-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="be7ec-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="be7ec-141">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="be7ec-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="be7ec-142">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="be7ec-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
