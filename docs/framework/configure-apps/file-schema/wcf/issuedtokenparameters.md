---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 07fc2c4c52c29de1cfc9f498a6dc6b6da887b502
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925345"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="34477-101">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="34477-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="34477-102">Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="34477-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="34477-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="34477-103">\<system.serviceModel></span></span>  
<span data-ttu-id="34477-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="34477-104">\<bindings></span></span>  
<span data-ttu-id="34477-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="34477-105">\<customBinding></span></span>  
<span data-ttu-id="34477-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="34477-106">\<binding></span></span>  
<span data-ttu-id="34477-107">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="34477-107">\<security></span></span>  
<span data-ttu-id="34477-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="34477-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34477-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34477-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="34477-110">type</span><span class="sxs-lookup"><span data-stu-id="34477-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34477-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34477-111">Attributes and Elements</span></span>  
 <span data-ttu-id="34477-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34477-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34477-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="34477-113">Attributes</span></span>  
  
|<span data-ttu-id="34477-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="34477-114">Attribute</span></span>|<span data-ttu-id="34477-115">Popis</span><span class="sxs-lookup"><span data-stu-id="34477-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34477-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="34477-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="34477-117">Určuje verze specifikací zabezpečení (WS-Security, WS-Trust, WS-Secure konverzace a WS-Security Policy), které musí vazba podporovat.</span><span class="sxs-lookup"><span data-stu-id="34477-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="34477-118">Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="34477-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="34477-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="34477-119">inclusionMode</span></span>|<span data-ttu-id="34477-120">Určuje požadavky na zařazení tokenu.</span><span class="sxs-lookup"><span data-stu-id="34477-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="34477-121">Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="34477-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="34477-122">keySize</span><span class="sxs-lookup"><span data-stu-id="34477-122">keySize</span></span>|<span data-ttu-id="34477-123">Celé číslo, které určuje velikost klíče tokenu.</span><span class="sxs-lookup"><span data-stu-id="34477-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="34477-124">Výchozí hodnota je 256.</span><span class="sxs-lookup"><span data-stu-id="34477-124">The default value is 256.</span></span>|  
|<span data-ttu-id="34477-125">keyType</span><span class="sxs-lookup"><span data-stu-id="34477-125">keyType</span></span>|<span data-ttu-id="34477-126">Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> , která určuje typ klíče.</span><span class="sxs-lookup"><span data-stu-id="34477-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="34477-127">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="34477-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="34477-128">tokenType</span><span class="sxs-lookup"><span data-stu-id="34477-128">tokenType</span></span>|<span data-ttu-id="34477-129">Řetězec, který určuje typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="34477-129">A string that specifies the token type.</span></span> <span data-ttu-id="34477-130">Ve výchozím nastavení je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="34477-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34477-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="34477-131">Child Elements</span></span>  
  
|<span data-ttu-id="34477-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="34477-132">Element</span></span>|<span data-ttu-id="34477-133">Popis</span><span class="sxs-lookup"><span data-stu-id="34477-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34477-134">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="34477-134">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="34477-135">Kolekce elementů konfigurace, které určují další parametry požadavku.</span><span class="sxs-lookup"><span data-stu-id="34477-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="34477-136">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="34477-136">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="34477-137">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="34477-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="34477-138">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="34477-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="34477-139">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="34477-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="34477-140">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="34477-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="34477-141">\<issuer></span><span class="sxs-lookup"><span data-stu-id="34477-141">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="34477-142">Prvek konfigurace, který určuje koncový bod, který vydává aktuální token.</span><span class="sxs-lookup"><span data-stu-id="34477-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="34477-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="34477-143">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="34477-144">Prvek konfigurace, který určuje adresu koncového bodu metadat vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="34477-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34477-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="34477-145">Parent Elements</span></span>  
  
|<span data-ttu-id="34477-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="34477-146">Element</span></span>|<span data-ttu-id="34477-147">Popis</span><span class="sxs-lookup"><span data-stu-id="34477-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34477-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="34477-148">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="34477-149">Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="34477-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="34477-150">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="34477-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="34477-151">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="34477-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34477-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34477-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="34477-153">Vazby</span><span class="sxs-lookup"><span data-stu-id="34477-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="34477-154">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="34477-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="34477-155">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="34477-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="34477-156">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="34477-156">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="34477-157">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="34477-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="34477-158">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="34477-158">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="34477-159">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="34477-159">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="34477-160">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="34477-160">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="34477-161">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="34477-161">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="34477-162">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="34477-162">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
