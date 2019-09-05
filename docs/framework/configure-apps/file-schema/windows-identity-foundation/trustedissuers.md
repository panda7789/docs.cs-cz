---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251757"
---
# <a name="trustedissuers"></a>\<trustedIssuers>
Nakonfiguruje seznam certifikátů důvěryhodných vystavitelů, které používá registr názvů vystavitelů na<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>základě konfigurace ().  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerNameRegistry >** ](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trustedIssuers >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|Přidá certifikát do kolekce důvěryhodných vystavitelů. Certifikát je zadán s `thumbprint` atributem. Tento atribut je povinný a měl by obsahovat formát ASN. 1 kódovaný v rámci kryptografického otisku certifikátu. `name` Atribut je nepovinný a dá se použít k zadání popisného názvu pro certifikát.|  
|`<clear>`|Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.|  
|`<remove thumbprint=xs:string>`|Odebere certifikát z kolekce důvěryhodných vystavitelů. Certifikát je zadán s `thumbprint` atributem. Tento atribut je vyžadován.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Nakonfiguruje registr názvu vystavitele. **Důležité:**  Atribut elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl elementplatný.`<trustedIssuers>` `<issuerNameRegistry>` `type`|  
  
## <a name="remarks"></a>Poznámky  
 Windows Identity Foundation (WIF) poskytuje jednu implementaci <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy mimo pole <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , třídu. Registr názvů vystavitele konfigurace uchovává seznam důvěryhodných vystavitelů načtených z konfigurace. Seznam přidruží jednotlivé názvy vystavitelů k certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných vystavitelem. Seznam certifikátů důvěryhodných vystavitelů je určen pod `<trustedIssuers>` prvkem. Každý prvek v seznamu přidruží název vystavitele pomocí certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných tímto vystavitelem. Důvěryhodné certifikáty jsou zadány pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány do kolekce pomocí `<add>` elementu. Můžete vymazat nebo odebrat vystavitele (certifikáty) ze seznamu pomocí `<clear>` prvků a. `<remove>`  
  
 Atribut elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl elementplatný.`<trustedIssuers>` `<issuerNameRegistry>` `type`  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
