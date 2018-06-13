---
title: '&lt;issuer&gt; – &lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 459f2f43d3ef9426fbce7e0a0dd067250eb2cc4b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748569"
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="7f867-102">&lt;issuer&gt; – &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="7f867-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="7f867-103">Určuje zabezpečení Token Service (Služba tokenů zabezpečení), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7f867-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="7f867-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7f867-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7f867-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7f867-105">\<bindings></span></span>  
<span data-ttu-id="7f867-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7f867-106">\<customBinding></span></span>  
<span data-ttu-id="7f867-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="7f867-107">\<binding></span></span>  
<span data-ttu-id="7f867-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="7f867-108">\<security></span></span>  
<span data-ttu-id="7f867-109">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="7f867-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="7f867-110">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="7f867-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f867-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f867-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f867-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f867-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7f867-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f867-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f867-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f867-114">Attributes</span></span>  
  
|<span data-ttu-id="7f867-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f867-115">Attribute</span></span>|<span data-ttu-id="7f867-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7f867-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f867-117">adresa</span><span class="sxs-lookup"><span data-stu-id="7f867-117">address</span></span>|<span data-ttu-id="7f867-118">Požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="7f867-118">Required string.</span></span> <span data-ttu-id="7f867-119">Adresa URL Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7f867-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f867-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f867-120">Child Elements</span></span>  
  
|<span data-ttu-id="7f867-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f867-121">Element</span></span>|<span data-ttu-id="7f867-122">Popis</span><span class="sxs-lookup"><span data-stu-id="7f867-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f867-123">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="7f867-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="7f867-124">Kolekce hlavičky adresy pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="7f867-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="7f867-125">\<identity ></span><span class="sxs-lookup"><span data-stu-id="7f867-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7f867-126">Při použití vydané token, určuje nastavení, které umožňují klienta k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="7f867-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f867-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f867-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7f867-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f867-128">Element</span></span>|<span data-ttu-id="7f867-129">Popis</span><span class="sxs-lookup"><span data-stu-id="7f867-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f867-130">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="7f867-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="7f867-131">Určuje aktuální vystavený token.</span><span class="sxs-lookup"><span data-stu-id="7f867-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f867-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f867-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="7f867-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="7f867-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7f867-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="7f867-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7f867-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="7f867-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="7f867-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="7f867-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7f867-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="7f867-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7f867-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="7f867-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7f867-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7f867-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7f867-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7f867-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="7f867-141">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7f867-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="7f867-142">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="7f867-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
