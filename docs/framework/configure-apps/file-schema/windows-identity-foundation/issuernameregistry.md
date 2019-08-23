---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942670"
---
# <a name="issuernameregistry"></a><span data-ttu-id="32ae2-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="32ae2-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="32ae2-102">Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="32ae2-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="32ae2-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="32ae2-103">\<system.identityModel></span></span>  
<span data-ttu-id="32ae2-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="32ae2-104">\<identityConfiguration></span></span>  
<span data-ttu-id="32ae2-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="32ae2-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="32ae2-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="32ae2-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="32ae2-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="32ae2-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ae2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32ae2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32ae2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32ae2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="32ae2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32ae2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32ae2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="32ae2-111">Attributes</span></span>  
  
|<span data-ttu-id="32ae2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="32ae2-112">Attribute</span></span>|<span data-ttu-id="32ae2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="32ae2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32ae2-114">– typ</span><span class="sxs-lookup"><span data-stu-id="32ae2-114">type</span></span>|<span data-ttu-id="32ae2-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="32ae2-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="32ae2-116">Další informace o tom, jak zadat vlastní `type`, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="32ae2-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32ae2-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32ae2-117">Child Elements</span></span>  
  
|<span data-ttu-id="32ae2-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="32ae2-118">Element</span></span>|<span data-ttu-id="32ae2-119">Popis</span><span class="sxs-lookup"><span data-stu-id="32ae2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32ae2-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="32ae2-120">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="32ae2-121">Pokud atribut určuje registr názvu vystavitele založený na konfiguraci <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (třída), [ \<](trustedissuers.md) musí být zadaný element trustedIssuers >. `type`</span><span class="sxs-lookup"><span data-stu-id="32ae2-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="32ae2-122">Element trustedIssuers > může převzít `<add>`, `<clear>`nebo `<remove>` prvky jako podřízené prvky. [ \<](trustedissuers.md)</span><span class="sxs-lookup"><span data-stu-id="32ae2-122">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32ae2-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32ae2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="32ae2-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="32ae2-124">Element</span></span>|<span data-ttu-id="32ae2-125">Popis</span><span class="sxs-lookup"><span data-stu-id="32ae2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32ae2-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="32ae2-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="32ae2-127">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="32ae2-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32ae2-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32ae2-128">Remarks</span></span>  
 <span data-ttu-id="32ae2-129">Všechny tokeny vystavitele se ověřují pomocí registru názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="32ae2-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="32ae2-130">Toto je objekt, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="32ae2-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="32ae2-131">Registr názvu vystavitele se používá k přidružení symbolického názvu k kryptografickému materiálu, který je nutný k ověření podpisů tokenů vyprodukovaných odpovídajícím vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="32ae2-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="32ae2-132">Registr názvů vystavitele uchovává seznam vystavitelů, které jsou důvěryhodné pro aplikaci předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="32ae2-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="32ae2-133">Typ registru názvu vystavitele je zadaný pomocí `type` atributu.</span><span class="sxs-lookup"><span data-stu-id="32ae2-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="32ae2-134">`<issuerNameRegistry>` Element může mít jeden nebo více podřízených elementů, které poskytují konfiguraci pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="32ae2-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="32ae2-135">Zadáte logiku, která zpracovává tyto podřízené prvky přepsáním <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="32ae2-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="32ae2-136">WIF poskytuje jeden název vystavitele jako typ registru v poli, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třída.</span><span class="sxs-lookup"><span data-stu-id="32ae2-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="32ae2-137">Tato třída používá sadu certifikátů důvěryhodných vystavitelů, které jsou zadány v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="32ae2-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="32ae2-138">Vyžaduje podřízený element `<trustedIssuers>`konfigurace, pod kterým je nakonfigurované shromažďování certifikátů důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="32ae2-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="32ae2-139">Důvěryhodné certifikáty jsou určeny pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány nebo odebrány z kolekce pomocí `<add>`prvků, `<clear>`nebo `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="32ae2-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="32ae2-140">Element je reprezentován <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>třídou. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="32ae2-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32ae2-141">Určení prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="32ae2-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="32ae2-142">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.</span><span class="sxs-lookup"><span data-stu-id="32ae2-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32ae2-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="32ae2-143">Example</span></span>  
 <span data-ttu-id="32ae2-144">Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="32ae2-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32ae2-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32ae2-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
