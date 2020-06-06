---
title: <message> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 748a734af8cf6767ce47cfffce9aec3ef627cb44
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736738"
---
# <a name="message-of-basichttpbinding"></a>\<message> z \<basicHttpBinding>
Definuje nastavení pro zabezpečení na úrovni zprávy [\<basicHttpBinding>](basichttpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> , který určuje algoritmy a velikosti klíčů. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení založeného na zprávách. Výchozí formát je `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|UserName|– Vyžaduje, aby byl klient ověřený pro server s přihlašovacími údaji uživatele. Toto pověření je nutné zadat pomocí [\<clientCredentials>](clientcredentials.md) .<br />-WCF nepodporuje odeslání výtahu hesla ani odvození klíčů pomocí hesel a použití takových klíčů pro zabezpečení zpráv. Proto WCF vynutilo zabezpečení přenosu při použití přihlašovacích údajů uživatelského jména. V případě nástroje `basicHttpBinding` to vyžaduje vytvoření kanálu SSL.|  
|Certifikát|Vyžaduje, aby byl klient ověřený na serveru pomocí certifikátu. Přihlašovací údaje klienta v tomto případě je nutné zadat pomocí [\<clientCredentials>](clientcredentials.md) a [\<clientCertificate>](clientcertificate-of-servicecredentials.md) . Kromě toho je nutné při použití režimu zabezpečení zpráv zřídit klienta s certifikátem služby. Pověření služby v tomto případě je nutné zadat pomocí <xref:System.ServiceModel.Description.ClientCredentials> elementu Class nebo `ClientCredentials` Behavior a zadáním certifikátu služby pomocí [\<serviceCertificate>](servicecertificate-of-servicecredentials.md) .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|Definuje možnosti zabezpečení pro [\<basicHttpBinding>](basichttpbinding.md) .|  
  
## <a name="example"></a>Příklad  
 Tato ukázka předvádí, jak implementovat aplikaci, která používá zabezpečení basicHttpBinding a Message. V následujícím příkladu konfigurace služby určuje definice koncového bodu basicHttpBinding a odkazuje na konfiguraci vazby s názvem `Binding1` . Certifikát, který služba používá ke vzájemnému ověření pro klienta, je nastaven v `behaviors` části konfiguračního souboru pod `serviceCredentials` prvkem. Režim ověřování, který se vztahuje na certifikát, který klient používá k ověření ve službě, je také nastaven v `behaviors` části pod `clientCertificate` prvkem.  
  
 V konfiguračním souboru klienta jsou zadány stejné podrobnosti o vazbě a zabezpečení.  
  
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
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
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
      <binding name="Binding1">
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
