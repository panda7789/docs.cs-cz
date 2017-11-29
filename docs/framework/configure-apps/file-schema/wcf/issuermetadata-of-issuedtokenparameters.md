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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8df1ffb74c59bfed2b9fa2f1e87e7669fe3ad9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="d9ec5-102">&lt;issuerMetadata&gt; – &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="d9ec5-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="d9ec5-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d9ec5-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-104">\<bindings></span></span>  
<span data-ttu-id="d9ec5-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-105">\<customBinding></span></span>  
<span data-ttu-id="d9ec5-106">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-106">\<binding></span></span>  
<span data-ttu-id="d9ec5-107">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-107">\<security></span></span>  
<span data-ttu-id="d9ec5-108">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="d9ec5-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ec5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9ec5-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9ec5-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d9ec5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d9ec5-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9ec5-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9ec5-113">Attributes</span></span>  
  
|<span data-ttu-id="d9ec5-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d9ec5-114">Attribute</span></span>|<span data-ttu-id="d9ec5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d9ec5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9ec5-116">adresa</span><span class="sxs-lookup"><span data-stu-id="d9ec5-116">address</span></span>|<span data-ttu-id="d9ec5-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-117">Required.</span></span> <span data-ttu-id="d9ec5-118">Řetězec, který určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="d9ec5-119">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-119">The address must be an absolute URI.</span></span> <span data-ttu-id="d9ec5-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9ec5-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d9ec5-121">Child Elements</span></span>  
  
|<span data-ttu-id="d9ec5-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9ec5-122">Element</span></span>|<span data-ttu-id="d9ec5-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d9ec5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9ec5-124">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="d9ec5-125">Kolekce hlavičky adresy.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="d9ec5-126">\<identity ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="d9ec5-127">Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9ec5-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d9ec5-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d9ec5-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9ec5-129">Element</span></span>|<span data-ttu-id="d9ec5-130">Popis</span><span class="sxs-lookup"><span data-stu-id="d9ec5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9ec5-131">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="d9ec5-132">Určuje parametry pro token zabezpečení vydané ve scénáři federovaný zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d9ec5-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9ec5-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9ec5-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="d9ec5-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d9ec5-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d9ec5-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d9ec5-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d9ec5-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d9ec5-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="d9ec5-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d9ec5-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d9ec5-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="d9ec5-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d9ec5-139">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="d9ec5-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="d9ec5-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d9ec5-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="d9ec5-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d9ec5-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="d9ec5-142">Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d9ec5-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="d9ec5-143">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d9ec5-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
