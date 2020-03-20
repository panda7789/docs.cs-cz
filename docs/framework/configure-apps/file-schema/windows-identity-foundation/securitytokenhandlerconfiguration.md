---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152564"
---
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration>
Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
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
|saveBootstrapContext|Určuje, zda mají být tokeny bootstrap zahrnuty do tokenu relace. Hodnota může být také nastavena na kolekci obslužné rutiny tokenu nastavením atributu `saveBootstrapContext` na elementu [ \<identityConfiguration>.](identityconfiguration.md) Hodnota nastavená v kolekci obslužné rutiny tokenu přepíše hodnotu nastavenou ve službě.|  
|maximumClockSkew|A, <xref:System.TimeSpan> který určuje maximální povolené hodiny zkosení. Řídí maximální povolené hodiny zkosení při provádění operací citlivých na čas, jako je například ověření doby vypršení platnosti relace přihlášení. Výchozí hodnota je 5 minut, "00:05:00". Další informace o zadávání <xref:System.TimeSpan> hodnot naleznete v tématu [Timespan Values](../windows-workflow-foundation/index.md). Maximální zkosení hodin může být také `maximumClockSkew` nastaveno na úrovni služby nastavením atributu na elementu [ \<identityConfiguration>.](identityconfiguration.md) Hodnota nastavená v kolekci obslužné rutiny tokenu přepíše hodnotu nastavenou ve službě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|Určuje sadu identifikátorů URI, které jsou přijatelnými identifikátory této předávající strany. Nepovinný parametr.|  
|[\<>mezipamětí](caches.md)|Registruje mezipaměti používané pro tokeny relace a detekci opětovného přehrání tokenů. Lze zadat na úrovni služby nebo na kolekci obslužné rutiny tokenu zabezpečení. Nepovinný parametr.|  
|[\<>ověření certifikátu](certificatevalidation.md)|Řídí nastavení, která obslužné rutiny tokenů používají k ověření certifikátů. Lze zadat na úrovni služby nebo na kolekci obslužné rutiny tokenu zabezpečení. Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována s vlastním validátorem. Nepovinný parametr.|  
|[\<>issuerNameRegistry](issuernameregistry.md)|Konfiguruje registr názvů vystavitele, který používají obslužné rutiny v kolekci obslužné rutiny tokenu. Nepovinný parametr.|  
|[\<>překladače tokenu](issuertokenresolver.md)|Registruje překladač tokenů vystavitelů, který používají obslužné rutiny v kolekci obslužné rutiny tokenu. Překladač tokenů vystavithonu se používá k vyřešení podpisového tokenu na příchozích tokenech a zprávách. Nepovinný parametr.|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|Registruje překladač tokenů služby, který používají obslužné rutiny v kolekci obslužné rutiny tokenu. Překládání tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách. Nepovinný parametr.|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Povolí detekci opětovného přehrání tokenů a určuje dobu vypršení platnosti tokenů. Lze zadat na úrovni služby nebo na kolekci obslužné rutiny tokenu zabezpečení. Nepovinný parametr.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány s koncovým bodem.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část obsahuje hodnoty <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> vlastností objektu. Nastavení nakonfigurovaná v této části přepisují nastavení nakonfigurovaná ve službě. Některá z těchto nastavení mohou být zase přepsána nastaveními, která jsou určena při přidání obslužné rutiny do kolekce obslužné rutiny tokenu zabezpečení.  
  
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
