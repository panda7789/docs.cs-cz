---
title: <authentication> z <clientCertificate> – Element
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: e232cde8f6838de734e37aeee3f52cd7f7e7502d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221199"
---
# <a name="authentication-of-clientcertificate-element"></a>\<ověřování > z \<clientCertificate > – Element
Určuje chování ověřování pro klientské certifikáty používané službou.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<clientCertificate>  
\<ověřování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customCertificateValidatorType|Volitelný řetězec. Typ a sestavení používané pro ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.|  
|certificateValidationMode|Volitelný výčet. Určuje jeden z režimů pro ověření pověření. Tento atribut je <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu. Pokud hodnotu <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, o `customCertificateValidator` musí být rovněž dodán. Výchozí hodnota je <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.|  
|includeWindowsGroups|Nepovinný datový typ Boolean. Určuje, pokud jsou skupiny Windows zahrnuty v kontextu zabezpečení. Nastavení tohoto atributu na `true` má dopad na výkon, protože výsledkem rozšíření celé skupiny. Tento atribut nastavte na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří.|  
|mapClientCertificateToWindowsAcccount|Datový typ Boolean. Určuje, zda klient je možné mapovat na Windows identity pomocí certifikátu. K tomu musí být povolené služby Active Directory.|  
|revocationMode|Volitelný výčet. Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (RCL). Výchozí hodnota je `Online`. Tato hodnota se ignoruje při použití zabezpečení přenosu HTTP.|  
|trustedStoreLocation|Volitelný výčet. Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá při certifikát služby se vyjedná do klienta. Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště. Výchozí hodnota je `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType Attribute  
  
|Value|Popis|  
|-----------|-----------------|  
|String|Určuje název typu a sestavení a další data použít k vyhledání typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: NONE, PeerTrust, ChainTrust, PeerOrChainTrust, vlastní.<br /><br /> Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: NoCheck, Online, Offline. Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`. Výchozí hodnota je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`. Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Určuje certifikát X.509 použitý k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 `<authentication>` Odpovídá elementu <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Umožňuje přizpůsobit, jak se budou ověřovat klienti. Můžete nastavit `certificateValidationMode` atribut `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, nebo `Custom`. Ve výchozím nastavení, úroveň je nastavena `ChainTrust`, která určuje, že každý certifikát musí být nalezena v hierarchii certifikátů končí na *kořenová autorita* na začátku řetězce. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že jsou přijímány samostatně vydané certifikáty (peer vztahu důvěryhodnosti) a také certifikáty, které jsou v důvěryhodným řetězem. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samostatně vydané certifikáty nemusí být zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte `ChainTrust` místo hodnoty.  
  
 Můžete také nastavit hodnotu `Custom`. Pokud je nastavena na `Custom` hodnotu, je nutné nastavit také `customCertificateValidatorType` atribut na sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy. Další informace najdete v tématu [jak: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Příklad  
 Následující kód Určuje certifikát X.509 a zadejte vlastní ověření v `<authentication>` elementu.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
