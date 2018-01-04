---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ac7284fa418c1540582c40bd744e913ba31aa881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
Poskytuje konfigurace pro kolekci tokenu obslužné rutiny.  
  
 \<system.identityModel >  
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
|saveBootstrapContext|Určuje, zda bootstrap tokeny mají být zahrnuty v tokenu relace. Hodnota může být také nastaven na kolekci obslužná rutina tokenu nastavením `saveBootstrapContext` atributu u [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element. Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.|  
|maximumClockSkew|A <xref:System.TimeSpan> , určuje zkosení maximální povolené hodiny. Určuje maximální povolený hodiny zkosení při provádění operace náročné na čas, jako je například ověřování čas vypršení platnosti relace přihlášení. Výchozí hodnota je 5 minut, "00: 05:00". Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v části [časový interval hodnoty](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maximální hodiny zkosení může být také nastaven na úrovni služby nastavením `maximumClockSkew` atributu u [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element. Hodnota nastavení kolekce obslužná rutina tokenu přepíše hodnotu nastavit na službu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Určuje sadu identifikátorů URI, které jsou přípustné identifikátory této předávající strany. Volitelné.|  
|[\<ukládá do mezipaměti >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Zaregistruje mezipamětí použít pro tokeny relace a rozpoznání opětovného přehrání tokenu. Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení. Volitelné.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů. Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení. Tato nastavení jsou přepsat, pokud obslužná rutina specifická nakonfigurovaný s vlastním validátoru. Volitelné.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Nakonfiguruje registru název vystavitele, který je používán obslužné rutiny v kolekci obslužná rutina tokenu. Volitelné.|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Zaregistruje překladač vystavitele tokenu, který je používán obslužné rutiny v kolekci obslužná rutina tokenu. Překladač vystavitele tokenu se používá k překladu podpisový token na příchozí tokeny a zprávy. Volitelné.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Zaregistruje překladač tokenu služby, který je používán obslužné rutiny v kolekci obslužná rutina tokenu. Překladač tokenu služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy. Volitelné.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů. Můžete zadat na úrovni služby, nebo na kolekci obslužná rutina tokenu zabezpečení. Volitelné.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část obsahuje hodnoty vlastností pro <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objektu. Nastavení v této části přepsat nakonfigurovaným na službu. Některá z těchto nastavení je, pak možné přepsat nastavení, které jsou uvedeny během obslužná rutina se přidá do kolekce obslužná rutina tokenu zabezpečení.  
  
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
