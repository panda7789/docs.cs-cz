---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942443"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="43a33-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="43a33-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="43a33-102">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="43a33-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="43a33-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="43a33-103">\<system.identityModel></span></span>  
<span data-ttu-id="43a33-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="43a33-104">\<identityConfiguration></span></span>  
<span data-ttu-id="43a33-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="43a33-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="43a33-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="43a33-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43a33-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43a33-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43a33-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43a33-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43a33-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43a33-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43a33-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="43a33-110">Attributes</span></span>  
  
|<span data-ttu-id="43a33-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="43a33-111">Attribute</span></span>|<span data-ttu-id="43a33-112">Popis</span><span class="sxs-lookup"><span data-stu-id="43a33-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43a33-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="43a33-113">saveBootstrapContext</span></span>|<span data-ttu-id="43a33-114">Určuje, zda mají být do tokenu relace zahrnuty tokeny Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="43a33-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="43a33-115">Hodnotu lze také nastavit pro kolekci obslužných rutin tokenů nastavením `saveBootstrapContext` atributu [ \<v elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="43a33-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="43a33-116">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="43a33-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="43a33-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="43a33-117">maximumClockSkew</span></span>|<span data-ttu-id="43a33-118">A <xref:System.TimeSpan> určuje maximální povolený časový posun.</span><span class="sxs-lookup"><span data-stu-id="43a33-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="43a33-119">Určuje maximální povolený časový posun při provádění operací závislých na čase, jako je například ověření doby platnosti přihlašovací relace.</span><span class="sxs-lookup"><span data-stu-id="43a33-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="43a33-120">Výchozí hodnota je 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="43a33-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="43a33-121">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="43a33-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="43a33-122">Maximální hodinový posun lze také nastavit na úrovni služby nastavením `maximumClockSkew` atributu [ \<u prvku IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="43a33-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="43a33-123">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="43a33-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43a33-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43a33-124">Child Elements</span></span>  
  
|<span data-ttu-id="43a33-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="43a33-125">Element</span></span>|<span data-ttu-id="43a33-126">Popis</span><span class="sxs-lookup"><span data-stu-id="43a33-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43a33-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="43a33-127">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="43a33-128">Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory této předávající strany.</span><span class="sxs-lookup"><span data-stu-id="43a33-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="43a33-129">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="43a33-129">Optional.</span></span>|  
|[<span data-ttu-id="43a33-130">\<caches></span><span class="sxs-lookup"><span data-stu-id="43a33-130">\<caches></span></span>](caches.md)|<span data-ttu-id="43a33-131">Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="43a33-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="43a33-132">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="43a33-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="43a33-133">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="43a33-133">Optional.</span></span>|  
|[<span data-ttu-id="43a33-134">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="43a33-134">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="43a33-135">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="43a33-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="43a33-136">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="43a33-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="43a33-137">Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru.</span><span class="sxs-lookup"><span data-stu-id="43a33-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="43a33-138">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="43a33-138">Optional.</span></span>|  
|[<span data-ttu-id="43a33-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="43a33-139">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="43a33-140">Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="43a33-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="43a33-141">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="43a33-141">Optional.</span></span>|  
|[<span data-ttu-id="43a33-142">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="43a33-142">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="43a33-143">Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="43a33-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="43a33-144">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="43a33-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="43a33-145">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="43a33-145">Optional.</span></span>|  
|[<span data-ttu-id="43a33-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="43a33-146">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="43a33-147">Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="43a33-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="43a33-148">Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="43a33-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="43a33-149">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="43a33-149">Optional.</span></span>|  
|[<span data-ttu-id="43a33-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="43a33-150">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="43a33-151">Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="43a33-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="43a33-152">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="43a33-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="43a33-153">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="43a33-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43a33-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43a33-154">Parent Elements</span></span>  
  
|<span data-ttu-id="43a33-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="43a33-155">Element</span></span>|<span data-ttu-id="43a33-156">Popis</span><span class="sxs-lookup"><span data-stu-id="43a33-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43a33-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="43a33-157">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="43a33-158">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="43a33-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43a33-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43a33-159">Remarks</span></span>  
 <span data-ttu-id="43a33-160">Tato část poskytuje hodnoty <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="43a33-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="43a33-161">Nastavení konfigurovaná v této části přepíší ty, které jsou ve službě nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="43a33-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="43a33-162">Některá z těchto nastavení lze naopak přepsat nastavením, která jsou zadána při přidání obslužné rutiny do kolekce obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="43a33-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43a33-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="43a33-163">Example</span></span>  
  
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
