---
title: '&lt;authentication&gt; elementu &lt;clientCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4eb125727d68d1618b32d21612ecfac28eaa5b6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a>&lt;authentication&gt; elementu &lt;clientCertificate&gt;
Určuje chování ověřování pro klientské certifikáty používané služby.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<clientCertificate >  
\<ověřování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customCertificateValidatorType|Volitelný řetězec. Typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`.|  
|certificateValidationMode|Volitelné výčtu. Určuje jeden z režimů slouží k ověření přihlašovacích údajů. Tento atribut je <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu. Pokud nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, pak `customCertificateValidator` musí být uveden také. Výchozí hodnota je <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.|  
|includeWindowsGroups|Volitelné logická hodnota. Určuje, pokud skupiny systému Windows jsou zahrnuty v kontextu zabezpečení. Nastavení tohoto atributu na `true` má dopad na výkon, jako je výsledkem rozšíření úplné skupiny. Nastavte tento atribut `false` Pokud není potřeba vytvořit seznam skupin uživatel patří do.|  
|mapClientCertificateToWindowsAcccount|Logická hodnota. Určuje, zda klient lze mapovat na identitu systému Windows pomocí certifikátu. K tomu musí být povolena služby Active Directory.|  
|revocationMode|Volitelné výčtu. Jeden z režimů používá k ověření pro seznamy odvolaných certifikátů (RCL). Výchozí hodnota je `Online`. Tato hodnota se ignoruje, pokud pomocí zabezpečení přenosu HTTP.|  
|trustedStoreLocation|Volitelné výčtu. Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá, když je klientovi vyjednal certifikát služby. Ověření se provádí před **důvěryhodné osoby** uložit do umístění zadaného úložiště. Výchozí hodnota je `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atribut  
  
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
|Výčet|Jeden z následujících hodnot: NoCheck, Online, do režimu Offline. Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`. Výchozí hodnota je `CurrentUser`. Pokud klientská aplikace běží pod účtem systému pak certifikát je obvykle v části `LocalMachine`. Pokud klientská aplikace běží pod účtem uživatele, pak tento certifikát je obvykle v `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Definuje certifikátu X.509. certifikát použitý k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 `<authentication>` Element odpovídá <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Umožňuje přizpůsobit, jak klienti se ověřují. Můžete nastavit `certificateValidationMode` atribut `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, nebo `Custom`. Ve výchozím nastavení je úroveň nastavena na `ChainTrust`, která určuje, že každý certifikát, je nutné nalézt v hierarchii certifikátů končí na *kořenová autorita* v horní části řetězu. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že samoobslužné vydaných certifikátů (peer vztahu důvěryhodnosti) jsou přijaty a také certifikáty, které jsou v důvěryhodné řetězu. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samoobslužné vydaných certifikátů nemusí zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte `ChainTrust` místo hodnoty.  
  
 Můžete také nastavit hodnotu `Custom`. Pokud nastavíte `Custom` hodnotu, je nutné také nastavit `customCertificateValidatorType` atribut sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy. Další informace najdete v tématu [postupy: vytvoření služby, který využívá validátor certifikátu vlastní](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Příklad  
 Následující kód určuje certifikátu X.509. certifikát a typ vlastní ověření v `<authentication>` elementu.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Postupy: vytvoření služby, který využívá validátor vlastní certifikát](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
