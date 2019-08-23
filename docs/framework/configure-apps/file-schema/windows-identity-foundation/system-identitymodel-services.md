---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943662"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="fc3e6-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="fc3e6-102">\<system.identityModel.services></span></span>
<span data-ttu-id="fc3e6-103">Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="fc3e6-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="fc3e6-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc3e6-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc3e6-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc3e6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="fc3e6-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc3e6-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc3e6-108">Attributes</span></span>  
 <span data-ttu-id="fc3e6-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc3e6-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fc3e6-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc3e6-110">Child Elements</span></span>  
  
|<span data-ttu-id="fc3e6-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc3e6-111">Element</span></span>|<span data-ttu-id="fc3e6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fc3e6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc3e6-113">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="fc3e6-113">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="fc3e6-114">Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> moduly protokolu HTTP (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> a (SAM).</span><span class="sxs-lookup"><span data-stu-id="fc3e6-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc3e6-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc3e6-115">Parent Elements</span></span>  
 <span data-ttu-id="fc3e6-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc3e6-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc3e6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc3e6-117">Remarks</span></span>  
 <span data-ttu-id="fc3e6-118">`<system.identityModel.services>` Přidejte oddíl do konfiguračního souboru aplikace a poskytněte tak nastavení pro Sam a WSFAM.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc3e6-119"><xref:System.IdentityModel.Services.ClaimsPrincipalPermission> Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu se Správce autorizací deklarací identity<xref:System.Security.Claims.ClaimsAuthorizationManager>() a zásady, které se používají `<identityConfiguration>` k rozhodování o autorizaci, nakonfigurují prostřednictvím prvek, který je implicitně nebo explicitně odkazován z `<federationConfiguration>` prvku v této části.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="fc3e6-120">Další informace naleznete v poznámkách pod [ \<prvkem federationConfiguration >](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="fc3e6-120">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="fc3e6-121">Oddíl je reprezentován <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>třídou. `<system.identityModel.services>`</span><span class="sxs-lookup"><span data-stu-id="fc3e6-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="fc3e6-122">Kolekce podřízených `<federationConfiguration>` prvků nakonfigurovaných v oddílu je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> třídou.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc3e6-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc3e6-123">Example</span></span>  
 <span data-ttu-id="fc3e6-124">Následující kód XML ukazuje, jak přidat `<system.identityModel.services>` oddíl do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="fc3e6-125">Nejdřív musíte přidat deklarace oddílů pro `<system.identityModel.services>` oddíl `<system.identityModel>` i oddíly.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="fc3e6-126">(Když přidáte `<system.identityModel.services>` oddíl, měli byste také přidat deklaraci `<system.identityModel>` pro oddíl, abyste měli jistotu, že v případě `<identityConfiguration>` potřeby může modul runtime vytvořit výchozí oddíl.) Po přidání oddílu deklarace můžete nakonfigurovat nastavení federovaného ověřování pod `<system.identityModel.services>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="fc3e6-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"   
        issuer="http://localhost:15839/wsFederationSTS/Issue"   
        realm="http://localhost:50969/" reply="http://localhost:50969/"   
        requireHttps="false"   
        signOutReply="http://localhost:50969/SignedOutPage.html"   
        signOutQueryString="Param1=value2&Param2=value2"   
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
