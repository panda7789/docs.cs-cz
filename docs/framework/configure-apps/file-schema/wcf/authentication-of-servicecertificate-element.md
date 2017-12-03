---
title: '&lt;authentication&gt; elementu &lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb2f567b47f66b378cc6e0a5d5e96441ea65c1ac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a>&lt;authentication&gt; elementu &lt;serviceCertificate&gt;
Určuje nastavení proxy serveru klienta používaná k ověřování certifikáty služby, které jsou získány pomocí vyjednávání SSL/TLS.  
  
 \<systém. ServiceModel >  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials >  
\<serviceCertificate >  
\<ověřování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customCertificateValidatorType|Řetězec. Typ a sestavení, které slouží k ověření vlastního typu.|  
|certificateValidationMode|Určuje jeden ze tří režimů slouží k ověření přihlašovacích údajů. Pokud nastavena na `Custom`, pak musí být uveden také customCertificateValidator. Výchozí hodnota je `ChainTrust`.|  
|revocationMode|Jeden z režimů používá k ověření pro seznamy odvolaných certifikátů (CRL). Výchozí hodnota je `Online`.|  
|trustedStoreLocation|Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá, když je klientovi vyjednal certifikát služby. Ověření se provádí před **důvěryhodné osoby** uložit do umístění zadaného úložiště. Výchozí hodnota je `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Určuje název typu a sestavení a další data použít k vyhledání typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, vlastní.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: NoCheck, Online, do režimu Offline.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: LocalMachine nebo CurrentUser. Výchozí hodnota je CurrentUser. Pokud klientská aplikace běží pod účtem system, certifikát je obvykle v rámci LocalMachine. Pokud klientská aplikace běží pod účtem uživatele, pak certifikát je obvykle v CurrentUser.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Určuje certifikát pro použití při ověřování služby klienta.|  
  
## <a name="remarks"></a>Poznámky  
 `certificateValidationMode` Atribut tohoto elementu konfigurace určuje úroveň důvěryhodnosti používá k ověření certifikátů. Ve výchozím nastavení je úroveň nastavena na `ChainTrust`, která určuje, že každý certifikát, je nutné nalézt v hierarchii certifikátů končí na důvěryhodné certifikační autority v horní části řetězu. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že samoobslužné vydaných certifikátů (peer vztahu důvěryhodnosti) jsou přijaty a také certifikáty, které jsou v důvěryhodné řetězu. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samoobslužné vydaných certifikátů nemusí zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte `ChainTrust` místo hodnoty. Můžete také nastavit hodnotu `Custom` nebo `None`. Použít `Custom` hodnotu, je nutné také nastavit `customCertificateValidator` atribut sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní třídy X509CertificateValidator. Další informace najdete v tématu [postupy: vytvoření služby, který využívá validátor certifikátu vlastní](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 `revocationMode` Atribut určuje, jak certifikáty jsou zaškrtnutá políčka pro odvolání. Výchozí hodnota je `online` což naznačuje, že certifikáty budou automaticky odvolání zkontrolovat. Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se dvě úlohy. Určuje první certifikát služby pro klienta pro použití při komunikaci s koncovými body, jejichž název domény je www.contoso.com přes protokol HTTP. Druhý Určuje odvolání režimu a úložiště umístění, která používají při ověřování.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: vytvoření služby, který využívá validátor vlastní certifikát](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [\<ověřování >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
