---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6b40bd6edd27f4c3b4b530387417311e1f93a921
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283592"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="3592d-101">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="3592d-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="3592d-102">Určuje parametry pro token zabezpečení vydané ve scénáři federativní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3592d-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="3592d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3592d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3592d-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3592d-104">\<bindings></span></span>  
<span data-ttu-id="3592d-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3592d-105">\<customBinding></span></span>  
<span data-ttu-id="3592d-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3592d-106">\<binding></span></span>  
<span data-ttu-id="3592d-107">\<security></span><span class="sxs-lookup"><span data-stu-id="3592d-107">\<security></span></span>  
<span data-ttu-id="3592d-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="3592d-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3592d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3592d-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="3592d-110">Typ</span><span class="sxs-lookup"><span data-stu-id="3592d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3592d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3592d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3592d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3592d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3592d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3592d-113">Attributes</span></span>  
  
|<span data-ttu-id="3592d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3592d-114">Attribute</span></span>|<span data-ttu-id="3592d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3592d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3592d-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="3592d-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="3592d-117">Určuje verzi specifikace zabezpečení (WS-Security, WS-Trust, WS-Secure Conversation a WS-Security Policy), který musí být podporovány vazbou.</span><span class="sxs-lookup"><span data-stu-id="3592d-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="3592d-118">Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="3592d-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="3592d-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="3592d-119">inclusionMode</span></span>|<span data-ttu-id="3592d-120">Určuje požadavky na zařazení tokenu.</span><span class="sxs-lookup"><span data-stu-id="3592d-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="3592d-121">Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="3592d-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="3592d-122">KeySize</span><span class="sxs-lookup"><span data-stu-id="3592d-122">keySize</span></span>|<span data-ttu-id="3592d-123">Celé číslo, které určuje velikost klíče tokenu.</span><span class="sxs-lookup"><span data-stu-id="3592d-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="3592d-124">Výchozí hodnota je 256.</span><span class="sxs-lookup"><span data-stu-id="3592d-124">The default value is 256.</span></span>|  
|<span data-ttu-id="3592d-125">keyType</span><span class="sxs-lookup"><span data-stu-id="3592d-125">keyType</span></span>|<span data-ttu-id="3592d-126">Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> , který určuje typ klíče.</span><span class="sxs-lookup"><span data-stu-id="3592d-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="3592d-127">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="3592d-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="3592d-128">tokenType</span><span class="sxs-lookup"><span data-stu-id="3592d-128">tokenType</span></span>|<span data-ttu-id="3592d-129">Řetězec, který určuje typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="3592d-129">A string that specifies the token type.</span></span> <span data-ttu-id="3592d-130">Ve výchozím nastavení je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="3592d-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3592d-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3592d-131">Child Elements</span></span>  
  
|<span data-ttu-id="3592d-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="3592d-132">Element</span></span>|<span data-ttu-id="3592d-133">Popis</span><span class="sxs-lookup"><span data-stu-id="3592d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3592d-134">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="3592d-134">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="3592d-135">Kolekce elementů konfigurace, které určují další parametry požadavku.</span><span class="sxs-lookup"><span data-stu-id="3592d-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="3592d-136">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="3592d-136">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="3592d-137">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="3592d-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="3592d-138">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="3592d-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3592d-139">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3592d-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3592d-140">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="3592d-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="3592d-141">\<issuer></span><span class="sxs-lookup"><span data-stu-id="3592d-141">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="3592d-142">Prvek konfigurace, který určuje koncový bod, který vydá aktuální token.</span><span class="sxs-lookup"><span data-stu-id="3592d-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="3592d-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="3592d-143">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="3592d-144">Konfigurace element, který určuje adresu koncového bodu metadat vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="3592d-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3592d-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3592d-145">Parent Elements</span></span>  
  
|<span data-ttu-id="3592d-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="3592d-146">Element</span></span>|<span data-ttu-id="3592d-147">Popis</span><span class="sxs-lookup"><span data-stu-id="3592d-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3592d-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="3592d-148">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="3592d-149">Určuje výchozí hodnoty pro inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="3592d-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="3592d-150">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3592d-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="3592d-151">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3592d-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3592d-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3592d-152">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3592d-153">Vazby</span><span class="sxs-lookup"><span data-stu-id="3592d-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3592d-154">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="3592d-154">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3592d-155">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3592d-155">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3592d-156">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3592d-156">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="3592d-157">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3592d-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="3592d-158">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="3592d-158">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="3592d-159">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="3592d-159">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3592d-160">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="3592d-160">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3592d-161">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="3592d-161">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3592d-162">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="3592d-162">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
