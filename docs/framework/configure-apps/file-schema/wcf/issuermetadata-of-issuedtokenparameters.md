---
title: "&lt;issuerMetadata&gt; – &lt;issuedTokenParameters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee0f6b2abe6ddfa81f236da47425ae586b56f0ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="35981-102">&lt;issuerMetadata&gt; – &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="35981-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="35981-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="35981-103">\<system.serviceModel></span></span>  
<span data-ttu-id="35981-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="35981-104">\<bindings></span></span>  
<span data-ttu-id="35981-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35981-105">\<customBinding></span></span>  
<span data-ttu-id="35981-106">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="35981-106">\<binding></span></span>  
<span data-ttu-id="35981-107">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="35981-107">\<security></span></span>  
<span data-ttu-id="35981-108">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="35981-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="35981-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="35981-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35981-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35981-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35981-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="35981-111">Attributes and Elements</span></span>  
 <span data-ttu-id="35981-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="35981-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35981-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="35981-113">Attributes</span></span>  
  
|<span data-ttu-id="35981-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="35981-114">Attribute</span></span>|<span data-ttu-id="35981-115">Popis</span><span class="sxs-lookup"><span data-stu-id="35981-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35981-116">adresa</span><span class="sxs-lookup"><span data-stu-id="35981-116">address</span></span>|<span data-ttu-id="35981-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="35981-117">Required.</span></span> <span data-ttu-id="35981-118">Řetězec, který určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="35981-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="35981-119">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="35981-119">The address must be an absolute URI.</span></span> <span data-ttu-id="35981-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="35981-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35981-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="35981-121">Child Elements</span></span>  
  
|<span data-ttu-id="35981-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="35981-122">Element</span></span>|<span data-ttu-id="35981-123">Popis</span><span class="sxs-lookup"><span data-stu-id="35981-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35981-124">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="35981-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="35981-125">Kolekce hlavičky adresy.</span><span class="sxs-lookup"><span data-stu-id="35981-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="35981-126">\<identity ></span><span class="sxs-lookup"><span data-stu-id="35981-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="35981-127">Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="35981-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35981-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="35981-128">Parent Elements</span></span>  
  
|<span data-ttu-id="35981-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="35981-129">Element</span></span>|<span data-ttu-id="35981-130">Popis</span><span class="sxs-lookup"><span data-stu-id="35981-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35981-131">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="35981-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="35981-132">Určuje parametry pro token zabezpečení vydané ve scénáři federovaný zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="35981-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35981-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="35981-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="35981-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="35981-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="35981-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="35981-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="35981-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="35981-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="35981-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="35981-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="35981-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="35981-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="35981-139">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="35981-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="35981-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="35981-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="35981-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35981-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="35981-142">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="35981-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="35981-143">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="35981-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
