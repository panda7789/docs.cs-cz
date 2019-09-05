---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251970"
---
# <a name="issuernameregistry"></a>\<issuerNameRegistry>
Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerNameRegistry >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
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
|– typ|Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy. Další informace o tom, jak zadat vlastní `type`, naleznete v tématu [odkazy na vlastní typ].|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|Pokud atribut určuje registr názvu vystavitele založený na konfiguraci <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (třída), [ \<](trustedissuers.md) musí být zadaný element trustedIssuers >. `type` Element trustedIssuers > může převzít `<add>`, `<clear>`nebo `<remove>` prvky jako podřízené prvky. [ \<](trustedissuers.md)|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny tokeny vystavitele se ověřují pomocí registru názvu vystavitele. Toto je objekt, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy. Registr názvu vystavitele se používá k přidružení symbolického názvu k kryptografickému materiálu, který je nutný k ověření podpisů tokenů vyprodukovaných odpovídajícím vystavitelem. Registr názvů vystavitele uchovává seznam vystavitelů, které jsou důvěryhodné pro aplikaci předávající strany (RP). Typ registru názvu vystavitele je zadaný pomocí `type` atributu. `<issuerNameRegistry>` Element může mít jeden nebo více podřízených elementů, které poskytují konfiguraci pro zadaný typ. Zadáte logiku, která zpracovává tyto podřízené prvky přepsáním <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.  
  
 WIF poskytuje jeden název vystavitele jako typ registru v poli, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třída. Tato třída používá sadu certifikátů důvěryhodných vystavitelů, které jsou zadány v konfiguraci. Vyžaduje podřízený element `<trustedIssuers>`konfigurace, pod kterým je nakonfigurované shromažďování certifikátů důvěryhodných vystavitelů. Důvěryhodné certifikáty jsou určeny pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány nebo odebrány z kolekce pomocí `<add>`prvků, `<clear>`nebo `<remove>` .  
  
 Element je reprezentován <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>třídou. `<issuerNameRegistry>`  
  
> [!NOTE]
> Určení prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. `<issuerNameRegistry>` Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
