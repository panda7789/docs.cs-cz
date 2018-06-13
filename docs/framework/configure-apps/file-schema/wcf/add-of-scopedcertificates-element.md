---
title: '&lt;add&gt; elementu &lt;scopedCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 0eb2f116fc0a2c7d59b90cea71150c7b46ee39fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746641"
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a>&lt;add&gt; elementu &lt;scopedCertificates&gt;
Přidá do kolekce vymezená certifikátů certifikát X.509.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials >  
\<serviceCertificate >  
\<scopedCertificates >  
\<Přidat > elementu pro \<scopedCertificates >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|targetUri|Řetězec. Určuje identifikátor URI služby přidruženého k certifikátu.|  
|findValue|Řetězec. Hodnota, kterou chcete vyhledat.|  
|X509FindType|Výčet. Jeden z pole certifikátu pro vyhledávání.|  
|storeLocation|Výčet. Jednu ze dvou ukládat prohledávaných umístění.|  
|storeName|Výčet. Jeden z úložiště systému pro vyhledávání.|  
  
## <a name="findvalue-attribute"></a>findValue atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Hodnota závisí na poli (zadané v atributu X509FindType) být vyhledán. Například pokud hledání kryptografický otisk, hodnota musí být řetězec o délce hexadecimální číslice.|  
  
## <a name="x509findtype-attribute"></a>Atribut x509FindType  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|CurrentUser nebo LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Hodnoty patří: CertificateAuthority adresáře, AuthRoot, zakázané, Moje, Root, TrustedPeople a TrustedPublisher.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<scopedCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Představuje kolekci certifikáty X.509, které jsou součástí konkrétní služby (obor) pro ověřování.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element umožňuje klientovi konfigurace certifikátu pro použití služby založené na adresu URL služby, kterým komunikuje. To je zvlášť užitečné v vydaných tokenů scénáře, kde může klient komunikovat na více služeb (na koncové služby a také služeb tokenu zprostředkující zabezpečení). U vazeb, které používají zabezpečení zpráv pomocí certifikátů tento certifikát se používá k šifrování zpráv do služby a očekává se použije pro podepisování odpovědi klientovi službou.  
  
 Pokud vazba vyžaduje certifikát pro službu a žádný konkrétní certifikát pro službu, kterou adresu URL se nachází v ScopedCertificates, použije se výchozí certifikát.  
  
 Další informace najdete v části "Obor certifikáty" z [postupy: vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá certifikát X.509 kolekce.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [Postupy: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
