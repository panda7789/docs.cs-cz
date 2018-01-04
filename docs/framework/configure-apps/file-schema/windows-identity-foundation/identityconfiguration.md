---
title: '&lt;identityConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48f9eef329f5d2e0e751fd2a03b0d3af9ddc355c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
Určuje nastavení identity úrovně služeb.  
  
 \<system.identityModel >  
\<identityConfiguration >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Název konfiguračního oddílu identity. Tento název vám pomůže odkazovat na konkrétní konfigurační oddíl. Pokud žádné `name` zadán atribut, v části definuje výchozí konfiguraci. Výchozí konfigurace je vždy používá pro scénáře pasivní federace. Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.|  
|saveBootstrapContext|Určuje, zda bootstrap tokeny mají být zahrnuty v tokenu relace. Hodnota může být také nastaven na kolekci obslužná rutina tokenu nastavením `saveBootstrapContext` atributu u [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element. Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.|  
|maximumClockSkew|A <xref:System.TimeSpan> , určuje zkosení maximální povolené hodiny. Určuje maximální povolený hodiny zkosení při provádění operace náročné na čas, jako je například ověřování čas vypršení platnosti relace přihlášení. Výchozí hodnota je 5 minut, "00: 05:00". Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v části [časový interval hodnoty](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maximální hodiny zkosení může být také nastaven na kolekci obslužná rutina tokenu nastavením `maximumClockSkew` atributu u [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element. Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<ukládá do mezipaměti >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Zaregistruje mezipamětí použít pro tokeny relace a rozpoznání opětovného přehrání tokenu. Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení. Volitelné.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů. Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení. Volitelné.|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity. Volitelné.|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Zaregistruje Správce autorizací příchozí deklarace identity deklarací identity. Volitelné.|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Určuje sadu požadované deklarací identity pro příchozí tokeny zabezpečení. Volitelné.|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Určuje kolekci rutin tokenu zabezpečení. Je možné zadat nula nebo více kolekcí obslužné rutiny tokenu zabezpečení. Volitelné.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů. Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení. Volitelné.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Poskytuje konfigurace pro povolení možnosti Windows Identity Foundation (WIF) v aplikacích.|  
  
## <a name="remarks"></a>Poznámky  
 Více identit, které se konfigurace může být definována, každý s jedinečným názvem. Toto chování je následujícím způsobem:  
  
1.  Pokud žádné `<identityConfiguration>` zadaný element. Výchozí konfigurace identity je vytvoří za běhu a zadat výchozí hodnoty.  
  
2.  Pokud jeden `<identityConfiguration>` zadaný element. To je výchozí konfigurace identity. Nezáleží, jestli je s názvem nebo nepojmenované.  
  
3.  Pokud je to více `<identityConfiguration>` elementy nejsou zadány. Nepojmenované element určuje výchozí konfigurace identity. Dále je doporučeno při zadávání více `<identityConfiguration>` elementy, jeden z nich měli nepojmenované.  
  
> [!WARNING]
>  Pokud zadáte více `<identityConfiguration>` elementy, jeden z nich měli nepojmenované. Nepojmenované prvek bude výchozí konfigurace identity.  
  
 Některá nastavení zadané v `<identityConfiguration>` element lze přepsat nastavením na kolekci obslužná rutina tokenu zabezpečení nebo nastavení na jednotlivých zabezpečení tokenu obslužné rutiny.  
  
> [!IMPORTANT]
>  Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třída k poskytování řízení přístupu na základě deklarace identity ve vašem kódu konfiguraci identity, která odkazuje `<federationConfiguration>` element nakonfiguruje Správce autorizací deklarace identity a zásadu, která se používá k zajištění rozhodnutí o autorizaci. Je to ve scénářích, které nejsou pasivní scénáře webového, například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založené na webu. Pokud aplikace není pasivní webové aplikace [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) element (a jeho podřízených elementů zásad, pokud existuje) konfigurace odkazované identity jsou jenom nastavení použité. Všechna ostatní nastavení se ignorují. Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.  
  
 `<identityConfiguration>` Element je reprezentována <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> třídy. Oddíl konfigurace identity je reprezentována <xref:System.IdentityModel.Configuration.IdentityConfiguration> třídy.  
  
> [!IMPORTANT]
>  Zadání následující prvky jako podřízených elementů `<identityConfiguration>` element se už nepoužívá, i když chování je stále podporováno pro zpětnou kompatibilitu. Tyto prvky měli, místo toho zadat v rámci [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element.  
>   
>  -   [\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří konfigurace aplikace identity s názvem "alternateConfiguration". Konfigurace identity Určuje výchozí nastavení.  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
