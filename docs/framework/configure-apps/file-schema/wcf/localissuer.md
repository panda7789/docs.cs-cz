---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931741"
---
# <a name="localissuer"></a>\<localIssuer>
Určuje adresu a vazbu místního vystavitele, který se má použít k získání tokenu zabezpečení.  
  
 \<system.ServiceModel>  
\<> chování  
oddíl endpointBehaviors  
\<> chování  
\<clientCredentials>  
\<Třídy IssuedToken >  
\<localIssuer>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Povinný řetězec. Určuje identifikátor URI místního vystavitele.|  
|vazba|Volitelný řetězec. Jedna z vazeb poskytovaných systémem. Seznam najdete v tématu [vazby poskytované systémem](../../../wcf/system-provided-bindings.md).|  
|bindingConfiguration|Volitelný řetězec. Určuje konfiguraci vazby nalezenou v konfiguračním souboru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Určuje informace o identitě místního vystavitele.|  
|[\<headers>](headers-element.md)|Kolekce hlaviček adres, které jsou požadovány pro správné adresování místního vystavitele. K přidání záhlaví do `add` této kolekce můžete použít klíčové slovo.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|Určuje vlastní token, který slouží k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Při získávání vystaveného tokenu ze služby tokenu zabezpečení (STS) musí být klientská aplikace nakonfigurovaná s adresou a vazbou, která se má použít ke komunikaci se službou STS. Pokud neposkytuje adresu URL pro službu tokenu zabezpečení, nebo pokud je `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` adresa vystavitele federované vazby nebo `null`, kanál Windows Communication Foundation (WCF) klienta používá hodnoty určené parametrem <xref:System.ServiceModel.WSFederationHttpBinding> `address` a`binding` ke komunikaci se službou STS pro získání vydaného tokenu. Další informace o konfiguraci místního vystavitele najdete v [tématu Postup: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou nastaveny `address`atributy `binding` `bindingConfiguration` , a elementu. `localIssuer`  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Postupy: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
