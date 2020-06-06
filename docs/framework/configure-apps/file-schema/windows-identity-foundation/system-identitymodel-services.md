---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152501"
---
# \<system.identityModel.services>
<span data-ttu-id="25b2a-102">Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="25b2a-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="25b2a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25b2a-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25b2a-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="25b2a-104">Attributes and Elements</span></span>  
 <span data-ttu-id="25b2a-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="25b2a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25b2a-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="25b2a-106">Attributes</span></span>  
 <span data-ttu-id="25b2a-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="25b2a-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25b2a-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="25b2a-108">Child Elements</span></span>  
  
|<span data-ttu-id="25b2a-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="25b2a-109">Element</span></span>|<span data-ttu-id="25b2a-110">Description</span><span class="sxs-lookup"><span data-stu-id="25b2a-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="25b2a-111">Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> moduly protokolu HTTP (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="25b2a-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25b2a-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="25b2a-112">Parent Elements</span></span>  
 <span data-ttu-id="25b2a-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="25b2a-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25b2a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25b2a-114">Remarks</span></span>  
 <span data-ttu-id="25b2a-115">Přidejte `<system.identityModel.services>` oddíl do konfiguračního souboru aplikace a poskytněte tak nastavení pro Sam a WSFAM.</span><span class="sxs-lookup"><span data-stu-id="25b2a-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="25b2a-116">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích v kódu jsou deklarace identity Manageru ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) a zásady, které se používají k rozhodování o autorizaci, konfigurovány prostřednictvím `<identityConfiguration>` elementu, který je implicitně nebo explicitně odkazován z `<federationConfiguration>` prvku v této části.</span><span class="sxs-lookup"><span data-stu-id="25b2a-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="25b2a-117">Další informace naleznete v **poznámkách** pod [\<federationConfiguration>](federationconfiguration.md) prvkem.</span><span class="sxs-lookup"><span data-stu-id="25b2a-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="25b2a-118">`<system.identityModel.services>`Oddíl je reprezentován <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> třídou.</span><span class="sxs-lookup"><span data-stu-id="25b2a-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="25b2a-119">Kolekce podřízených `<federationConfiguration>` prvků nakonfigurovaných v oddílu je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> třídou.</span><span class="sxs-lookup"><span data-stu-id="25b2a-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25b2a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="25b2a-120">Example</span></span>  
 <span data-ttu-id="25b2a-121">Následující kód XML ukazuje, jak přidat `<system.identityModel.services>` oddíl do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="25b2a-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="25b2a-122">Nejdřív musíte přidat deklarace oddílů pro `<system.identityModel.services>` oddíl i `<system.identityModel>` oddíly.</span><span class="sxs-lookup"><span data-stu-id="25b2a-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="25b2a-123">(Když přidáte `<system.identityModel.services>` oddíl, měli byste také přidat deklaraci pro `<system.identityModel>` oddíl, abyste měli jistotu, že `<identityConfiguration>` v případě potřeby může modul runtime vytvořit výchozí oddíl.) Po přidání oddílu deklarace můžete nakonfigurovat nastavení federovaného ověřování pod `<system.identityModel.services>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="25b2a-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
