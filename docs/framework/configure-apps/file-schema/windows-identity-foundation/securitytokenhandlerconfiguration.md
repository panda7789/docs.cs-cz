---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 168bdc4fbf640b201ebc61462d04727c23f838f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758422"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="88d2b-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="88d2b-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="88d2b-103">Poskytuje konfigurace pro kolekci tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="88d2b-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="88d2b-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="88d2b-104">\<system.identityModel></span></span>  
<span data-ttu-id="88d2b-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="88d2b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="88d2b-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="88d2b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="88d2b-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="88d2b-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d2b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88d2b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88d2b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="88d2b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88d2b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="88d2b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88d2b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="88d2b-111">Attributes</span></span>  
  
|<span data-ttu-id="88d2b-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="88d2b-112">Attribute</span></span>|<span data-ttu-id="88d2b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="88d2b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88d2b-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="88d2b-114">saveBootstrapContext</span></span>|<span data-ttu-id="88d2b-115">Určuje, zda bootstrap tokeny mají být zahrnuty v tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="88d2b-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="88d2b-116">Hodnota může být také nastaven na kolekci obslužná rutina tokenu nastavením `saveBootstrapContext` atributu u [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="88d2b-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="88d2b-117">Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="88d2b-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="88d2b-118">maximumClockSkew</span></span>|<span data-ttu-id="88d2b-119">A <xref:System.TimeSpan> , určuje zkosení maximální povolené hodiny.</span><span class="sxs-lookup"><span data-stu-id="88d2b-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="88d2b-120">Určuje maximální povolený hodiny zkosení při provádění operace náročné na čas, jako je například ověřování čas vypršení platnosti relace přihlášení.</span><span class="sxs-lookup"><span data-stu-id="88d2b-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="88d2b-121">Výchozí hodnota je 5 minut, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="88d2b-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="88d2b-122">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v části [časový interval hodnoty](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="88d2b-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="88d2b-123">Maximální hodiny zkosení může být také nastaven na úrovni služby nastavením `maximumClockSkew` atributu u [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="88d2b-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="88d2b-124">Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88d2b-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="88d2b-125">Child Elements</span></span>  
  
|<span data-ttu-id="88d2b-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="88d2b-126">Element</span></span>|<span data-ttu-id="88d2b-127">Popis</span><span class="sxs-lookup"><span data-stu-id="88d2b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88d2b-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="88d2b-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="88d2b-129">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory této předávající strany.</span><span class="sxs-lookup"><span data-stu-id="88d2b-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="88d2b-130">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d2b-130">Optional.</span></span>|  
|[<span data-ttu-id="88d2b-131">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="88d2b-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="88d2b-132">Zaregistruje mezipamětí použít pro tokeny relace a rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="88d2b-133">Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="88d2b-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="88d2b-134">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d2b-134">Optional.</span></span>|  
|[<span data-ttu-id="88d2b-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="88d2b-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="88d2b-136">Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="88d2b-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="88d2b-137">Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="88d2b-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="88d2b-138">Tato nastavení jsou přepsat, pokud obslužná rutina specifická nakonfigurovaný s vlastním validátoru.</span><span class="sxs-lookup"><span data-stu-id="88d2b-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="88d2b-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d2b-139">Optional.</span></span>|  
|[<span data-ttu-id="88d2b-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="88d2b-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="88d2b-141">Nakonfiguruje registru název vystavitele, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="88d2b-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d2b-142">Optional.</span></span>|  
|[<span data-ttu-id="88d2b-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="88d2b-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="88d2b-144">Zaregistruje překladač vystavitele tokenu, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="88d2b-145">Překladač vystavitele tokenu se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="88d2b-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="88d2b-146">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d2b-146">Optional.</span></span>|  
|[<span data-ttu-id="88d2b-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="88d2b-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="88d2b-148">Zaregistruje překladač tokenu služby, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="88d2b-149">Překladač tokenu služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="88d2b-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="88d2b-150">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d2b-150">Optional.</span></span>|  
|[<span data-ttu-id="88d2b-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="88d2b-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="88d2b-152">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="88d2b-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="88d2b-153">Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="88d2b-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="88d2b-154">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d2b-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88d2b-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="88d2b-155">Parent Elements</span></span>  
  
|<span data-ttu-id="88d2b-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="88d2b-156">Element</span></span>|<span data-ttu-id="88d2b-157">Popis</span><span class="sxs-lookup"><span data-stu-id="88d2b-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88d2b-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="88d2b-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="88d2b-159">Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.</span><span class="sxs-lookup"><span data-stu-id="88d2b-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88d2b-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88d2b-160">Remarks</span></span>  
 <span data-ttu-id="88d2b-161">Tato část obsahuje hodnoty vlastností pro <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objektu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="88d2b-162">Nastavení v této části přepsat nakonfigurovaným na službu.</span><span class="sxs-lookup"><span data-stu-id="88d2b-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="88d2b-163">Některá z těchto nastavení je, pak možné přepsat nastavení, které jsou uvedeny během obslužná rutina se přidá do kolekce obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="88d2b-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88d2b-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="88d2b-164">Example</span></span>  
  
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
