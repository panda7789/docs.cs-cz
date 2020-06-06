---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152564"
---
# \<securityTokenHandlerConfiguration>
<span data-ttu-id="f4e6e-101">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-101">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="f4e6e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4e6e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4e6e-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f4e6e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f4e6e-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4e6e-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="f4e6e-105">Attributes</span></span>  
  
|<span data-ttu-id="f4e6e-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="f4e6e-106">Attribute</span></span>|<span data-ttu-id="f4e6e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f4e6e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4e6e-108">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="f4e6e-108">saveBootstrapContext</span></span>|<span data-ttu-id="f4e6e-109">Určuje, zda mají být do tokenu relace zahrnuty tokeny Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-109">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="f4e6e-110">Hodnotu lze také nastavit pro kolekci obslužné rutiny tokenů nastavením `saveBootstrapContext` atributu u [\<identityConfiguration>](identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-110">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="f4e6e-111">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-111">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="f4e6e-112">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="f4e6e-112">maximumClockSkew</span></span>|<span data-ttu-id="f4e6e-113">A <xref:System.TimeSpan> Určuje maximální povolený časový posun.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-113">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="f4e6e-114">Určuje maximální povolený časový posun při provádění operací závislých na čase, jako je například ověření doby platnosti přihlašovací relace.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-114">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="f4e6e-115">Výchozí hodnota je 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="f4e6e-115">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="f4e6e-116">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4e6e-116">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f4e6e-117">Maximální hodinový posun lze také nastavit na úrovni služby nastavením `maximumClockSkew` atributu u [\<identityConfiguration>](identityconfiguration.md) prvku.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-117">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="f4e6e-118">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-118">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4e6e-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f4e6e-119">Child Elements</span></span>  
  
|<span data-ttu-id="f4e6e-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4e6e-120">Element</span></span>|<span data-ttu-id="f4e6e-121">Description</span><span class="sxs-lookup"><span data-stu-id="f4e6e-121">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="f4e6e-122">Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory této předávající strany.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-122">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="f4e6e-123">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-123">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="f4e6e-124">Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-124">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="f4e6e-125">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-125">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f4e6e-126">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-126">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="f4e6e-127">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-127">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="f4e6e-128">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-128">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f4e6e-129">Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-129">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="f4e6e-130">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-130">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="f4e6e-131">Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-131">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f4e6e-132">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-132">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="f4e6e-133">Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-133">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f4e6e-134">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-134">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="f4e6e-135">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-135">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="f4e6e-136">Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-136">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f4e6e-137">Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-137">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="f4e6e-138">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-138">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="f4e6e-139">Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-139">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="f4e6e-140">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-140">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f4e6e-141">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-141">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4e6e-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f4e6e-142">Parent Elements</span></span>  
  
|<span data-ttu-id="f4e6e-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4e6e-143">Element</span></span>|<span data-ttu-id="f4e6e-144">Description</span><span class="sxs-lookup"><span data-stu-id="f4e6e-144">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="f4e6e-145">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-145">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4e6e-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4e6e-146">Remarks</span></span>  
 <span data-ttu-id="f4e6e-147">Tato část poskytuje hodnoty vlastností <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objektu.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-147">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="f4e6e-148">Nastavení konfigurovaná v této části přepíší ty, které jsou ve službě nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-148">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="f4e6e-149">Některá z těchto nastavení lze naopak přepsat nastavením, která jsou zadána při přidání obslužné rutiny do kolekce obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f4e6e-149">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4e6e-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4e6e-150">Example</span></span>  
  
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
