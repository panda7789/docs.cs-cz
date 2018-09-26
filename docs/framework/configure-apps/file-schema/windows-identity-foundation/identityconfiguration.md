---
title: '&lt;identityConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 11ba7df79ead1693fc6828aeabde413237680737
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075654"
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
Určuje nastavení identit na úrovni služby.  
  
 \<system.identityModel>  
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
|name|Název oddílu konfigurace identity. Tento název slouží k odkazování konkrétní konfigurační oddíl. Pokud ne `name` atribut zadán, oddíl definuje výchozí konfiguraci. Výchozí konfigurace je vždy používá pro scénáře pasivní federaci. Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.|  
|saveBootstrapContext|Určuje, zda mají být zahrnuty bootstrap tokeny v tokenu relace. Hodnota může také nastavit na kolekci obslužné rutiny tokenů nastavením `saveBootstrapContext` atribut na [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu. Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.|  
|maximumClockSkew|A <xref:System.TimeSpan> , která určuje maximální povolený posun. Určuje maximální povolený posun při provádění operace citlivé na čas, jako je například ověřování čas vypršení platnosti relace přihlášení. Výchozí hodnota je 5 minut, "00: 05:00". Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v článku [hodnoty prvku Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maximální posun může také nastavit na kolekci obslužné rutiny tokenů nastavením `maximumClockSkew` atribut na [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu. Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<ukládá do mezipaměti >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Zaregistruje mezipaměti používané pro tokeny relace a rozpoznání opětovného přehrání tokenu. Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení. Volitelné.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů. Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení. Volitelné.|  
|[\<komponenty claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity. Volitelné.|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Zaregistruje Správce autorizací deklarace identity pro příchozí deklarace identity. Volitelné.|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Určuje sadu požadované deklarace identit pro příchozí tokeny zabezpečení. Volitelné.|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Určuje kolekci obslužné rutiny tokenů zabezpečení. Je možné zadat nuly nebo více kolekcí obslužné rutiny tokenů zabezpečení. Volitelné.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů. Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení. Volitelné.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Poskytuje konfiguraci pro povolení technologie Windows Identity Foundation (WIF) možnosti v aplikacích.|  
  
## <a name="remarks"></a>Poznámky  
 Více identit konfigurace mohou být definovány, každý s jedinečným názvem. Chování vypadá takto:  
  
1.  Pokud ne `<identityConfiguration>` zadaný element. Výchozí konfigurace identity se za běhu a zadat výchozí hodnoty.  
  
2.  Pokud jeden `<identityConfiguration>` zadaný element. To je výchozí konfigurace identity. Nezáleží, jestli je soubor s názvem nebo nepojmenované.  
  
3.  Pokud je položek víc `<identityConfiguration>` zadaných elementů. Nepojmenované prvek určuje výchozí konfigurace identity. Doporučuje, pokud zadáte více `<identityConfiguration>` prvky, jeden z nich měli nepojmenované.  
  
> [!WARNING]
>  Pokud zadáte více `<identityConfiguration>` prvky, jeden z nich měli nepojmenované. Nepojmenované prvek bude výchozí konfigurace identity.  
  
 Některé z nastavení uvedená v `<identityConfiguration>` element lze přepsat nastavením na kolekci obslužné rutiny tokenů zabezpečení nebo nastavení obslužné rutiny tokenů zabezpečení.  
  
> [!IMPORTANT]
>  Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity ve vašem kódu, konfigurace identity, na který odkazuje `<federationConfiguration>` element nakonfiguruje Správce autorizací deklarace identity a zásadu, která se využívá k Prognózování rozhodování o autorizaci. To platí dokonce i ve scénářích, které nejsou pasivní scénáře pro webové, například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založena na Web. Pokud aplikace není pasivní webové aplikace [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) – element (a jeho podřízených elementů zásad, pokud jsou k dispozici) konfigurace odkazované identity jsou jenom nastavení, která použijí. Všechna ostatní nastavení se ignorují. Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.  
  
 `<identityConfiguration>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> třídy. Identit konfigurační oddíl představuje <xref:System.IdentityModel.Configuration.IdentityConfiguration> třídy.  
  
> [!IMPORTANT]
>  Zadáním následujících prvků jako podřízených elementů `<identityConfiguration>` prvek se už nepoužívá, i když je chování stále podporována z důvodu zpětné kompatibility. Tyto prvky musí, místo toho nastavit v rámci [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu.  
>   
>  -   [\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se vytvoří konfigurace identity s názvem "alternateConfiguration". Konfigurace identity Určuje výchozí nastavení.  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
