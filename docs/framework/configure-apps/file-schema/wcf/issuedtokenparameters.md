---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397955"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="d05d1-101">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="d05d1-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="d05d1-102">Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d05d1-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
<span data-ttu-id="d05d1-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d05d1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d05d1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d05d1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d05d1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d05d1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d05d1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="d05d1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="d05d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="d05d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d05d1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="d05d1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="d05d1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedTokenParameters >**</span><span class="sxs-lookup"><span data-stu-id="d05d1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d05d1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d05d1-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="d05d1-111">type</span><span class="sxs-lookup"><span data-stu-id="d05d1-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d05d1-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d05d1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d05d1-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d05d1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d05d1-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d05d1-114">Attributes</span></span>  
  
|<span data-ttu-id="d05d1-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d05d1-115">Attribute</span></span>|<span data-ttu-id="d05d1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d05d1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d05d1-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="d05d1-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="d05d1-118">Určuje verze specifikací zabezpečení (WS-Security, WS-Trust, WS-Secure konverzace a WS-Security Policy), které musí vazba podporovat.</span><span class="sxs-lookup"><span data-stu-id="d05d1-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="d05d1-119">Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="d05d1-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="d05d1-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="d05d1-120">inclusionMode</span></span>|<span data-ttu-id="d05d1-121">Určuje požadavky na zařazení tokenu.</span><span class="sxs-lookup"><span data-stu-id="d05d1-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="d05d1-122">Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="d05d1-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="d05d1-123">keySize</span><span class="sxs-lookup"><span data-stu-id="d05d1-123">keySize</span></span>|<span data-ttu-id="d05d1-124">Celé číslo, které určuje velikost klíče tokenu.</span><span class="sxs-lookup"><span data-stu-id="d05d1-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="d05d1-125">Výchozí hodnota je 256.</span><span class="sxs-lookup"><span data-stu-id="d05d1-125">The default value is 256.</span></span>|  
|<span data-ttu-id="d05d1-126">keyType</span><span class="sxs-lookup"><span data-stu-id="d05d1-126">keyType</span></span>|<span data-ttu-id="d05d1-127">Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> , která určuje typ klíče.</span><span class="sxs-lookup"><span data-stu-id="d05d1-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="d05d1-128">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="d05d1-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="d05d1-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="d05d1-129">tokenType</span></span>|<span data-ttu-id="d05d1-130">Řetězec, který určuje typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="d05d1-130">A string that specifies the token type.</span></span> <span data-ttu-id="d05d1-131">Ve výchozím nastavení je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="d05d1-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d05d1-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d05d1-132">Child Elements</span></span>  
  
|<span data-ttu-id="d05d1-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d05d1-133">Element</span></span>|<span data-ttu-id="d05d1-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d05d1-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d05d1-135">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="d05d1-135">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="d05d1-136">Kolekce elementů konfigurace, které určují další parametry požadavku.</span><span class="sxs-lookup"><span data-stu-id="d05d1-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="d05d1-137">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d05d1-137">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="d05d1-138">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="d05d1-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="d05d1-139">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d05d1-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d05d1-140">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="d05d1-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d05d1-141">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="d05d1-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="d05d1-142">\<issuer></span><span class="sxs-lookup"><span data-stu-id="d05d1-142">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="d05d1-143">Prvek konfigurace, který určuje koncový bod, který vydává aktuální token.</span><span class="sxs-lookup"><span data-stu-id="d05d1-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="d05d1-144">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="d05d1-144">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="d05d1-145">Prvek konfigurace, který určuje adresu koncového bodu metadat vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="d05d1-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d05d1-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d05d1-146">Parent Elements</span></span>  
  
|<span data-ttu-id="d05d1-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="d05d1-147">Element</span></span>|<span data-ttu-id="d05d1-148">Popis</span><span class="sxs-lookup"><span data-stu-id="d05d1-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d05d1-149">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="d05d1-149">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="d05d1-150">Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="d05d1-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="d05d1-151">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d05d1-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="d05d1-152">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="d05d1-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d05d1-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d05d1-153">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d05d1-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="d05d1-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d05d1-155">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d05d1-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d05d1-156">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d05d1-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d05d1-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d05d1-157">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="d05d1-158">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d05d1-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="d05d1-159">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d05d1-159">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="d05d1-160">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d05d1-160">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d05d1-161">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d05d1-161">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d05d1-162">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d05d1-162">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d05d1-163">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d05d1-163">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
