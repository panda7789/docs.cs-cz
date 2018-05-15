---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b695cc6d66e5b9e45bb6a5fd22d594bc22ea3cba
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="87472-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="87472-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="87472-103">Nakonfiguruje registru název vystavitele, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="87472-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="87472-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="87472-104">\<system.identityModel></span></span>  
<span data-ttu-id="87472-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="87472-105">\<identityConfiguration></span></span>  
<span data-ttu-id="87472-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="87472-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="87472-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="87472-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="87472-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="87472-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87472-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87472-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87472-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87472-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87472-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87472-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87472-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="87472-112">Attributes</span></span>  
  
|<span data-ttu-id="87472-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="87472-113">Attribute</span></span>|<span data-ttu-id="87472-114">Popis</span><span class="sxs-lookup"><span data-stu-id="87472-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87472-115">– typ</span><span class="sxs-lookup"><span data-stu-id="87472-115">type</span></span>|<span data-ttu-id="87472-116">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="87472-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="87472-117">Další informace o tom, jak zadat vlastní `type`, najdete v části [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="87472-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87472-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87472-118">Child Elements</span></span>  
  
|<span data-ttu-id="87472-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="87472-119">Element</span></span>|<span data-ttu-id="87472-120">Popis</span><span class="sxs-lookup"><span data-stu-id="87472-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87472-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="87472-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="87472-122">Když `type` atribut určuje název registru vystavitelů založená na konfiguraci ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třída), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) musí být zadaný element.</span><span class="sxs-lookup"><span data-stu-id="87472-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="87472-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element může trvat `<add>`, `<clear>`, nebo `<remove>` elementy jako podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="87472-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87472-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87472-124">Parent Elements</span></span>  
  
|<span data-ttu-id="87472-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="87472-125">Element</span></span>|<span data-ttu-id="87472-126">Popis</span><span class="sxs-lookup"><span data-stu-id="87472-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87472-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="87472-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="87472-128">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="87472-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87472-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87472-129">Remarks</span></span>  
 <span data-ttu-id="87472-130">Všechny tokeny vystavitele se ověřují pomocí registru název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="87472-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="87472-131">Toto je objekt, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="87472-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="87472-132">Registru název vystavitele je použito k přidružení klávesovými název, který kryptografických materiál, který je potřeba k ověřování podpisů tokenů vyprodukované odpovídající vystavitele.</span><span class="sxs-lookup"><span data-stu-id="87472-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="87472-133">Název registru vystavitele udržuje seznam vystavitelů, které jsou důvěryhodné aplikace předávající stranu.</span><span class="sxs-lookup"><span data-stu-id="87472-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="87472-134">Byl zadán typ registru název vystavitele, pomocí `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="87472-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="87472-135">`<issuerNameRegistry>` Element může obsahovat jeden nebo více podřízených elementů, které poskytují konfiguraci pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="87472-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="87472-136">Zadejte logiky, která zpracovává tyto podřízené elementy přepsáním <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="87472-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="87472-137">WIF poskytuje jednoho vystavitele název registru typ mimo pole <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="87472-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="87472-138">Tato třída se používá sadu důvěryhodných vystavitelů certifikátů, které jsou určené v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="87472-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="87472-139">Vyžaduje podřízený element konfigurace `<trustedIssuers>`, v části, která je nakonfigurována kolekce důvěryhodných vystavitelů certifikátů.</span><span class="sxs-lookup"><span data-stu-id="87472-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="87472-140">Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódovaný formu kryptografický otisk certifikátu a přidávání nebo odebírání z kolekce pomocí `<add>`, `<clear>`, nebo `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="87472-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="87472-141">`<issuerNameRegistry>` Element je reprezentována <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="87472-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87472-142">Určení `<issuerNameRegistry>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="87472-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="87472-143">Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="87472-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87472-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="87472-144">Example</span></span>  
 <span data-ttu-id="87472-145">Následující kód XML ukazuje, jak zadat konfiguraci na základě vystavitele název registru.</span><span class="sxs-lookup"><span data-stu-id="87472-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87472-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="87472-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
