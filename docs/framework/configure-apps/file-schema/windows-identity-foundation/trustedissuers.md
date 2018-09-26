---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: c390cecc265b27dfa8d9d0a892f5930c982f7054
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206473"
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
Nakonfiguruje seznam důvěryhodných vystavitelů certifikátů používané registru názvu vystavitele založená na konfiguraci (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<system.identityModel>  
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
|`<add thumbprint=xs:string name=xs:string>`|Přidá certifikát do kolekce důvěryhodných vystavitelů. Certifikát se zadaným `thumbprint` atribut. Tento atribut je vyžadován a musí obsahovat ASN.1 kódované podobě kryptografický otisk certifikátu. `name` Atribut je volitelný a je možné zadat popisný název certifikátu.|  
|`<clear>`|Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.|  
|`<remove thumbprint=xs:string>`|Certifikát se odebere z kolekce důvěryhodných vystavitelů. Certifikát se zadaným `thumbprint` atribut. Tento atribut je vyžadován.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Nakonfiguruje registru názvu vystavitele. **Důležité:** `type` atribut `<issuerNameRegistry>` prvek musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` element platný.|  
  
## <a name="remarks"></a>Poznámky  
 Technologie Windows Identity Foundation (WIF) poskytuje jedna implementace položky <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy hned po spuštění <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy. Konfigurace registru názvu vystavitele udržuje seznam důvěryhodných vystavitelů, který je načten z konfigurace. V seznamu přidruží každý název vystavitele, která je potřeba ověřit podpis tokeny vytvářených vystavitele certifikátu X.509. Seznam důvěryhodných vystavitelů certifikátů se zadává v části `<trustedIssuers>` elementu. Každý prvek v seznamu přidruží mnemonická vystavitele certifikátu X.509, který je potřeba k ověření podpisu tokeny vytvářených tohoto vydavatele. Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódovaný formu kryptografický otisk certifikátu a jsou přidány do kolekce pomocí `<add>` elementu. Můžete vymazat nebo odebrání vystavitele (certifikáty) ze seznamu pomocí `<clear>` a `<remove>` elementy.  
  
 `type` Atribut `<issuerNameRegistry>` prvek musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` element platný.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak zadat vystavitele konfigurace na základě názvu registru.  
  
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
