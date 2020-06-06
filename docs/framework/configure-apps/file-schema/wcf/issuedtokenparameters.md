---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397955"
---
# \<issuedTokenParameters>
<span data-ttu-id="820cc-101">Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="820cc-101">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="820cc-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="820cc-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="820cc-103">Typ</span><span class="sxs-lookup"><span data-stu-id="820cc-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="820cc-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="820cc-104">Attributes and Elements</span></span>  
 <span data-ttu-id="820cc-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="820cc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="820cc-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="820cc-106">Attributes</span></span>  
  
|<span data-ttu-id="820cc-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="820cc-107">Attribute</span></span>|<span data-ttu-id="820cc-108">Popis</span><span class="sxs-lookup"><span data-stu-id="820cc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="820cc-109">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="820cc-109">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="820cc-110">Určuje verze specifikací zabezpečení (WS-Security, WS-Trust, WS-Secure konverzace a WS-Security Policy), které musí vazba podporovat.</span><span class="sxs-lookup"><span data-stu-id="820cc-110">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="820cc-111">Tato hodnota je typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="820cc-111">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="820cc-112">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="820cc-112">inclusionMode</span></span>|<span data-ttu-id="820cc-113">Určuje požadavky na zařazení tokenu.</span><span class="sxs-lookup"><span data-stu-id="820cc-113">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="820cc-114">Tento atribut je typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> .</span><span class="sxs-lookup"><span data-stu-id="820cc-114">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="820cc-115">keySize</span><span class="sxs-lookup"><span data-stu-id="820cc-115">keySize</span></span>|<span data-ttu-id="820cc-116">Celé číslo, které určuje velikost klíče tokenu.</span><span class="sxs-lookup"><span data-stu-id="820cc-116">An integer that specifies the token key size.</span></span> <span data-ttu-id="820cc-117">Výchozí hodnota je 256.</span><span class="sxs-lookup"><span data-stu-id="820cc-117">The default value is 256.</span></span>|  
|<span data-ttu-id="820cc-118">keyType</span><span class="sxs-lookup"><span data-stu-id="820cc-118">keyType</span></span>|<span data-ttu-id="820cc-119">Platná hodnota <xref:System.IdentityModel.Tokens.SecurityKeyType> , která určuje typ klíče.</span><span class="sxs-lookup"><span data-stu-id="820cc-119">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="820cc-120">Výchozí formát je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="820cc-120">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="820cc-121">Typ TokenType</span><span class="sxs-lookup"><span data-stu-id="820cc-121">tokenType</span></span>|<span data-ttu-id="820cc-122">Řetězec, který určuje typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="820cc-122">A string that specifies the token type.</span></span> <span data-ttu-id="820cc-123">Ve výchozím nastavení je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="820cc-123">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="820cc-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="820cc-124">Child Elements</span></span>  
  
|<span data-ttu-id="820cc-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="820cc-125">Element</span></span>|<span data-ttu-id="820cc-126">Description</span><span class="sxs-lookup"><span data-stu-id="820cc-126">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="820cc-127">Kolekce elementů konfigurace, které určují další parametry požadavku.</span><span class="sxs-lookup"><span data-stu-id="820cc-127">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="820cc-128">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="820cc-128">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="820cc-129">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="820cc-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="820cc-130">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="820cc-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="820cc-131">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="820cc-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="820cc-132">Prvek konfigurace, který určuje koncový bod, který vydává aktuální token.</span><span class="sxs-lookup"><span data-stu-id="820cc-132">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="820cc-133">Prvek konfigurace, který určuje adresu koncového bodu metadat vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="820cc-133">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="820cc-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="820cc-134">Parent Elements</span></span>  
  
|<span data-ttu-id="820cc-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="820cc-135">Element</span></span>|<span data-ttu-id="820cc-136">Description</span><span class="sxs-lookup"><span data-stu-id="820cc-136">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="820cc-137">Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="820cc-137">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="820cc-138">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="820cc-138">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="820cc-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="820cc-139">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="820cc-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="820cc-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="820cc-141">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="820cc-141">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="820cc-142">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="820cc-142">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="820cc-143">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="820cc-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="820cc-144">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="820cc-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="820cc-145">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="820cc-145">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="820cc-146">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="820cc-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="820cc-147">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="820cc-147">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="820cc-148">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="820cc-148">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
