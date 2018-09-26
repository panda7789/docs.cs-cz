---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206085"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="4fe87-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="4fe87-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="4fe87-103">Poskytuje konfiguraci pro kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="4fe87-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="4fe87-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4fe87-104">\<system.identityModel></span></span>  
<span data-ttu-id="4fe87-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4fe87-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4fe87-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="4fe87-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4fe87-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4fe87-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe87-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fe87-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe87-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4fe87-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4fe87-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4fe87-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe87-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4fe87-111">Attributes</span></span>  
  
|<span data-ttu-id="4fe87-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4fe87-112">Attribute</span></span>|<span data-ttu-id="4fe87-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe87-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fe87-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="4fe87-114">saveBootstrapContext</span></span>|<span data-ttu-id="4fe87-115">Určuje, zda mají být zahrnuty bootstrap tokeny v tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="4fe87-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="4fe87-116">Hodnota může také nastavit na kolekci obslužné rutiny tokenů nastavením `saveBootstrapContext` atribut na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4fe87-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="4fe87-117">Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.</span><span class="sxs-lookup"><span data-stu-id="4fe87-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="4fe87-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="4fe87-118">maximumClockSkew</span></span>|<span data-ttu-id="4fe87-119">A <xref:System.TimeSpan> , která určuje maximální povolený posun.</span><span class="sxs-lookup"><span data-stu-id="4fe87-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="4fe87-120">Určuje maximální povolený posun při provádění operace citlivé na čas, jako je například ověřování čas vypršení platnosti relace přihlášení.</span><span class="sxs-lookup"><span data-stu-id="4fe87-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="4fe87-121">Výchozí hodnota je 5 minut, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="4fe87-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="4fe87-122">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v článku [hodnoty prvku Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="4fe87-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="4fe87-123">Maximální posun může být rovněž nastaven na úrovni služby pomocí nastavení `maximumClockSkew` atribut na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4fe87-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="4fe87-124">Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.</span><span class="sxs-lookup"><span data-stu-id="4fe87-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe87-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4fe87-125">Child Elements</span></span>  
  
|<span data-ttu-id="4fe87-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fe87-126">Element</span></span>|<span data-ttu-id="4fe87-127">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe87-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe87-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="4fe87-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="4fe87-129">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory této předávající straně.</span><span class="sxs-lookup"><span data-stu-id="4fe87-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="4fe87-130">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fe87-130">Optional.</span></span>|  
|[<span data-ttu-id="4fe87-131">\<ukládá do mezipaměti ></span><span class="sxs-lookup"><span data-stu-id="4fe87-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="4fe87-132">Zaregistruje mezipaměti používané pro tokeny relace a rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="4fe87-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="4fe87-133">Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4fe87-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4fe87-134">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fe87-134">Optional.</span></span>|  
|[<span data-ttu-id="4fe87-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="4fe87-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="4fe87-136">Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4fe87-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="4fe87-137">Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4fe87-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4fe87-138">Tato nastavení jsou přepsány, pokud jsou nakonfigurované vlastní validátor konkrétní obslužnou rutinou.</span><span class="sxs-lookup"><span data-stu-id="4fe87-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="4fe87-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fe87-139">Optional.</span></span>|  
|[<span data-ttu-id="4fe87-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="4fe87-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="4fe87-141">Nakonfiguruje registru názvu vystavitele, který se používá obslužné rutiny v kolekci obslužná rutina tokenů.</span><span class="sxs-lookup"><span data-stu-id="4fe87-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4fe87-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fe87-142">Optional.</span></span>|  
|[<span data-ttu-id="4fe87-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="4fe87-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="4fe87-144">Zaregistruje překladač tokenů vystavitele, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="4fe87-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4fe87-145">Překladač tokenů vystavitele se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="4fe87-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="4fe87-146">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fe87-146">Optional.</span></span>|  
|[<span data-ttu-id="4fe87-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="4fe87-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="4fe87-148">Zaregistruje překladač tokenů služby, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="4fe87-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4fe87-149">Překladač tokenů služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="4fe87-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="4fe87-150">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fe87-150">Optional.</span></span>|  
|[<span data-ttu-id="4fe87-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="4fe87-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="4fe87-152">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="4fe87-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="4fe87-153">Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4fe87-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4fe87-154">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4fe87-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe87-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4fe87-155">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe87-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fe87-156">Element</span></span>|<span data-ttu-id="4fe87-157">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe87-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe87-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="4fe87-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="4fe87-159">Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4fe87-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe87-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fe87-160">Remarks</span></span>  
 <span data-ttu-id="4fe87-161">Tato část obsahuje hodnoty vlastností <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objektu.</span><span class="sxs-lookup"><span data-stu-id="4fe87-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="4fe87-162">Přepsat nastavení nakonfigurovaná v této části porty nakonfigurované na službu.</span><span class="sxs-lookup"><span data-stu-id="4fe87-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="4fe87-163">Některá z těchto nastavení můžete přepsat zase nastavením, které jsou zadány při obslužnou rutinu je přidán do kolekce obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4fe87-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe87-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fe87-164">Example</span></span>  
  
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
