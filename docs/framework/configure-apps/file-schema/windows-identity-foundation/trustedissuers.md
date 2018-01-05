---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 26f3d4f0b272168083bed2bbe249532181a6db67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
Nakonfiguruje seznam důvěryhodných vystavitelů certifikátů používaných registru název vystavitele založené na konfiguraci (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
\<trustedIssuers >  
  
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
|`<add thumbprint=xs:string name=xs:string>`|Přidá certifikát do kolekce důvěryhodných vystavitelů. Certifikát zadaný `thumbprint` atribut. Tento atribut je povinný a musí obsahovat kódovaný ASN.1 formu kryptografický otisk certifikátu. `name` Atribut je volitelné a lze zadat popisný název certifikátu.|  
|`<clear>`|Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.|  
|`<remove thumbprint=xs:string>`|Odebere certifikát z kolekce důvěryhodných vystavitelů. Certifikát zadaný `thumbprint` atribut. Tento atribut je vyžadován.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Nakonfiguruje registru název vystavitele. **Důležité:** `type` atribut `<issuerNameRegistry>` element musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` elementu platný.|  
  
## <a name="remarks"></a>Poznámky  
 Windows Identity Foundation (WIF) poskytuje jedna implementace položky <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třída předinstalované, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy. Konfigurace registru název vystavitele udržuje seznam důvěryhodných vystavitelů, který je načten z konfigurace. V seznamu přidruží každý název vystavitele certifikátu X.509, který je třeba ověřit podpis tokeny vyprodukované vystavitele. Seznam důvěryhodných vystavitelů certifikátů je zadaný v `<trustedIssuers>` elementu. Každý prvek v seznamu přidruží název klávesovými vystavitele certifikátu X.509, který je třeba ověřit podpis tokeny vyprodukované této vystavitele. Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódovaný formu kryptografický otisk certifikátu a kolekce se přidají pomocí `<add>` elementu. Můžete vyčistit nebo můžete odebrat ze seznamu vystavitelů (certifikáty) pomocí `<clear>` a `<remove>` elementy.  
  
 `type` Atribut `<issuerNameRegistry>` element musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` elementu platný.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak zadat konfiguraci na základě vystavitele název registru.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
