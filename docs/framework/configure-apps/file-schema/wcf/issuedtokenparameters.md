---
title: "&lt;– issuedTokenParameters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac725e0c4fe590623ac82ec45bcf669a2e57179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="54584-102">&lt;– issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="54584-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="54584-103">Určuje parametry pro token zabezpečení vydané ve scénáři federovaný zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54584-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="54584-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="54584-104">\<system.serviceModel></span></span>  
<span data-ttu-id="54584-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="54584-105">\<bindings></span></span>  
<span data-ttu-id="54584-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="54584-106">\<customBinding></span></span>  
<span data-ttu-id="54584-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="54584-107">\<binding></span></span>  
<span data-ttu-id="54584-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="54584-108">\<security></span></span>  
<span data-ttu-id="54584-109">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="54584-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54584-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54584-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="54584-111">Typ</span><span class="sxs-lookup"><span data-stu-id="54584-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54584-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="54584-112">Attributes and Elements</span></span>  
 <span data-ttu-id="54584-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="54584-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54584-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="54584-114">Attributes</span></span>  
  
|<span data-ttu-id="54584-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="54584-115">Attribute</span></span>|<span data-ttu-id="54584-116">Popis</span><span class="sxs-lookup"><span data-stu-id="54584-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54584-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="54584-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="54584-118">Určuje bezpečnostní specifikací verze (WS-zabezpečení, WS-Trust, WS-zabezpečené konverzace a zásady zabezpečení WS), musí být podporována vazba.</span><span class="sxs-lookup"><span data-stu-id="54584-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="54584-119">Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="54584-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="54584-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="54584-120">inclusionMode</span></span>|<span data-ttu-id="54584-121">Určuje požadavky na zařazení tokenu.</span><span class="sxs-lookup"><span data-stu-id="54584-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="54584-122">Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="54584-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="54584-123">Velikost klíče</span><span class="sxs-lookup"><span data-stu-id="54584-123">keySize</span></span>|<span data-ttu-id="54584-124">Celé číslo, které určuje velikost klíče tokenu.</span><span class="sxs-lookup"><span data-stu-id="54584-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="54584-125">Výchozí hodnota je 256.</span><span class="sxs-lookup"><span data-stu-id="54584-125">The default value is 256.</span></span>|  
|<span data-ttu-id="54584-126">Typ_klíče.</span><span class="sxs-lookup"><span data-stu-id="54584-126">keyType</span></span>|<span data-ttu-id="54584-127">Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> určující typ klíče.</span><span class="sxs-lookup"><span data-stu-id="54584-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="54584-128">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="54584-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="54584-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="54584-129">tokenType</span></span>|<span data-ttu-id="54584-130">Řetězec, který určuje typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="54584-130">A string that specifies the token type.</span></span> <span data-ttu-id="54584-131">Výchozí hodnota je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="54584-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54584-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="54584-132">Child Elements</span></span>  
  
|<span data-ttu-id="54584-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="54584-133">Element</span></span>|<span data-ttu-id="54584-134">Popis</span><span class="sxs-lookup"><span data-stu-id="54584-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54584-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="54584-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="54584-136">Kolekce konfigurační prvky, které zadejte parametry další požadavek.</span><span class="sxs-lookup"><span data-stu-id="54584-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="54584-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="54584-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="54584-138">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="54584-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="54584-139">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="54584-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="54584-140">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="54584-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="54584-141">Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="54584-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="54584-142">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="54584-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="54584-143">Konfigurace element, který určuje koncového bodu, který vydá aktuální token.</span><span class="sxs-lookup"><span data-stu-id="54584-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="54584-144">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="54584-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="54584-145">Konfigurace element, který určuje adresa koncového bodu metadat vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="54584-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54584-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="54584-146">Parent Elements</span></span>  
  
|<span data-ttu-id="54584-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="54584-147">Element</span></span>|<span data-ttu-id="54584-148">Popis</span><span class="sxs-lookup"><span data-stu-id="54584-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54584-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="54584-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="54584-150">Určuje výchozí hodnoty používané pro inicializaci služby Zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="54584-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="54584-151">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="54584-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="54584-152">Určuje možnosti zabezpečení u vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="54584-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54584-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="54584-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="54584-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="54584-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="54584-155">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="54584-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="54584-156">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="54584-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="54584-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="54584-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="54584-158">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="54584-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="54584-159">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="54584-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="54584-160">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="54584-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="54584-161">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="54584-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="54584-162">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="54584-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="54584-163">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="54584-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
