---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: ae263a4590cc523c64306ff5d53e54b5190ca510
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791643"
---
# <a name="issuernameregistry"></a><span data-ttu-id="08d43-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="08d43-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="08d43-102">Nakonfiguruje registru názvu vystavitele, který se používá obslužné rutiny v kolekci obslužná rutina tokenů.</span><span class="sxs-lookup"><span data-stu-id="08d43-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="08d43-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="08d43-103">\<system.identityModel></span></span>  
<span data-ttu-id="08d43-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="08d43-104">\<identityConfiguration></span></span>  
<span data-ttu-id="08d43-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="08d43-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="08d43-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="08d43-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="08d43-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="08d43-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d43-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08d43-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08d43-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="08d43-109">Attributes and Elements</span></span>  
 <span data-ttu-id="08d43-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="08d43-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08d43-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="08d43-111">Attributes</span></span>  
  
|<span data-ttu-id="08d43-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="08d43-112">Attribute</span></span>|<span data-ttu-id="08d43-113">Popis</span><span class="sxs-lookup"><span data-stu-id="08d43-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08d43-114"> – typ</span><span class="sxs-lookup"><span data-stu-id="08d43-114">type</span></span>|<span data-ttu-id="08d43-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="08d43-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="08d43-116">Další informace o tom, jak určit vlastní `type`, najdete v článku [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="08d43-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08d43-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="08d43-117">Child Elements</span></span>  
  
|<span data-ttu-id="08d43-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="08d43-118">Element</span></span>|<span data-ttu-id="08d43-119">Popis</span><span class="sxs-lookup"><span data-stu-id="08d43-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08d43-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="08d43-120">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="08d43-121">Když `type` atribut určuje registru názvu vystavitele založená na konfiguraci ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elementu musí být zadán.</span><span class="sxs-lookup"><span data-stu-id="08d43-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="08d43-122">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element může trvat `<add>`, `<clear>`, nebo `<remove>` prvků jako podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="08d43-122">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08d43-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08d43-123">Parent Elements</span></span>  
  
|<span data-ttu-id="08d43-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="08d43-124">Element</span></span>|<span data-ttu-id="08d43-125">Popis</span><span class="sxs-lookup"><span data-stu-id="08d43-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08d43-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="08d43-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="08d43-127">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="08d43-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d43-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08d43-128">Remarks</span></span>  
 <span data-ttu-id="08d43-129">Všechny tokeny vystavitele se ověřují pomocí registru názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="08d43-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="08d43-130">Toto je objekt, který je odvozen z <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="08d43-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="08d43-131">Registru názvu vystavitele je použito k přidružení symbolický název, který kryptografický materiál, který je nezbytný k ověřování podpisů tokeny vytvářených odpovídající vystavitele.</span><span class="sxs-lookup"><span data-stu-id="08d43-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="08d43-132">Registru názvu vystavitele udržuje seznam vystavitelů, které jsou důvěryhodné aplikace předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="08d43-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="08d43-133">Typ registru názvu vystavitele je určen pomocí `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="08d43-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="08d43-134">`<issuerNameRegistry>` Prvek může mít jeden nebo více podřízených elementů, které poskytují konfigurace pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="08d43-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="08d43-135">Poskytuje logiku, která zpracovává tyto podřízené prvky tak, že přepíšete <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="08d43-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="08d43-136">Technologie WIF umožňuje jednoho vystavitele registru typ názvu hned po spuštění <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="08d43-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="08d43-137">Tato třída používá sadu důvěryhodných vystavitelů certifikátů, které jsou určené v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="08d43-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="08d43-138">Vyžaduje podřízený element konfigurace `<trustedIssuers>`, v rámci kolekce důvěryhodných vystavitelů certifikátů je nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="08d43-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="08d43-139">Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódované podobě kryptografický otisk certifikátu a přidání nebo odebrání z kolekce s použitím `<add>`, `<clear>`, nebo `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="08d43-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="08d43-140">`<issuerNameRegistry>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="08d43-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08d43-141">Zadání `<issuerNameRegistry>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována.</span><span class="sxs-lookup"><span data-stu-id="08d43-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="08d43-142">Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="08d43-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08d43-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="08d43-143">Example</span></span>  
 <span data-ttu-id="08d43-144">Následující kód XML ukazuje, jak zadat vystavitele konfigurace na základě názvu registru.</span><span class="sxs-lookup"><span data-stu-id="08d43-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08d43-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08d43-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
