---
title: <add><scopedCertificates> elementu
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 9756d37527fcf888cad930b24677ae8e6a2c8fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920046"
---
# <a name="add-of-scopedcertificates-element"></a>\<Přidat > \<prvku > scopedCertificates
Přidá certifikát X. 509 do kolekce certifikátů s vymezeným oborem.  
  
 \<system.ServiceModel>  
\<> chování  
oddíl endpointBehaviors  
\<> chování  
\<clientCredentials>  
\<serviceCertificate>  
\<scopedCertificates>  
\<Přidat > element pro \<> scopedCertificates  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|targetUri|Řetezce. Určuje identifikátor URI služby přidružené k certifikátu.|  
|findValue|Řetezce. Hodnota, kterou chcete vyhledat.|  
|x509FindType|Enumeration. Jedno z polí certifikátu, které chcete vyhledat.|  
|storeLocation|Enumeration. Jedno ze dvou umístění úložiště, které chcete vyhledat.|  
|storeName|Enumeration. Jedno ze systémových úložišť, které chcete vyhledat.|  
  
## <a name="findvalue-attribute"></a>findValue – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|String|Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván. Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.|  
  
## <a name="x509findtype-attribute"></a>x509FindType – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|CurrentUser nebo LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek umožňuje klientovi nakonfigurovat certifikát služby tak, aby se použil na základě adresy URL služby, se kterou komunikuje. To je užitečné hlavně ve scénářích vydaných tokenů, kde klient může komunikovat s více službami (koncová služba i zprostředkující služba tokenů zabezpečení). U vazeb, které používají zabezpečení zpráv založených na certifikátech, se tento certifikát používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.  
  
 Pokud vazba vyžaduje certifikát pro službu a v ScopedCertificates se nenajde žádný konkrétní certifikát pro adresu URL služby, použije se výchozí certifikát.  
  
 Další informace najdete v části ["vymezené certifikáty" v tématu Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá do kolekce certifikát X. 509.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
