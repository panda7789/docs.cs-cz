---
title: Element &lt;message&gt; – &lt;ws2007FederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 6954a7b9646b35ee03aab311deae026a711be9cd
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847543"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a>Element &lt;message&gt; – &lt;ws2007FederationHttpBinding&gt;
Definuje nastavení pro zprávy úroveň zabezpečení pro [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.  
  
 \<system.ServiceModel>  
\<vazby >  
\<ws2007FederationHttpBinding>  
\<Vytvoření vazby >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007FederationBinding>  
   <binding >  
      <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
            <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
            </issuer>  
            <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
            </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
         </message>  
      </security>  
   </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`algorithmSuite`|Volitelné. Nastaví šifrování zpráv, podpisu a key-wrap algoritmy. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Najdete v následující tabulce možných hodnot. Výchozí hodnota je Basic256.|  
|`issuedKeyType`|Určuje typ klíče vystavování. Platné hodnoty patří:<br /><br /> -SymmetricKey<br />-PublicKey<br />-BearerKey<br /><br /> Výchozí hodnota je SymmetricKey. Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|`issuedTokenType`|Identifikátor URI, který určuje typ tokenu je nutno spustit. Výchozí hodnota je `null`.|  
|`negotiateServiceCredential`|Hodnota, která určuje, zda by měl být vyměňují v rámci vyjednávání přihlašovacích údajů služby, nebo je k dispozici mimo pásmo. Výchozí hodnota je `true`, což znamená, že se vyjedná přihlašovacích údajů pro služby.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Zabalení klíče použijte Aes128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.|  
|Basic192|Použijte šifrování Aes192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použití Aes192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Použití Aes128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Použití Aes128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Určuje kolekci typů deklarací identity pro tuto vazbu. Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|[\<Issuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Určuje koncový bod, který vydá token zabezpečení. Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Určuje adresu koncového bodu vystavitele.|  
|[\<tokenRequestParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|Kolekce parametrů žádosti o token. Každý parametr je platný element XML.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|Definuje nastavení zabezpečení pro vazbu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
