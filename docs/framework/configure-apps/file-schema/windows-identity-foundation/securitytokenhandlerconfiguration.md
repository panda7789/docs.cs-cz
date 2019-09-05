---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251890"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="201f2-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="201f2-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="201f2-102">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="201f2-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="201f2-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="201f2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="201f2-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="201f2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="201f2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="201f2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="201f2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="201f2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="201f2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="201f2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201f2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="201f2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="201f2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="201f2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="201f2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="201f2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="201f2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="201f2-111">Attributes</span></span>  
  
|<span data-ttu-id="201f2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="201f2-112">Attribute</span></span>|<span data-ttu-id="201f2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="201f2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="201f2-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="201f2-114">saveBootstrapContext</span></span>|<span data-ttu-id="201f2-115">Určuje, zda mají být do tokenu relace zahrnuty tokeny Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="201f2-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="201f2-116">Hodnotu lze také nastavit pro kolekci obslužných rutin tokenů nastavením `saveBootstrapContext` atributu [ \<v elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="201f2-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="201f2-117">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="201f2-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="201f2-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="201f2-118">maximumClockSkew</span></span>|<span data-ttu-id="201f2-119">A <xref:System.TimeSpan> určuje maximální povolený časový posun.</span><span class="sxs-lookup"><span data-stu-id="201f2-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="201f2-120">Určuje maximální povolený časový posun při provádění operací závislých na čase, jako je například ověření doby platnosti přihlašovací relace.</span><span class="sxs-lookup"><span data-stu-id="201f2-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="201f2-121">Výchozí hodnota je 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="201f2-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="201f2-122">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="201f2-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="201f2-123">Maximální hodinový posun lze také nastavit na úrovni služby nastavením `maximumClockSkew` atributu [ \<u prvku IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="201f2-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="201f2-124">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="201f2-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="201f2-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="201f2-125">Child Elements</span></span>  
  
|<span data-ttu-id="201f2-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="201f2-126">Element</span></span>|<span data-ttu-id="201f2-127">Popis</span><span class="sxs-lookup"><span data-stu-id="201f2-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="201f2-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="201f2-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="201f2-129">Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory této předávající strany.</span><span class="sxs-lookup"><span data-stu-id="201f2-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="201f2-130">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="201f2-130">Optional.</span></span>|  
|[<span data-ttu-id="201f2-131">\<caches></span><span class="sxs-lookup"><span data-stu-id="201f2-131">\<caches></span></span>](caches.md)|<span data-ttu-id="201f2-132">Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="201f2-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="201f2-133">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="201f2-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="201f2-134">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="201f2-134">Optional.</span></span>|  
|[<span data-ttu-id="201f2-135">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="201f2-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="201f2-136">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="201f2-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="201f2-137">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="201f2-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="201f2-138">Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru.</span><span class="sxs-lookup"><span data-stu-id="201f2-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="201f2-139">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="201f2-139">Optional.</span></span>|  
|[<span data-ttu-id="201f2-140">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="201f2-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="201f2-141">Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="201f2-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="201f2-142">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="201f2-142">Optional.</span></span>|  
|[<span data-ttu-id="201f2-143">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="201f2-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="201f2-144">Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="201f2-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="201f2-145">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="201f2-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="201f2-146">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="201f2-146">Optional.</span></span>|  
|[<span data-ttu-id="201f2-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="201f2-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="201f2-148">Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="201f2-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="201f2-149">Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="201f2-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="201f2-150">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="201f2-150">Optional.</span></span>|  
|[<span data-ttu-id="201f2-151">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="201f2-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="201f2-152">Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="201f2-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="201f2-153">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="201f2-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="201f2-154">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="201f2-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="201f2-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="201f2-155">Parent Elements</span></span>  
  
|<span data-ttu-id="201f2-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="201f2-156">Element</span></span>|<span data-ttu-id="201f2-157">Popis</span><span class="sxs-lookup"><span data-stu-id="201f2-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="201f2-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="201f2-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="201f2-159">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="201f2-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="201f2-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="201f2-160">Remarks</span></span>  
 <span data-ttu-id="201f2-161">Tato část poskytuje hodnoty <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="201f2-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="201f2-162">Nastavení konfigurovaná v této části přepíší ty, které jsou ve službě nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="201f2-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="201f2-163">Některá z těchto nastavení lze naopak přepsat nastavením, která jsou zadána při přidání obslužné rutiny do kolekce obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="201f2-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="201f2-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="201f2-164">Example</span></span>  
  
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
