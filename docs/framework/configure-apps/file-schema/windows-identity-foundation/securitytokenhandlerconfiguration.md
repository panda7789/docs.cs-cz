---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793276"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
Poskytuje konfiguraci pro kolekci obslužné rutiny tokenů.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|saveBootstrapContext|Určuje, zda mají být zahrnuty bootstrap tokeny v tokenu relace. Hodnota může také nastavit na kolekci obslužné rutiny tokenů nastavením `saveBootstrapContext` atribut na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu. Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.|  
|maximumClockSkew|A <xref:System.TimeSpan> , která určuje maximální povolený posun. Určuje maximální povolený posun při provádění operace citlivé na čas, jako je například ověřování čas vypršení platnosti relace přihlášení. Výchozí hodnota je 5 minut, "00: 05:00". Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v článku [hodnoty prvku Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maximální posun může být rovněž nastaven na úrovni služby pomocí nastavení `maximumClockSkew` atribut na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu. Hodnota nastavení kolekce obslužná rutina tokenů přepíše hodnoty nastavené ve službě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Určuje sadu identifikátorů URI, které jsou přípustné identifikátory této předávající straně. Volitelné.|  
|[\<ukládá do mezipaměti >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Zaregistruje mezipaměti používané pro tokeny relace a rozpoznání opětovného přehrání tokenu. Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení. Volitelné.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů. Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení. Tato nastavení jsou přepsány, pokud jsou nakonfigurované vlastní validátor konkrétní obslužnou rutinou. Volitelné.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Nakonfiguruje registru názvu vystavitele, který se používá obslužné rutiny v kolekci obslužná rutina tokenů. Volitelné.|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Zaregistruje překladač tokenů vystavitele, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů. Překladač tokenů vystavitele se používá k překladu podpisový token na příchozí tokeny a zprávy. Volitelné.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Zaregistruje překladač tokenů služby, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů. Překladač tokenů služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy. Volitelné.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů. Můžete nastavit na úrovni služby nebo v kolekci obslužné rutiny tokenů zabezpečení. Volitelné.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část obsahuje hodnoty vlastností <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objektu. Přepsat nastavení nakonfigurovaná v této části porty nakonfigurované na službu. Některá z těchto nastavení můžete přepsat zase nastavením, které jsou zadány při obslužnou rutinu je přidán do kolekce obslužné rutiny tokenů zabezpečení.  
  
## <a name="example"></a>Příklad  
  
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
