---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152501"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="ed979-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="ed979-102">\<system.identityModel.services></span></span>
<span data-ttu-id="ed979-103">Konfigurační část pro ověřování pomocí protokolu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="ed979-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="ed979-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed979-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed979-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span><span class="sxs-lookup"><span data-stu-id="ed979-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed979-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed979-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed979-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ed979-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ed979-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ed979-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed979-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="ed979-109">Attributes</span></span>  
 <span data-ttu-id="ed979-110">Žádný</span><span class="sxs-lookup"><span data-stu-id="ed979-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ed979-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ed979-111">Child Elements</span></span>  
  
|<span data-ttu-id="ed979-112">Element</span><span class="sxs-lookup"><span data-stu-id="ed979-112">Element</span></span>|<span data-ttu-id="ed979-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ed979-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed979-114">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="ed979-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="ed979-115">Obsahuje nastavení, která <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurují moduly HTTP (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="ed979-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed979-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ed979-116">Parent Elements</span></span>  
 <span data-ttu-id="ed979-117">Žádný</span><span class="sxs-lookup"><span data-stu-id="ed979-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed979-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed979-118">Remarks</span></span>  
 <span data-ttu-id="ed979-119">Přidejte `<system.identityModel.services>` oddíl do konfiguračního souboru aplikace a zadejte nastavení pro sam a wsfam.</span><span class="sxs-lookup"><span data-stu-id="ed979-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ed979-120">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě<xref:System.Security.Claims.ClaimsAuthorizationManager>deklarací identity ve vašem kódu, správce `<identityConfiguration>` autorizace deklarací ( ) a `<federationConfiguration>` zásady, které se používají k rozhodování o autorizaci jsou konfigurovány prostřednictvím prvku, který je implicitně nebo explicitně odkazován z prvku v této části.</span><span class="sxs-lookup"><span data-stu-id="ed979-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="ed979-121">Další informace naleznete v **části Poznámky** v části [ \<federationConfiguration>](federationconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="ed979-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="ed979-122">Oddíl `<system.identityModel.services>` je reprezentován <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> třídou.</span><span class="sxs-lookup"><span data-stu-id="ed979-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="ed979-123">Kolekce podřízených `<federationConfiguration>` prvků nakonfigurovaných <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> v části je reprezentována třídou.</span><span class="sxs-lookup"><span data-stu-id="ed979-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed979-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed979-124">Example</span></span>  
 <span data-ttu-id="ed979-125">Následující jazyk XML ukazuje, `<system.identityModel.services>` jak přidat oddíl do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ed979-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="ed979-126">Nejprve je nutné přidat deklarace oddílů `<system.identityModel.services>` pro oddíl i oddíly. `<system.identityModel>`</span><span class="sxs-lookup"><span data-stu-id="ed979-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="ed979-127">(Když přidáte `<system.identityModel.services>` oddíl, měli byste také přidat `<system.identityModel>` deklaraci pro `<identityConfiguration>` oddíl, abyste zajistili, že v případě potřeby může být výchozí oddíl vytvořen za běhu.) Po přidání deklarací oddílu můžete nakonfigurovat federovaná `<system.identityModel.services>` nastavení ověřování pod elementem.</span><span class="sxs-lookup"><span data-stu-id="ed979-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
