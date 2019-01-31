---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 29e18cdda9e18addef4f0f32fd30e9abf6af78fc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262884"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="e3dc4-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e3dc4-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="e3dc4-102">Poskytuje konfiguraci pro kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="e3dc4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e3dc4-103">\<system.identityModel></span></span>  
<span data-ttu-id="e3dc4-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e3dc4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="e3dc4-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e3dc4-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e3dc4-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e3dc4-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3dc4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3dc4-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3dc4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3dc4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e3dc4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3dc4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3dc4-110">Attributes</span></span>  
  
|<span data-ttu-id="e3dc4-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e3dc4-111">Attribute</span></span>|<span data-ttu-id="e3dc4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e3dc4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3dc4-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="e3dc4-113">saveBootstrapContext</span></span>|<span data-ttu-id="e3dc4-114">Určuje, zda mají být zahrnuty bootstrap tokeny v tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="e3dc4-115">Hodnota může také nastavit na kolekci obslužné rutiny tokenů nastavením `saveBootstrapContext` atribut na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="e3dc4-116">Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="e3dc4-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="e3dc4-117">maximumClockSkew</span></span>|<span data-ttu-id="e3dc4-118">A <xref:System.TimeSpan> , která určuje maximální povolený posun.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="e3dc4-119">Určuje maximální povolený posun při provádění operace citlivé na čas, jako je například ověřování čas vypršení platnosti relace přihlášení.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="e3dc4-120">Výchozí hodnota je 5 minut, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="e3dc4-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="e3dc4-121">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v článku [hodnoty prvku Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3dc4-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="e3dc4-122">Maximální posun může být rovněž nastaven na úrovni služby pomocí nastavení `maximumClockSkew` atribut na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="e3dc4-123">Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3dc4-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e3dc4-124">Child Elements</span></span>  
  
|<span data-ttu-id="e3dc4-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3dc4-125">Element</span></span>|<span data-ttu-id="e3dc4-126">Popis</span><span class="sxs-lookup"><span data-stu-id="e3dc4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3dc4-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="e3dc4-127">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="e3dc4-128">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory této předávající straně.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="e3dc4-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-129">Optional.</span></span>|  
|[<span data-ttu-id="e3dc4-130">\<caches></span><span class="sxs-lookup"><span data-stu-id="e3dc4-130">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="e3dc4-131">Zaregistruje mezipaměti používané pro tokeny relace a rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="e3dc4-132">Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e3dc4-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-133">Optional.</span></span>|  
|[<span data-ttu-id="e3dc4-134">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="e3dc4-134">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="e3dc4-135">Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="e3dc4-136">Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e3dc4-137">Tato nastavení jsou přepsány, pokud jsou nakonfigurované vlastní validátor konkrétní obslužnou rutinou.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="e3dc4-138">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-138">Optional.</span></span>|  
|[<span data-ttu-id="e3dc4-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="e3dc4-139">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="e3dc4-140">Nakonfiguruje registru názvu vystavitele, který se používá obslužné rutiny v kolekci obslužná rutina tokenů.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e3dc4-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-141">Optional.</span></span>|  
|[<span data-ttu-id="e3dc4-142">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="e3dc4-142">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="e3dc4-143">Zaregistruje překladač tokenů vystavitele, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e3dc4-144">Překladač tokenů vystavitele se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="e3dc4-145">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-145">Optional.</span></span>|  
|[<span data-ttu-id="e3dc4-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="e3dc4-146">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="e3dc4-147">Zaregistruje překladač tokenů služby, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e3dc4-148">Překladač tokenů služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e3dc4-149">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-149">Optional.</span></span>|  
|[<span data-ttu-id="e3dc4-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="e3dc4-150">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="e3dc4-151">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="e3dc4-152">Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e3dc4-153">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3dc4-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e3dc4-154">Parent Elements</span></span>  
  
|<span data-ttu-id="e3dc4-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3dc4-155">Element</span></span>|<span data-ttu-id="e3dc4-156">Popis</span><span class="sxs-lookup"><span data-stu-id="e3dc4-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3dc4-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e3dc4-157">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="e3dc4-158">Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3dc4-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3dc4-159">Remarks</span></span>  
 <span data-ttu-id="e3dc4-160">Tato část obsahuje hodnoty vlastností <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objektu.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="e3dc4-161">Přepsat nastavení nakonfigurovaná v této části porty nakonfigurované na službu.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="e3dc4-162">Některá z těchto nastavení můžete přepsat zase nastavením, které jsou zadány při obslužnou rutinu je přidán do kolekce obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e3dc4-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3dc4-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3dc4-163">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
