---
title: '&lt;issuerNameRegistry&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0c0552e06564e09832cf78afeb8f183a0a0dc94c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="399f8-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="399f8-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="399f8-103">Nakonfiguruje registru název vystavitele, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="399f8-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="399f8-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="399f8-104">\<system.identityModel></span></span>  
<span data-ttu-id="399f8-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="399f8-105">\<identityConfiguration></span></span>  
<span data-ttu-id="399f8-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="399f8-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="399f8-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="399f8-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="399f8-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="399f8-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="399f8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="399f8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="399f8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="399f8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="399f8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="399f8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="399f8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="399f8-112">Attributes</span></span>  
  
|<span data-ttu-id="399f8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="399f8-113">Attribute</span></span>|<span data-ttu-id="399f8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="399f8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="399f8-115">– typ</span><span class="sxs-lookup"><span data-stu-id="399f8-115">type</span></span>|<span data-ttu-id="399f8-116">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="399f8-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="399f8-117">Další informace o tom, jak zadat vlastní `type`, najdete v části [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="399f8-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="399f8-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="399f8-118">Child Elements</span></span>  
  
|<span data-ttu-id="399f8-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="399f8-119">Element</span></span>|<span data-ttu-id="399f8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="399f8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="399f8-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="399f8-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="399f8-122">Když `type` atribut určuje název registru vystavitelů založená na konfiguraci ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třída), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) musí být zadaný element.</span><span class="sxs-lookup"><span data-stu-id="399f8-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="399f8-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element může trvat `<add>`, `<clear>`, nebo `<remove>` elementy jako podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="399f8-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="399f8-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="399f8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="399f8-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="399f8-125">Element</span></span>|<span data-ttu-id="399f8-126">Popis</span><span class="sxs-lookup"><span data-stu-id="399f8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="399f8-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="399f8-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="399f8-128">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="399f8-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="399f8-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="399f8-129">Remarks</span></span>  
 <span data-ttu-id="399f8-130">Všechny tokeny vystavitele se ověřují pomocí registru název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="399f8-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="399f8-131">Toto je objekt, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="399f8-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="399f8-132">Registru název vystavitele je použito k přidružení klávesovými název, který kryptografických materiál, který je potřeba k ověřování podpisů tokenů vyprodukované odpovídající vystavitele.</span><span class="sxs-lookup"><span data-stu-id="399f8-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="399f8-133">Název registru vystavitele udržuje seznam vystavitelů, které jsou důvěryhodné aplikace předávající stranu.</span><span class="sxs-lookup"><span data-stu-id="399f8-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="399f8-134">Byl zadán typ registru název vystavitele, pomocí `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="399f8-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="399f8-135">`<issuerNameRegistry>` Element může obsahovat jeden nebo více podřízených elementů, které poskytují konfiguraci pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="399f8-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="399f8-136">Zadejte logiky, která zpracovává tyto podřízené elementy přepsáním <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="399f8-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="399f8-137">WIF poskytuje jednoho vystavitele název registru typ mimo pole <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="399f8-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="399f8-138">Tato třída se používá sadu důvěryhodných vystavitelů certifikátů, které jsou určené v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="399f8-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="399f8-139">Vyžaduje podřízený element konfigurace `<trustedIssuers>`, v části, která je nakonfigurována kolekce důvěryhodných vystavitelů certifikátů.</span><span class="sxs-lookup"><span data-stu-id="399f8-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="399f8-140">Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódovaný formu kryptografický otisk certifikátu a přidávání nebo odebírání z kolekce pomocí `<add>`, `<clear>`, nebo `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="399f8-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="399f8-141">`<issuerNameRegistry>` Element je reprezentována <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="399f8-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="399f8-142">Určení `<issuerNameRegistry>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="399f8-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="399f8-143">Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="399f8-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="399f8-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="399f8-144">Example</span></span>  
 <span data-ttu-id="399f8-145">Následující kód XML ukazuje, jak zadat konfiguraci na základě vystavitele název registru.</span><span class="sxs-lookup"><span data-stu-id="399f8-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="399f8-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="399f8-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
