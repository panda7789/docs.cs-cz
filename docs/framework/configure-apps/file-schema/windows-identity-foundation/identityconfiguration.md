---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251985"
---
# \<identityConfiguration>

<span data-ttu-id="f38e9-101">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="f38e9-101">Specifies service-level identity settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

## <a name="syntax"></a><span data-ttu-id="f38e9-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f38e9-102">Syntax</span></span>

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f38e9-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f38e9-103">Attributes and Elements</span></span>

<span data-ttu-id="f38e9-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f38e9-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f38e9-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="f38e9-105">Attributes</span></span>

|<span data-ttu-id="f38e9-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="f38e9-106">Attribute</span></span>|<span data-ttu-id="f38e9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f38e9-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f38e9-108">name</span><span class="sxs-lookup"><span data-stu-id="f38e9-108">name</span></span>|<span data-ttu-id="f38e9-109">Název oddílu konfigurace identity</span><span class="sxs-lookup"><span data-stu-id="f38e9-109">The name of the identity configuration section.</span></span> <span data-ttu-id="f38e9-110">Tento název můžete použít k odkazování na konkrétní konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="f38e9-110">You can use this name to reference a specific configuration section.</span></span> <span data-ttu-id="f38e9-111">Pokud `name` není zadán žádný atribut, oddíl definuje výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f38e9-111">If no `name` attribute is specified, the section defines the default configuration.</span></span> <span data-ttu-id="f38e9-112">Výchozí konfigurace se vždycky používá pro scénáře pasivní federace.</span><span class="sxs-lookup"><span data-stu-id="f38e9-112">The default configuration is always used for passive federation scenarios.</span></span> <span data-ttu-id="f38e9-113">Další informace naleznete v tématu [\<federationConfiguration>](federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f38e9-113">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>|
|<span data-ttu-id="f38e9-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="f38e9-114">saveBootstrapContext</span></span>|<span data-ttu-id="f38e9-115">Určuje, zda mají být do tokenu relace zahrnuty tokeny Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f38e9-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="f38e9-116">Hodnotu lze také nastavit pro kolekci obslužné rutiny tokenů nastavením `saveBootstrapContext` atributu u [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f38e9-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="f38e9-117">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="f38e9-117">A value set on the token handler collection overrides the value set on the service.</span></span>|
|<span data-ttu-id="f38e9-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="f38e9-118">maximumClockSkew</span></span>|<span data-ttu-id="f38e9-119">A <xref:System.TimeSpan> Určuje maximální povolený časový posun.</span><span class="sxs-lookup"><span data-stu-id="f38e9-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="f38e9-120">Určuje maximální povolený časový posun při provádění operací závislých na čase, jako je například ověření doby platnosti přihlašovací relace.</span><span class="sxs-lookup"><span data-stu-id="f38e9-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="f38e9-121">Výchozí hodnota je 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="f38e9-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="f38e9-122">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f38e9-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f38e9-123">Maximální hodinový posun lze také nastavit pro kolekci obslužných rutin tokenů nastavením `maximumClockSkew` atributu u [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f38e9-123">The maximum clock skew may also be set on a token handler collection by setting the `maximumClockSkew` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="f38e9-124">Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.</span><span class="sxs-lookup"><span data-stu-id="f38e9-124">A value set on the token handler collection overrides the value set on the service.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f38e9-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f38e9-125">Child Elements</span></span>

|<span data-ttu-id="f38e9-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f38e9-126">Element</span></span>|<span data-ttu-id="f38e9-127">Description</span><span class="sxs-lookup"><span data-stu-id="f38e9-127">Description</span></span>|
|-------------|-----------------|
|[\<caches>](caches.md)|<span data-ttu-id="f38e9-128">Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="f38e9-128">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="f38e9-129">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-129">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f38e9-130">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f38e9-130">Optional.</span></span>|
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="f38e9-131">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f38e9-131">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="f38e9-132">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f38e9-133">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f38e9-133">Optional.</span></span>|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|<span data-ttu-id="f38e9-134">Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="f38e9-134">Registers a claims authentication manager for the incoming claims.</span></span> <span data-ttu-id="f38e9-135">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f38e9-135">Optional.</span></span>|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|<span data-ttu-id="f38e9-136">Registruje Správce autorizací deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="f38e9-136">Registers a claims authorization manager for the incoming claims.</span></span> <span data-ttu-id="f38e9-137">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f38e9-137">Optional.</span></span>|
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="f38e9-138">Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-138">Specifies the set of required claims for incoming security tokens.</span></span> <span data-ttu-id="f38e9-139">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f38e9-139">Optional.</span></span>|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="f38e9-140">Určuje kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-140">Specifies a collection of security token handlers.</span></span> <span data-ttu-id="f38e9-141">Je možné zadat nula nebo více kolekcí obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-141">Zero or more collections of security token handlers can be specified.</span></span> <span data-ttu-id="f38e9-142">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f38e9-142">Optional.</span></span>|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="f38e9-143">Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="f38e9-143">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="f38e9-144">Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-144">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f38e9-145">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f38e9-145">Optional.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f38e9-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f38e9-146">Parent Elements</span></span>

|<span data-ttu-id="f38e9-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="f38e9-147">Element</span></span>|<span data-ttu-id="f38e9-148">Description</span><span class="sxs-lookup"><span data-stu-id="f38e9-148">Description</span></span>|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|<span data-ttu-id="f38e9-149">Poskytuje konfiguraci pro povolení možností Windows Identity Foundation (WIF) v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="f38e9-149">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f38e9-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f38e9-150">Remarks</span></span>

<span data-ttu-id="f38e9-151">Je možné definovat více konfigurací identity, z nichž každý má jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="f38e9-151">Multiple identity configurations may be defined, each with a unique name.</span></span> <span data-ttu-id="f38e9-152">Chování je následující:</span><span class="sxs-lookup"><span data-stu-id="f38e9-152">The behavior is as follows:</span></span>

1. <span data-ttu-id="f38e9-153">Pokud `<identityConfiguration>` není zadán žádný element.</span><span class="sxs-lookup"><span data-stu-id="f38e9-153">If no `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="f38e9-154">Výchozí konfigurace identity se vytvoří za běhu a naplní se výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="f38e9-154">A default identity configuration is created at runtime and populated with default values.</span></span>

2. <span data-ttu-id="f38e9-155">Je-li `<identityConfiguration>` zadán jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="f38e9-155">If a single `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="f38e9-156">Jedná se o výchozí konfiguraci identity.</span><span class="sxs-lookup"><span data-stu-id="f38e9-156">It is the default identity configuration.</span></span> <span data-ttu-id="f38e9-157">Nezáleží na tom, zda má název nebo není pojmenován.</span><span class="sxs-lookup"><span data-stu-id="f38e9-157">It does not matter whether it is named or unnamed.</span></span>

3. <span data-ttu-id="f38e9-158">Je-li `<identityConfiguration>` zadáno více prvků.</span><span class="sxs-lookup"><span data-stu-id="f38e9-158">If multiple `<identityConfiguration>` elements are specified.</span></span> <span data-ttu-id="f38e9-159">Nepojmenovaný element určuje výchozí konfiguraci identity.</span><span class="sxs-lookup"><span data-stu-id="f38e9-159">The unnamed element specifies the default identity configuration.</span></span> <span data-ttu-id="f38e9-160">Doporučuje se, když zadáte více `<identityConfiguration>` prvků, jeden z nich by měl být nepojmenovaný.</span><span class="sxs-lookup"><span data-stu-id="f38e9-160">It is recommended that when you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span>

> [!WARNING]
> <span data-ttu-id="f38e9-161">Pokud zadáte více `<identityConfiguration>` prvků, jeden z nich by měl být nepojmenovaný.</span><span class="sxs-lookup"><span data-stu-id="f38e9-161">If you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span> <span data-ttu-id="f38e9-162">Nepojmenovaný prvek bude výchozí konfigurace identity.</span><span class="sxs-lookup"><span data-stu-id="f38e9-162">The unnamed element will be the default identity configuration.</span></span>

 <span data-ttu-id="f38e9-163">Některá nastavení zadaná v `<identityConfiguration>` elementu lze přepsat nastavením v kolekci obslužných rutin tokenu zabezpečení nebo pomocí nastavení u jednotlivých obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-163">Some of the settings specified in the `<identityConfiguration>` element can be overridden by settings on a security token handler collection or by settings on individual security token handlers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f38e9-164">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu, konfigurace identity, na kterou se odkazuje element, `<federationConfiguration>` konfiguruje správce autorizací deklarací identity a zásadu, která se používá k rozhodování o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="f38e9-164">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="f38e9-165">To platí i ve scénářích, které nejsou pasivními webovými scénáři, například v aplikacích Windows Communication Foundation (WCF) nebo v aplikaci, která není založená na webu.</span><span class="sxs-lookup"><span data-stu-id="f38e9-165">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="f38e9-166">Pokud aplikace není pasivní webovou aplikací, použije se pro daný [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) prvek (a jeho podřízené prvky zásad, pokud jsou k dispozici) odkazovaná konfigurace identity pouze nastavení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-166">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="f38e9-167">Všechna ostatní nastavení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="f38e9-167">All other settings are ignored.</span></span> <span data-ttu-id="f38e9-168">Další informace naleznete v tématu [\<federationConfiguration>](federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f38e9-168">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>

<span data-ttu-id="f38e9-169">`<identityConfiguration>`Element je reprezentován <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="f38e9-169">The `<identityConfiguration>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> class.</span></span> <span data-ttu-id="f38e9-170">Oddíl konfigurace identity je reprezentovaný <xref:System.IdentityModel.Configuration.IdentityConfiguration> třídou.</span><span class="sxs-lookup"><span data-stu-id="f38e9-170">An identity configuration section is represented by the <xref:System.IdentityModel.Configuration.IdentityConfiguration> class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f38e9-171">Určení následujících prvků jako podřízených elementů `<identityConfiguration>` elementu je zastaralé, přestože chování je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="f38e9-171">Specifying the following elements as child elements of the `<identityConfiguration>` element has been deprecated, although the behavior is still supported for backward compatibility.</span></span> <span data-ttu-id="f38e9-172">Tyto prvky by měly být místo toho zadány pod [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) prvkem.</span><span class="sxs-lookup"><span data-stu-id="f38e9-172">These elements should, instead, be specified under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span>
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a><span data-ttu-id="f38e9-173">Příklad</span><span class="sxs-lookup"><span data-stu-id="f38e9-173">Example</span></span>

<span data-ttu-id="f38e9-174">Následující příklad vytvoří konfiguraci identity s názvem "alternateConfiguration".</span><span class="sxs-lookup"><span data-stu-id="f38e9-174">The following example creates an identity configuration named "alternateConfiguration".</span></span> <span data-ttu-id="f38e9-175">Konfigurace identity určuje výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="f38e9-175">The identity configuration specifies default settings.</span></span>

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a><span data-ttu-id="f38e9-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="f38e9-176">See also</span></span>

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
