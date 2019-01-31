---
title: <message> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 66e854ca9dd33b608b93dae08376caaf590bd97f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277131"
---
# <a name="message-of-nethttpbinding"></a>\<Zpráva > z \<netHttpBinding >
Definuje nastavení pro zabezpečení na úrovni zprávy z [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<netHttpBinding>  
\<Vytvoření vazby >  
\<security>  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Nastaví zprávu algoritmy šifrování a klíč zalamování řádků. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, která určuje algoritmy a velikosti klíče. Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Určuje typ přihlašovacích údajů pro použití při ověřování klientů pomocí zabezpečení na základě zpráv. Výchozí hodnota je `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType Attribute  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|UserName|-Vyžaduje ověření klienta k serveru pomocí přihlašovacích údajů uživatelského jména. Tyto přihlašovací údaje musí být zadaná pomocí <`clientCredentials`> element.<br />-WCF nepodporuje odesílání hodnotou hash hesla nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro zabezpečení zpráv. Proto WCF vynutí, že přenos zabezpečit při použití pověření uživatelských jmen. Pro `basicHttpBinding`, to vyžaduje nastavení kanálu SSL.|  
|Certifikát|Vyžaduje se k serveru, používá certifikát ověření klienta. Pověření klienta nejsou v tomto případě musí být zadaná pomocí <`clientCredentials`> a <`clientCertificate`>. Kromě toho-když používají režim zabezpečených zpráv, klient musí být zřízená s certifikátem služby. Přihlašovací údaje služby v tomto případě musí být zadaná pomocí <xref:System.ServiceModel.Description.ClientCredentials> třídy nebo `ClientCredentials` prvek chování a zadáním služby certifikátu pomocí \<serviceCertificate > elementu serviceCredentials.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|<`security`> elementu <`netHttpBinding`>|Definuje možnosti zabezpečení pro <`netHttpBinding`> Element.|  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak implementovat aplikaci, která používá zabezpečení tříd basicHttpBinding a zprávy. V následujícím příkladu konfigurace pro službu, definice koncového bodu, určuje, basicHttpBinding a odkazuje na konfiguraci vazby s názvem `Binding1`. Nastavení certifikátu, který službu používá ke svému ověření ke klientovi `behaviors` souboru konfigurace v rámci `serviceCredentials` elementu. Režim ověřování, který se vztahuje na certifikát, který klient použije ke svému ověření ke službě je také nastavena `behaviors` části `clientCertificate` elementu.  
  
 Stejné informace pro vazby a zabezpečení jsou uvedeny v souboru konfigurace klienta.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
                 is in the user's Trusted People store, then it will be trusted without performing a
                 validation of the certificate's issuer chain. This setting is used here for convenience so that the
                 sample can be run without having to have certificates issued by a certification authority (CA).
                 This setting is less secure than the default, ChainTrust. The security implications of this
                 setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
