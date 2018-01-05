---
title: "&lt;issuer&gt; – &lt;issuedTokenParameters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b31214f5552283c40cdc93e6e72a374bbfef9997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="59194-102">&lt;issuer&gt; – &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="59194-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="59194-103">Určuje zabezpečení Token Service (Služba tokenů zabezpečení), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59194-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="59194-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="59194-104">\<system.serviceModel></span></span>  
<span data-ttu-id="59194-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="59194-105">\<bindings></span></span>  
<span data-ttu-id="59194-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="59194-106">\<customBinding></span></span>  
<span data-ttu-id="59194-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="59194-107">\<binding></span></span>  
<span data-ttu-id="59194-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="59194-108">\<security></span></span>  
<span data-ttu-id="59194-109">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="59194-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="59194-110">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="59194-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59194-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59194-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59194-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59194-112">Attributes and Elements</span></span>  
 <span data-ttu-id="59194-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59194-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59194-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="59194-114">Attributes</span></span>  
  
|<span data-ttu-id="59194-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="59194-115">Attribute</span></span>|<span data-ttu-id="59194-116">Popis</span><span class="sxs-lookup"><span data-stu-id="59194-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59194-117">adresa</span><span class="sxs-lookup"><span data-stu-id="59194-117">address</span></span>|<span data-ttu-id="59194-118">Požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="59194-118">Required string.</span></span> <span data-ttu-id="59194-119">Adresa URL Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59194-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59194-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59194-120">Child Elements</span></span>  
  
|<span data-ttu-id="59194-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="59194-121">Element</span></span>|<span data-ttu-id="59194-122">Popis</span><span class="sxs-lookup"><span data-stu-id="59194-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59194-123">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="59194-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="59194-124">Kolekce hlavičky adresy pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="59194-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="59194-125">\<identity ></span><span class="sxs-lookup"><span data-stu-id="59194-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="59194-126">Při použití vydané token, určuje nastavení, které umožňují klienta k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="59194-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59194-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59194-127">Parent Elements</span></span>  
  
|<span data-ttu-id="59194-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="59194-128">Element</span></span>|<span data-ttu-id="59194-129">Popis</span><span class="sxs-lookup"><span data-stu-id="59194-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59194-130">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="59194-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="59194-131">Určuje aktuální vystavený token.</span><span class="sxs-lookup"><span data-stu-id="59194-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59194-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="59194-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="59194-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="59194-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="59194-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="59194-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="59194-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="59194-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="59194-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="59194-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="59194-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="59194-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="59194-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="59194-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="59194-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="59194-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="59194-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="59194-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="59194-141">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="59194-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="59194-142">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="59194-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
