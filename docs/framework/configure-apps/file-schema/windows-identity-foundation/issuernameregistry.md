---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251970"
---
# \<issuerNameRegistry>
Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
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
|typ|Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy. Další informace o tom, jak zadat vlastní `type` , naleznete v tématu [odkazy na vlastní typ].|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|Pokud `type` atribut určuje registr názvu vystavitele založený na konfiguraci ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třída), [\<trustedIssuers>](trustedissuers.md) musí být zadaný element. [\<trustedIssuers>](trustedissuers.md)Element může převzít `<add>` prvky, `<clear>` nebo `<remove>` jako podřízené prvky.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny tokeny vystavitele se ověřují pomocí registru názvu vystavitele. Toto je objekt, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy. Registr názvu vystavitele se používá k přidružení symbolického názvu k kryptografickému materiálu, který je nutný k ověření podpisů tokenů vyprodukovaných odpovídajícím vystavitelem. Registr názvů vystavitele uchovává seznam vystavitelů, které jsou důvěryhodné pro aplikaci předávající strany (RP). Typ registru názvu vystavitele je zadaný pomocí `type` atributu. `<issuerNameRegistry>`Element může mít jeden nebo více podřízených elementů, které poskytují konfiguraci pro zadaný typ. Zadáte logiku, která zpracovává tyto podřízené prvky přepsáním <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.  
  
 WIF poskytuje jeden název vystavitele jako typ registru v poli, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> Třída. Tato třída používá sadu certifikátů důvěryhodných vystavitelů, které jsou zadány v konfiguraci. Vyžaduje podřízený element konfigurace, `<trustedIssuers>` pod kterým je nakonfigurované shromažďování certifikátů důvěryhodných vystavitelů. Důvěryhodné certifikáty jsou určeny pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány nebo odebrány z kolekce pomocí `<add>` `<clear>` prvků, nebo `<remove>` .  
  
 `<issuerNameRegistry>`Element je reprezentován <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> třídou.  
  
> [!NOTE]
> Určení `<issuerNameRegistry>` prvku jako podřízený element [\<identityConfiguration>](identityconfiguration.md) elementu je zastaralé, ale je stále podporováno z důvodu zpětné kompatibility. Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
