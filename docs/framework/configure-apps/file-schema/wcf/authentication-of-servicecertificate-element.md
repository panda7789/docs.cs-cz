---
title: <authentication><serviceCertificate> elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: d770ba1f9a0a18c927b3a4bf6d4141286e3a380c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919985"
---
# <a name="authentication-of-servicecertificate-element"></a>\<ověřování > \<elementu serviceCertificate >
Určuje nastavení používané klientským proxy serverem k ověřování certifikátů služby, které jsou získány pomocí vyjednávání protokolu SSL/TLS.  
  
 \<system.ServiceModel>  
\<> chování  
oddíl endpointBehaviors  
\<> chování  
\<clientCredentials>  
\<serviceCertificate>  
\<> ověřování  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customCertificateValidatorType|Řetezce. Typ a sestavení, které slouží k ověření vlastního typu.|  
|certificateValidationMode|Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů. Pokud je nastaveno `Custom`na, je nutné zadat také CustomCertificateValidator. Výchozí hodnota je `ChainTrust`.|  
|revocationMode|Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL). Výchozí hodnota je `Online`.|  
|trustedStoreLocation|Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser` Tato hodnota se používá, když je certifikát služby vyjednán klientovi. Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště. Výchozí hodnota je `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|String|Určuje název typu a sestavení a další data, která se používají k vyhledání typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: Nekontrolujte, online, offline.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: LocalMachine nebo CurrentUser. Výchozí hodnota je CurrentUser. Pokud klientská aplikace běží pod účtem systému, pak je certifikát obvykle pod LocalMachine. Pokud klientská aplikace běží pod uživatelským účtem, je certifikát většinou v CurrentUser.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Určuje certifikát, který se má použít při ověřování služby pro klienta.|  
  
## <a name="remarks"></a>Poznámky  
 `certificateValidationMode` Atribut tohoto elementu konfigurace určuje úroveň důvěryhodnosti použitou k ověřování certifikátů. Ve výchozím nastavení je úroveň nastavena na `ChainTrust`hodnotu, která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících důvěryhodnou certifikační autoritou v horní části řetězce. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu na `PeerOrChainTrust`, což znamená, že jsou přijímány certifikáty vystavené svým držitelem (vztah důvěryhodnosti peering) i certifikáty, které jsou v důvěryhodném řetězci. Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou. Při nasazování klienta použijte `ChainTrust` místo něj hodnotu. Můžete také nastavit hodnotu na `Custom` nebo. `None` Chcete-li `Custom` použít hodnotu, je nutné také `customCertificateValidator` nastavit atribut na sestavení a typ použitý k ověření certifikátu. Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní třídy X509CertificateValidator. Další informace najdete v tématu [jak: Vytvořte službu, která využívá vlastní validátor](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certifikátů.  
  
 `revocationMode` Atribut určuje, jak se kontrolují certifikáty pro odvolání. Ve výchozím nastavení `online` to znamená, že se certifikáty budou kontrolovat automaticky pro odvolání. Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad provádí dvě úlohy. Nejprve Určuje certifikát služby, který má klient použít při komunikaci s koncovými body, jejichž název domény `www.contoso.com` je přes protokol HTTP. Za druhé určuje režim odvolání a umístění úložiště použité při ověřování.  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<> ověřování](authentication-of-clientcertificate-element.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
