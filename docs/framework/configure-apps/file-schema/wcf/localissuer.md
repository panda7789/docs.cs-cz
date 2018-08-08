---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 9118d1462d4790bb457fc8dc2f7c74b6e69de43a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749111"
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
Určuje adresu a vazba místního vystavitele, který se má použít k získání tokenu zabezpečení.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials >  
\<issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Požadovaný řetězec. Určuje identifikátor URI místního vystavitele.|  
|vazba|Volitelný řetězec. Jeden z vazby poskytované systémem. Seznam najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|Volitelný řetězec. Určuje konfiguraci vazby v konfiguračním souboru nalézt.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje informace o identitě pro místního vystavitele.|  
|[\<hlavičky >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekce hlavičky adresy, které jsou požadovány k správně adres místního vystavitele. Můžete použít `add` – klíčové slovo přidat hlavičku do této kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Určuje vlastní token používaný k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Při získávání tokenu vydaných z zabezpečení tokenu služby (STS), klient aplikace musí být nakonfigurována s adresou a vazbou, který bude používat pro komunikaci se služba tokenů zabezpečení. Když <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL služby tokenů zabezpečení, nebo pokud je adresa vystavitele federované vazby http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous nebo `null`, kanálu klienta Windows Communication Foundation (WCF) používá hodnoty zadané ve `address`a `binding` ke komunikaci s služby tokenů zabezpečení získat vydaný token. Další informace týkající se konfigurace místního vystavitele najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad nastavuje `address`, `binding`, a `bindingConfiguration` atributy `localIssuer` elementu.  
  
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
