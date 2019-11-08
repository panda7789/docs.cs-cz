---
title: <message> element <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738994"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a>\<> elementu \<ws2007FederationHttpBinding >
Definuje nastavení pro zabezpečení na úrovni zprávy [\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) elementu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zpráva >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
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
|`algorithmSuite`|Volitelné. Nastaví algoritmy šifrování, podpisu a zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny třídou <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Možné hodnoty jsou uvedené v následující tabulce. Výchozí hodnota je Basic256.|  
|`issuedKeyType`|Určuje typ klíče, který se má vystavit. Platné hodnoty jsou následující:<br /><br /> - SymmetricKey<br />– PublicKey<br />- BearerKey<br /><br /> Výchozí hodnota je SymmetricKey. Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.|  
|`issuedTokenType`|Identifikátor URI, který určuje typ tokenu, který se má vystavit. Výchozí hodnota je `null`.|  
|`negotiateServiceCredential`|Hodnota, která určuje, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť. Výchozí hodnota je `true`, což znamená, že se pověření služby vyjednávat.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Pro zabalení klíče použijte šifrování Aes128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.|  
|Basic192|Pro zabalení klíče použijte šifrování Aes192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256|Pro zabalení klíče použijte šifrování AES256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256Rsa15|Použijte AES256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Aes192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDes|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.|  
|Basic128Rsa15|Použijte Aes128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.|  
|Basic128Sha256|Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic192Sha256|Pro zabalení klíče použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic256Sha256|Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|TripleDesSha256|Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic128Sha256Rsa15|Použijte Aes128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](claimtyperequirements-element.md)|Určuje kolekci typů deklarací pro tuto vazbu. Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.|  
|[Vystavitel \<](issuer.md)|Určuje koncový bod, který vydá token zabezpečení. Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.|  
|[\<issuerMetadata >](issuermetadata.md)|Určuje adresu koncového bodu vystavitele.|  
|[\<tokenRequestParameters >](tokenrequestparameters.md)|Kolekce parametrů požadavku tokenu Každý parametr je XML element.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-element-of-ws2007federationhttpbinding.md)|Definuje nastavení zabezpečení pro vazbu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
