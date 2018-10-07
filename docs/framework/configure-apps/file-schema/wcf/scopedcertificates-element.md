---
title: Element &lt;scopedCertificates&gt;
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 5b9bf4d25e23c8bdc4e3d01c2dfa61d059166117
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838271"
---
# <a name="ltscopedcertificatesgt-element"></a>Element &lt;scopedCertificates&gt;
Představuje kolekci certifikátů X.509 poskytnuty konkrétní službou pro ověřování. Tato kolekce se obvykle používá k určení certifikáty služeb pro služby tokenu zabezpečení v případě federovaných.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<třídu clientCredentials >  
\<serviceCertificate >  
\<scopedCertificates > – Element  
\<Přidat > – element pro \<scopedCertificates >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|Přidá certifikát X.509 do kolekce vymezených certifikátů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|Určuje certifikát používaný při ověřování služby ke klientovi.|  
  
## <a name="remarks"></a>Poznámky  
 Tato kolekce umožňuje klientovi nakonfigurovat certifikáty služby, které budou používat na základě adresy URL služby, se kterým komunikuje. To je zvláště užitečná v vydaný token situacích, kdy může klient komunikovat k více službám (ukončení služby také služby tokenu zabezpečení zprostředkující). U vazeb, které používají zabezpečení na základě certifikátů zpráv tento certifikát se používá k šifrování zpráv ve službě a očekává se využívat službu k podepisování odpovědi klientovi.  
  
 Pokud vazba vyžaduje certifikát pro službu a žádné konkrétní certifikát pro službu, kterou adresy URL se nachází v ScopedCertificates, použije se výchozí certifikát.  
  
 Další informace najdete v části "Obor certifikáty" v [postupy: vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje certifikátu služby pro klienta pro použití při komunikaci s koncovými body, jejichž název domény je `http://www.contoso.com` přes protokol HTTP.  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
