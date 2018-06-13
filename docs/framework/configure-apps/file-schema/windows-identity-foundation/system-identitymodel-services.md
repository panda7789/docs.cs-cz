---
title: '&lt;system.identityModel.services&gt;'
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ca108d7dd0498b0d7c08bb632ab45c7229ff58c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757044"
---
# <a name="ltsystemidentitymodelservicesgt"></a><span data-ttu-id="ae5fb-102">&lt;system.identityModel.services&gt;</span><span class="sxs-lookup"><span data-stu-id="ae5fb-102">&lt;system.identityModel.services&gt;</span></span>
<span data-ttu-id="ae5fb-103">Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="ae5fb-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="ae5fb-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae5fb-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae5fb-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae5fb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ae5fb-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae5fb-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae5fb-108">Attributes</span></span>  
 <span data-ttu-id="ae5fb-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae5fb-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ae5fb-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae5fb-110">Child Elements</span></span>  
  
|<span data-ttu-id="ae5fb-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae5fb-111">Element</span></span>|<span data-ttu-id="ae5fb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ae5fb-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae5fb-113">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ae5fb-113">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="ae5fb-114">Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> modulů HTTP (SAM).</span><span class="sxs-lookup"><span data-stu-id="ae5fb-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae5fb-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae5fb-115">Parent Elements</span></span>  
 <span data-ttu-id="ae5fb-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae5fb-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae5fb-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae5fb-117">Remarks</span></span>  
 <span data-ttu-id="ae5fb-118">Přidat `<system.identityModel.services>` části do vaší aplikace konfiguračního souboru k poskytování nastavení SAM a WSFAM.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae5fb-119">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třída k poskytování řízení přístupu na základě deklarace identity ve vašem kódu, Správce autorizací deklarace identity (<xref:System.Security.Claims.ClaimsAuthorizationManager>) a zásad, který se používá pro autorizační rozhodnutí konfigurované prostřednictvím `<identityConfiguration>` element, který je odkazován implicitně nebo explicitně z `<federationConfiguration>` elementu v této části.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="ae5fb-120">Další informace najdete v tématu **poznámky** pod [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-120">For more information, see the **Remarks** under the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="ae5fb-121">`<system.identityModel.services>` Část je reprezentována <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> třídy.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="ae5fb-122">Kolekce podřízených `<federationConfiguration>` elementy nakonfigurovali v sekci je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae5fb-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae5fb-123">Example</span></span>  
 <span data-ttu-id="ae5fb-124">Následující kód XML ukazuje, jak přidat `<system.identityModel.services>` oddíl konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="ae5fb-125">Je nutné nejdříve přidat části deklarace pro oba `<system.identityModel.services>` části a `<system.identityModel>` části.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="ae5fb-126">(Když přidáte `<system.identityModel.services>` části, měli byste také přidat deklaraci pro `<system.identityModel>` části zajistit, aby výchozí `<identityConfiguration>` části lze vytvořit pomocí modulu runtime, v případě potřeby.) Po nebyly přidané deklarace oddílu, můžete nakonfigurovat nastavení federovaného ověřování v rámci `<system.identityModel.services>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ae5fb-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
