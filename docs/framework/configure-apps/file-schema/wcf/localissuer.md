---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: cb5afb0e73ad0a07ea43f06915f4e477d7f8f985
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841550"
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
Určuje adresu a vazbu lokálního vystavitele, který se má použít k získání tokenu zabezpečení.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<třídu clientCredentials >  
\<třídy issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Povinný řetězec. Určuje identifikátor URI místního vystavitele.|  
|vazba|Volitelný řetězec. Jedna z vazeb poskytovaných systémem. Seznam najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|Volitelný řetězec. Určuje konfiguraci vazby nacházející se v konfiguračním souboru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje informace o identitě pro lokálního vystavitele.|  
|[\<záhlaví >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekce záhlaví adres nutných ke správnému adresování lokálního vystavitele. Můžete použít `add` – klíčové slovo do této kolekce přidat hlavičku.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<třídy issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Určuje vlastní token pro ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Při získávání vydaný token z tokenu služby zabezpečení (STS), klientská aplikace musí být nakonfigurované s adresou a vazba k použití pro komunikaci pomocí služby STS. Když <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL pro službu tokenů zabezpečení, nebo když je adresa vystavitele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null`, kanálu klienta Windows Communication Foundation (WCF) používá hodnoty zadané ve `address`a `binding` ke komunikaci s služby STS pro získání vydaný token. Další informace týkající se konfigurace místního vystavitele najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví `address`, `binding`, a `bindingConfiguration` atributy `localIssuer` elementu.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Postupy: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
