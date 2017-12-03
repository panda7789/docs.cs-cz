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
ms.openlocfilehash: ccd0417aeebbaf08d28457dd94a4d1698882c79e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="ca7fa-102">&lt;issuerMetadata&gt; – &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ca7fa-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="ca7fa-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ca7fa-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-104">\<bindings></span></span>  
<span data-ttu-id="ca7fa-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-105">\<customBinding></span></span>  
<span data-ttu-id="ca7fa-106">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-106">\<binding></span></span>  
<span data-ttu-id="ca7fa-107">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-107">\<security></span></span>  
<span data-ttu-id="ca7fa-108">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="ca7fa-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca7fa-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca7fa-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca7fa-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ca7fa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca7fa-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca7fa-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="ca7fa-113">Attributes</span></span>  
  
|<span data-ttu-id="ca7fa-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="ca7fa-114">Attribute</span></span>|<span data-ttu-id="ca7fa-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ca7fa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca7fa-116">adresa</span><span class="sxs-lookup"><span data-stu-id="ca7fa-116">address</span></span>|<span data-ttu-id="ca7fa-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-117">Required.</span></span> <span data-ttu-id="ca7fa-118">Řetězec, který určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="ca7fa-119">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-119">The address must be an absolute URI.</span></span> <span data-ttu-id="ca7fa-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca7fa-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ca7fa-121">Child Elements</span></span>  
  
|<span data-ttu-id="ca7fa-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca7fa-122">Element</span></span>|<span data-ttu-id="ca7fa-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ca7fa-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca7fa-124">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="ca7fa-125">Kolekce hlavičky adresy.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="ca7fa-126">\<identity ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="ca7fa-127">Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca7fa-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ca7fa-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ca7fa-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca7fa-129">Element</span></span>|<span data-ttu-id="ca7fa-130">Popis</span><span class="sxs-lookup"><span data-stu-id="ca7fa-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca7fa-131">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="ca7fa-132">Určuje parametry pro token zabezpečení vydané ve scénáři federovaný zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ca7fa-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca7fa-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca7fa-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="ca7fa-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="ca7fa-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="ca7fa-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="ca7fa-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="ca7fa-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="ca7fa-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="ca7fa-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="ca7fa-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="ca7fa-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="ca7fa-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ca7fa-139">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="ca7fa-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="ca7fa-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="ca7fa-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="ca7fa-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ca7fa-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="ca7fa-142">Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ca7fa-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="ca7fa-143">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="ca7fa-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
