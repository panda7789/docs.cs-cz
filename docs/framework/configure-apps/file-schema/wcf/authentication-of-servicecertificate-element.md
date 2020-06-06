---
title: <authentication><serviceCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398227"
---
# <a name="authentication-of-servicecertificate-element"></a>\<authentication>\<serviceCertificate>elementu
Určuje nastavení používané klientským proxy serverem k ověřování certifikátů služby, které jsou získány pomocí vyjednávání protokolu SSL/TLS.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
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
|customCertificateValidatorType|Řetězec. Typ a sestavení, které slouží k ověření vlastního typu.|  
|certificateValidationMode|Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů. Pokud je nastaveno na `Custom` , je nutné zadat také CustomCertificateValidator. Výchozí formát je `ChainTrust`.|  
|revocationMode|Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL). Výchozí formát je `Online`.|  
|trustedStoreLocation|Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` . Tato hodnota se používá, když je certifikát služby vyjednán klientovi. Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště. Výchozí formát je `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Řetězec|Určuje název typu a sestavení a další data, která se používají k vyhledání typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: nekontrolujte, online, offline.<br /><br /> Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Jedna z následujících hodnot: LocalMachine nebo CurrentUser. Výchozí hodnota je CurrentUser. Pokud klientská aplikace běží pod účtem systému, pak je certifikát obvykle pod LocalMachine. Pokud klientská aplikace běží pod uživatelským účtem, je certifikát většinou v CurrentUser.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Určuje certifikát, který se má použít při ověřování služby pro klienta.|  
  
## <a name="remarks"></a>Poznámky  
 `certificateValidationMode`Atribut tohoto elementu konfigurace určuje úroveň důvěryhodnosti použitou k ověřování certifikátů. Ve výchozím nastavení je úroveň nastavena na hodnotu `ChainTrust` , která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících důvěryhodnou certifikační autoritou v horní části řetězce. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu na `PeerOrChainTrust` , což znamená, že jsou přijímány certifikáty vystavené svým držitelem (vztah důvěryhodnosti peering) i certifikáty, které jsou v důvěryhodném řetězci. Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou. Při nasazování klienta použijte `ChainTrust` místo něj hodnotu. Můžete také nastavit hodnotu na `Custom` nebo `None` . Chcete-li použít `Custom` hodnotu, je nutné také nastavit `customCertificateValidator` atribut na sestavení a typ použitý k ověření certifikátu. Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní třídy X509CertificateValidator. Další informace najdete v tématu [Postup: vytvoření služby, která využívá vlastní validátor certifikátů](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 `revocationMode`Atribut určuje, jak se kontrolují certifikáty pro odvolání. Ve výchozím nastavení `online` to znamená, že se certifikáty budou kontrolovat automaticky pro odvolání. Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad provádí dvě úlohy. Nejprve Určuje certifikát služby, který má klient použít při komunikaci s koncovými body, jejichž název domény je `www.contoso.com` přes protokol HTTP. Za druhé určuje režim odvolání a umístění úložiště použité při ověřování.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
