---
title: '&lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 2060f98e94cec9e656420ac073204a82bc592b92
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149238"
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="4d8ad-102">&lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="4d8ad-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="4d8ad-103">Určuje parametry pro token zabezpečení vydané ve scénáři federativní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="4d8ad-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4d8ad-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4d8ad-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-105">\<bindings></span></span>  
<span data-ttu-id="4d8ad-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-106">\<customBinding></span></span>  
<span data-ttu-id="4d8ad-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-107">\<binding></span></span>  
<span data-ttu-id="4d8ad-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-108">\<security></span></span>  
<span data-ttu-id="4d8ad-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d8ad-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d8ad-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="4d8ad-111">Typ</span><span class="sxs-lookup"><span data-stu-id="4d8ad-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d8ad-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d8ad-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4d8ad-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d8ad-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d8ad-114">Attributes</span></span>  
  
|<span data-ttu-id="4d8ad-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="4d8ad-115">Attribute</span></span>|<span data-ttu-id="4d8ad-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4d8ad-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d8ad-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="4d8ad-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="4d8ad-118">Určuje verzi specifikace zabezpečení (WS-Security, WS-Trust, WS-Secure Conversation a WS-Security Policy), který musí být podporovány vazbou.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="4d8ad-119">Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="4d8ad-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="4d8ad-120">inclusionMode</span></span>|<span data-ttu-id="4d8ad-121">Určuje požadavky na zařazení tokenu.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="4d8ad-122">Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="4d8ad-123">KeySize</span><span class="sxs-lookup"><span data-stu-id="4d8ad-123">keySize</span></span>|<span data-ttu-id="4d8ad-124">Celé číslo, které určuje velikost klíče tokenu.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="4d8ad-125">Výchozí hodnota je 256.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-125">The default value is 256.</span></span>|  
|<span data-ttu-id="4d8ad-126">Typ klíče</span><span class="sxs-lookup"><span data-stu-id="4d8ad-126">keyType</span></span>|<span data-ttu-id="4d8ad-127">Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> , který určuje typ klíče.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="4d8ad-128">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="4d8ad-129">Typ TokenType</span><span class="sxs-lookup"><span data-stu-id="4d8ad-129">tokenType</span></span>|<span data-ttu-id="4d8ad-130">Řetězec, který určuje typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-130">A string that specifies the token type.</span></span> <span data-ttu-id="4d8ad-131">Ve výchozím nastavení je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="4d8ad-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d8ad-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d8ad-132">Child Elements</span></span>  
  
|<span data-ttu-id="4d8ad-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d8ad-133">Element</span></span>|<span data-ttu-id="4d8ad-134">Popis</span><span class="sxs-lookup"><span data-stu-id="4d8ad-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d8ad-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="4d8ad-136">Kolekce elementů konfigurace, které určují další parametry požadavku.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="4d8ad-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="4d8ad-138">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="4d8ad-139">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="4d8ad-140">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="4d8ad-141">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="4d8ad-142">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="4d8ad-143">Prvek konfigurace, který určuje koncový bod, který vydá aktuální token.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="4d8ad-144">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="4d8ad-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="4d8ad-145">Konfigurace element, který určuje adresu koncového bodu metadat vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d8ad-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d8ad-146">Parent Elements</span></span>  
  
|<span data-ttu-id="4d8ad-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d8ad-147">Element</span></span>|<span data-ttu-id="4d8ad-148">Popis</span><span class="sxs-lookup"><span data-stu-id="4d8ad-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d8ad-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="4d8ad-150">Určuje výchozí hodnoty pro inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="4d8ad-151">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="4d8ad-152">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4d8ad-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d8ad-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d8ad-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="4d8ad-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="4d8ad-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4d8ad-155">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="4d8ad-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4d8ad-156">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4d8ad-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4d8ad-157">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="4d8ad-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="4d8ad-158">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4d8ad-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="4d8ad-159">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="4d8ad-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="4d8ad-160">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="4d8ad-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="4d8ad-161">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="4d8ad-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="4d8ad-162">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="4d8ad-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="4d8ad-163">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="4d8ad-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
