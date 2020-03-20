---
title: <add><claimTypeRequirements> prvku
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153097"
---
# <a name="add-of-claimtyperequirements-element"></a>\<přidat> \<prvku claimTypeRequirements>
Určuje typy požadovaných a volitelných deklarací, u kterých se má zobrazit ve federovaném pověření. Služby například uvádějí požadavky na příchozí pověření, která musí mít určitou sadu typů deklarací.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vázání>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<závazné>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bezpečnostní>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zpráv**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|claimType|Identifikátor URI, který definuje typ deklarace. Chcete-li například zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným úvěrovým limitem. Typ deklarace by byl identifikátor URI platební karty.|  
|isOptional|Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci. Nastavte tento `false` atribut, pokud se jedná o požadovanou deklaraci.<br /><br /> Tento atribut můžete použít, když služba požádá o některé informace, ale nevyžaduje je. Pokud například požadujete, aby uživatel zadá své jméno, příjmení a adresu, ale rozhodnete, že telefonní číslo je volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|Určuje kolekci požadovaných typů deklarací. Každý prvek je <xref:System.ServiceModel.Configuration.ClaimTypeElement>typu .<br /><br /> Ve federovaném scénáři služby uvedou požadavky na příchozí pověření. Například příchozí pověření musí mít určitou sadu typů deklarací. Každý prvek v této kolekci určuje typy povinných a volitelných deklarací, které se mají zobrazit ve federovaném pověření.|  
  
## <a name="remarks"></a>Poznámky  
 Ve federovaném scénáři služby uvedou požadavky na příchozí pověření. Například příchozí pověření musí mít určitou sadu typů deklarací. Tento požadavek se projevuje v zásadách zabezpečení. Když klient požaduje pověření z federované služby (například CardSpace), vloží požadavky do požadavku na token (RequestSecurityToken) tak, aby federovaná služba může vydat pověření, která splňují požadavky odpovídajícím způsobem.  
  
## <a name="example"></a>Příklad  
 Následující konfigurace přidá dva požadavky na typ deklarace deklarace zabezpečení do vazby zabezpečení.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
