---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: db4e0492772d6fd0e155843422b7350aa630f713
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369679"
---
# <a name="issuernameregistry"></a><span data-ttu-id="4b212-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="4b212-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="4b212-102">Nakonfiguruje registru názvu vystavitele, který se používá obslužné rutiny v kolekci obslužná rutina tokenů.</span><span class="sxs-lookup"><span data-stu-id="4b212-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="4b212-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4b212-103">\<system.identityModel></span></span>  
<span data-ttu-id="4b212-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b212-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4b212-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4b212-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4b212-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b212-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="4b212-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="4b212-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b212-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b212-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b212-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b212-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4b212-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4b212-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b212-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b212-111">Attributes</span></span>  
  
|<span data-ttu-id="4b212-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4b212-112">Attribute</span></span>|<span data-ttu-id="4b212-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4b212-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b212-114"> – typ</span><span class="sxs-lookup"><span data-stu-id="4b212-114">type</span></span>|<span data-ttu-id="4b212-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b212-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="4b212-116">Další informace o tom, jak určit vlastní `type`, najdete v článku [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="4b212-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b212-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b212-117">Child Elements</span></span>  
  
|<span data-ttu-id="4b212-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b212-118">Element</span></span>|<span data-ttu-id="4b212-119">Popis</span><span class="sxs-lookup"><span data-stu-id="4b212-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b212-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="4b212-120">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="4b212-121">Když `type` atribut určuje registru názvu vystavitele založená na konfiguraci ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elementu musí být zadán.</span><span class="sxs-lookup"><span data-stu-id="4b212-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="4b212-122">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element může trvat `<add>`, `<clear>`, nebo `<remove>` prvků jako podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="4b212-122">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b212-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b212-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4b212-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b212-124">Element</span></span>|<span data-ttu-id="4b212-125">Popis</span><span class="sxs-lookup"><span data-stu-id="4b212-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b212-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b212-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="4b212-127">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="4b212-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b212-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b212-128">Remarks</span></span>  
 <span data-ttu-id="4b212-129">Všechny tokeny vystavitele se ověřují pomocí registru názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="4b212-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="4b212-130">Toto je objekt, který je odvozen z <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b212-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="4b212-131">Registru názvu vystavitele je použito k přidružení symbolický název, který kryptografický materiál, který je nezbytný k ověřování podpisů tokeny vytvářených odpovídající vystavitele.</span><span class="sxs-lookup"><span data-stu-id="4b212-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="4b212-132">Registru názvu vystavitele udržuje seznam vystavitelů, které jsou důvěryhodné aplikace předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="4b212-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="4b212-133">Typ registru názvu vystavitele je určen pomocí `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="4b212-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="4b212-134">`<issuerNameRegistry>` Prvek může mít jeden nebo více podřízených elementů, které poskytují konfigurace pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="4b212-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="4b212-135">Poskytuje logiku, která zpracovává tyto podřízené prvky tak, že přepíšete <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4b212-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="4b212-136">Technologie WIF umožňuje jednoho vystavitele registru typ názvu hned po spuštění <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b212-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="4b212-137">Tato třída používá sadu důvěryhodných vystavitelů certifikátů, které jsou určené v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4b212-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="4b212-138">Vyžaduje podřízený element konfigurace `<trustedIssuers>`, v rámci kolekce důvěryhodných vystavitelů certifikátů je nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="4b212-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="4b212-139">Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódované podobě kryptografický otisk certifikátu a přidání nebo odebrání z kolekce s použitím `<add>`, `<clear>`, nebo `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="4b212-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="4b212-140">`<issuerNameRegistry>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b212-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b212-141">Zadání `<issuerNameRegistry>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována.</span><span class="sxs-lookup"><span data-stu-id="4b212-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="4b212-142">Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4b212-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b212-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b212-143">Example</span></span>  
 <span data-ttu-id="4b212-144">Následující kód XML ukazuje, jak zadat vystavitele konfigurace na základě názvu registru.</span><span class="sxs-lookup"><span data-stu-id="4b212-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b212-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b212-145">See also</span></span>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
