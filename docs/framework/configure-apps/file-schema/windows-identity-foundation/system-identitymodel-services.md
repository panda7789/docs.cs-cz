---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 9728f3caee4dba367e4fc4a3e68213b1055cc3d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793780"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="f78e1-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="f78e1-102">\<system.identityModel.services></span></span>
<span data-ttu-id="f78e1-103">Konfigurační oddíl pro ověřování pomocí protokolu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="f78e1-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="f78e1-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="f78e1-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f78e1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f78e1-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f78e1-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f78e1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f78e1-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f78e1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f78e1-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="f78e1-108">Attributes</span></span>  
 <span data-ttu-id="f78e1-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="f78e1-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f78e1-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f78e1-110">Child Elements</span></span>  
  
|<span data-ttu-id="f78e1-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="f78e1-111">Element</span></span>|<span data-ttu-id="f78e1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f78e1-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f78e1-113">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="f78e1-113">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="f78e1-114">Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> z modulů HTTP (SAM).</span><span class="sxs-lookup"><span data-stu-id="f78e1-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f78e1-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f78e1-115">Parent Elements</span></span>  
 <span data-ttu-id="f78e1-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="f78e1-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f78e1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f78e1-117">Remarks</span></span>  
 <span data-ttu-id="f78e1-118">Přidat `<system.identityModel.services>` části do konfiguračního souboru aplikace k poskytování nastavení SAM a WSFAM.</span><span class="sxs-lookup"><span data-stu-id="f78e1-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f78e1-119">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity ve vašem kódu, deklarace identity Správce autorizací (<xref:System.Security.Claims.ClaimsAuthorizationManager>) a zásad, který se používá pro autorizační rozhodnutí, které jsou konfigurovány pomocí `<identityConfiguration>` element, který je implicitně nebo explicitně odkazovat z `<federationConfiguration>` elementu v této části.</span><span class="sxs-lookup"><span data-stu-id="f78e1-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="f78e1-120">Další informace najdete v tématu **poznámky** pod [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f78e1-120">For more information, see the **Remarks** under the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="f78e1-121">`<system.identityModel.services>` Části je reprezentována <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> třídy.</span><span class="sxs-lookup"><span data-stu-id="f78e1-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="f78e1-122">Kolekce podřízených `<federationConfiguration>` prvky nakonfigurovali v sekci je reprezentována <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="f78e1-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f78e1-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f78e1-123">Example</span></span>  
 <span data-ttu-id="f78e1-124">Následující kód XML ukazuje, jak přidat `<system.identityModel.services>` části ke konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="f78e1-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="f78e1-125">Musíte je napřed přidat části deklarace pro obě `<system.identityModel.services>` oddílu a `<system.identityModel>` oddíly.</span><span class="sxs-lookup"><span data-stu-id="f78e1-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="f78e1-126">(Po přidání `<system.identityModel.services>` oddílu, měli byste také přidat deklaraci `<system.identityModel>` části a ujistěte se, že výchozí `<identityConfiguration>` část lze vytvořit modul runtime, v případě potřeby.) Po přidání deklarace části můžete nakonfigurovat v nastavení federovaného ověřování `<system.identityModel.services>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f78e1-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
