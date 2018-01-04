---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ac7284fa418c1540582c40bd744e913ba31aa881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="68a4a-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="68a4a-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="68a4a-103">Poskytuje konfigurace pro kolekci tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="68a4a-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="68a4a-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="68a4a-104">\<system.identityModel></span></span>  
<span data-ttu-id="68a4a-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="68a4a-105">\<identityConfiguration></span></span>  
<span data-ttu-id="68a4a-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="68a4a-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="68a4a-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="68a4a-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68a4a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68a4a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68a4a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68a4a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="68a4a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68a4a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68a4a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="68a4a-111">Attributes</span></span>  
  
|<span data-ttu-id="68a4a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="68a4a-112">Attribute</span></span>|<span data-ttu-id="68a4a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="68a4a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68a4a-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="68a4a-114">saveBootstrapContext</span></span>|<span data-ttu-id="68a4a-115">Určuje, zda bootstrap tokeny mají být zahrnuty v tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="68a4a-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="68a4a-116">Hodnota může být také nastaven na kolekci obslužná rutina tokenu nastavením `saveBootstrapContext` atributu u [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="68a4a-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="68a4a-117">Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="68a4a-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="68a4a-118">maximumClockSkew</span></span>|<span data-ttu-id="68a4a-119">A <xref:System.TimeSpan> , určuje zkosení maximální povolené hodiny.</span><span class="sxs-lookup"><span data-stu-id="68a4a-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="68a4a-120">Určuje maximální povolený hodiny zkosení při provádění operace náročné na čas, jako je například ověřování čas vypršení platnosti relace přihlášení.</span><span class="sxs-lookup"><span data-stu-id="68a4a-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="68a4a-121">Výchozí hodnota je 5 minut, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="68a4a-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="68a4a-122">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v části [časový interval hodnoty](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="68a4a-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="68a4a-123">Maximální hodiny zkosení může být také nastaven na úrovni služby nastavením `maximumClockSkew` atributu u [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="68a4a-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="68a4a-124">Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68a4a-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="68a4a-125">Child Elements</span></span>  
  
|<span data-ttu-id="68a4a-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="68a4a-126">Element</span></span>|<span data-ttu-id="68a4a-127">Popis</span><span class="sxs-lookup"><span data-stu-id="68a4a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68a4a-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="68a4a-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="68a4a-129">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory této předávající strany.</span><span class="sxs-lookup"><span data-stu-id="68a4a-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="68a4a-130">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68a4a-130">Optional.</span></span>|  
|[<span data-ttu-id="68a4a-131">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="68a4a-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="68a4a-132">Zaregistruje mezipamětí použít pro tokeny relace a rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="68a4a-133">Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68a4a-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="68a4a-134">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68a4a-134">Optional.</span></span>|  
|[<span data-ttu-id="68a4a-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="68a4a-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="68a4a-136">Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="68a4a-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="68a4a-137">Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68a4a-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="68a4a-138">Tato nastavení jsou přepsat, pokud obslužná rutina specifická nakonfigurovaný s vlastním validátoru.</span><span class="sxs-lookup"><span data-stu-id="68a4a-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="68a4a-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68a4a-139">Optional.</span></span>|  
|[<span data-ttu-id="68a4a-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="68a4a-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="68a4a-141">Nakonfiguruje registru název vystavitele, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="68a4a-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68a4a-142">Optional.</span></span>|  
|[<span data-ttu-id="68a4a-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="68a4a-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="68a4a-144">Zaregistruje překladač vystavitele tokenu, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="68a4a-145">Překladač vystavitele tokenu se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="68a4a-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="68a4a-146">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68a4a-146">Optional.</span></span>|  
|[<span data-ttu-id="68a4a-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="68a4a-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="68a4a-148">Zaregistruje překladač tokenu služby, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="68a4a-149">Překladač tokenu služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="68a4a-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="68a4a-150">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68a4a-150">Optional.</span></span>|  
|[<span data-ttu-id="68a4a-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="68a4a-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="68a4a-152">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="68a4a-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="68a4a-153">Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68a4a-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="68a4a-154">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68a4a-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68a4a-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="68a4a-155">Parent Elements</span></span>  
  
|<span data-ttu-id="68a4a-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="68a4a-156">Element</span></span>|<span data-ttu-id="68a4a-157">Popis</span><span class="sxs-lookup"><span data-stu-id="68a4a-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68a4a-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="68a4a-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="68a4a-159">Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.</span><span class="sxs-lookup"><span data-stu-id="68a4a-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68a4a-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68a4a-160">Remarks</span></span>  
 <span data-ttu-id="68a4a-161">Tato část obsahuje hodnoty vlastností pro <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objektu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="68a4a-162">Nastavení v této části přepsat nakonfigurovaným na službu.</span><span class="sxs-lookup"><span data-stu-id="68a4a-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="68a4a-163">Některá z těchto nastavení je, pak možné přepsat nastavení, které jsou uvedeny během obslužná rutina se přidá do kolekce obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68a4a-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68a4a-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="68a4a-164">Example</span></span>  
  
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
