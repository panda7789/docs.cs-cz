---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152564"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="4afb6-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4afb6-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="4afb6-102">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="4afb6-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="4afb6-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4afb6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4afb6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="4afb6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="4afb6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="4afb6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="4afb6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="4afb6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="4afb6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="4afb6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4afb6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4afb6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4afb6-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4afb6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4afb6-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4afb6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4afb6-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4afb6-111">Attributes</span></span>  
  
|<span data-ttu-id="4afb6-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4afb6-112">Attribute</span></span>|<span data-ttu-id="4afb6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4afb6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4afb6-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="4afb6-114">saveBootstrapContext</span></span>|<span data-ttu-id="4afb6-115">Určuje, zda mají být tokeny bootstrap zahrnuty do tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="4afb6-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="4afb6-116">Hodnota může být také nastavena na kolekci obslužné rutiny tokenu nastavením atributu `saveBootstrapContext` na elementu [ \<identityConfiguration>.](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="4afb6-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="4afb6-117">Hodnota nastavená v kolekci obslužné rutiny tokenu přepíše hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="4afb6-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="4afb6-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="4afb6-118">maximumClockSkew</span></span>|<span data-ttu-id="4afb6-119">A, <xref:System.TimeSpan> který určuje maximální povolené hodiny zkosení.</span><span class="sxs-lookup"><span data-stu-id="4afb6-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="4afb6-120">Řídí maximální povolené hodiny zkosení při provádění operací citlivých na čas, jako je například ověření doby vypršení platnosti relace přihlášení.</span><span class="sxs-lookup"><span data-stu-id="4afb6-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="4afb6-121">Výchozí hodnota je 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="4afb6-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="4afb6-122">Další informace o zadávání <xref:System.TimeSpan> hodnot naleznete v tématu [Timespan Values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="4afb6-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="4afb6-123">Maximální zkosení hodin může být také `maximumClockSkew` nastaveno na úrovni služby nastavením atributu na elementu [ \<identityConfiguration>.](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="4afb6-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="4afb6-124">Hodnota nastavená v kolekci obslužné rutiny tokenu přepíše hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="4afb6-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4afb6-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4afb6-125">Child Elements</span></span>  
  
|<span data-ttu-id="4afb6-126">Element</span><span class="sxs-lookup"><span data-stu-id="4afb6-126">Element</span></span>|<span data-ttu-id="4afb6-127">Popis</span><span class="sxs-lookup"><span data-stu-id="4afb6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4afb6-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="4afb6-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="4afb6-129">Určuje sadu identifikátorů URI, které jsou přijatelnými identifikátory této předávající strany.</span><span class="sxs-lookup"><span data-stu-id="4afb6-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="4afb6-130">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4afb6-130">Optional.</span></span>|  
|[<span data-ttu-id="4afb6-131">\<>mezipamětí</span><span class="sxs-lookup"><span data-stu-id="4afb6-131">\<caches></span></span>](caches.md)|<span data-ttu-id="4afb6-132">Registruje mezipaměti používané pro tokeny relace a detekci opětovného přehrání tokenů.</span><span class="sxs-lookup"><span data-stu-id="4afb6-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="4afb6-133">Lze zadat na úrovni služby nebo na kolekci obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4afb6-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4afb6-134">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4afb6-134">Optional.</span></span>|  
|[<span data-ttu-id="4afb6-135">\<>ověření certifikátu</span><span class="sxs-lookup"><span data-stu-id="4afb6-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="4afb6-136">Řídí nastavení, která obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4afb6-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="4afb6-137">Lze zadat na úrovni služby nebo na kolekci obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4afb6-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4afb6-138">Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována s vlastním validátorem.</span><span class="sxs-lookup"><span data-stu-id="4afb6-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="4afb6-139">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4afb6-139">Optional.</span></span>|  
|[<span data-ttu-id="4afb6-140">\<>issuerNameRegistry</span><span class="sxs-lookup"><span data-stu-id="4afb6-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="4afb6-141">Konfiguruje registr názvů vystavitele, který používají obslužné rutiny v kolekci obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="4afb6-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4afb6-142">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4afb6-142">Optional.</span></span>|  
|[<span data-ttu-id="4afb6-143">\<>překladače tokenu</span><span class="sxs-lookup"><span data-stu-id="4afb6-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="4afb6-144">Registruje překladač tokenů vystavitelů, který používají obslužné rutiny v kolekci obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="4afb6-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4afb6-145">Překladač tokenů vystavithonu se používá k vyřešení podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="4afb6-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="4afb6-146">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4afb6-146">Optional.</span></span>|  
|[<span data-ttu-id="4afb6-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="4afb6-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="4afb6-148">Registruje překladač tokenů služby, který používají obslužné rutiny v kolekci obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="4afb6-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4afb6-149">Překládání tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="4afb6-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="4afb6-150">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4afb6-150">Optional.</span></span>|  
|[<span data-ttu-id="4afb6-151">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="4afb6-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="4afb6-152">Povolí detekci opětovného přehrání tokenů a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="4afb6-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="4afb6-153">Lze zadat na úrovni služby nebo na kolekci obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4afb6-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4afb6-154">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4afb6-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4afb6-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4afb6-155">Parent Elements</span></span>  
  
|<span data-ttu-id="4afb6-156">Element</span><span class="sxs-lookup"><span data-stu-id="4afb6-156">Element</span></span>|<span data-ttu-id="4afb6-157">Popis</span><span class="sxs-lookup"><span data-stu-id="4afb6-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4afb6-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4afb6-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="4afb6-159">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="4afb6-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4afb6-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4afb6-160">Remarks</span></span>  
 <span data-ttu-id="4afb6-161">Tato část obsahuje hodnoty <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="4afb6-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="4afb6-162">Nastavení nakonfigurovaná v této části přepisují nastavení nakonfigurovaná ve službě.</span><span class="sxs-lookup"><span data-stu-id="4afb6-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="4afb6-163">Některá z těchto nastavení mohou být zase přepsána nastaveními, která jsou určena při přidání obslužné rutiny do kolekce obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4afb6-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4afb6-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="4afb6-164">Example</span></span>  
  
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
