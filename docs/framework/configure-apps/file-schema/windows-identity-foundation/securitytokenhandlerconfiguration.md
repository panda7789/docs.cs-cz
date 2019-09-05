---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251890"
---
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration>
Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**  
  
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
|saveBootstrapContext|Určuje, zda mají být do tokenu relace zahrnuty tokeny Bootstrap. Hodnotu lze také nastavit pro kolekci obslužných rutin tokenů nastavením `saveBootstrapContext` atributu [ \<v elementu IdentityConfiguration >](identityconfiguration.md) . Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.|  
|maximumClockSkew|A <xref:System.TimeSpan> určuje maximální povolený časový posun. Určuje maximální povolený časový posun při provádění operací závislých na čase, jako je například ověření doby platnosti přihlašovací relace. Výchozí hodnota je 5 minut, "00:05:00". Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md). Maximální hodinový posun lze také nastavit na úrovni služby nastavením `maximumClockSkew` atributu [ \<u prvku IdentityConfiguration >](identityconfiguration.md) . Hodnota nastavená v kolekci obslužných rutin tokenu Přepisuje hodnotu nastavenou ve službě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory této předávající strany. Volitelný parametr.|  
|[\<caches>](caches.md)|Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Volitelný parametr.|  
|[\<certificateValidation>](certificatevalidation.md)|Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru. Volitelný parametr.|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů. Volitelný parametr.|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu. Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách. Volitelný parametr.|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu. Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách. Volitelný parametr.|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů. Lze zadat na úrovni služby nebo v kolekci obslužných rutin tokenu zabezpečení. Volitelný parametr.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část poskytuje hodnoty <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> vlastností objektu. Nastavení konfigurovaná v této části přepíší ty, které jsou ve službě nakonfigurované. Některá z těchto nastavení lze naopak přepsat nastavením, která jsou zadána při přidání obslužné rutiny do kolekce obslužné rutiny tokenu zabezpečení.  
  
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
