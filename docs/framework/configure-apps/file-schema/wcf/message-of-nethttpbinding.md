---
title: "&lt;message&gt; – &lt;netHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af7dcd39dbc7ecca899cda0779c98efa1493c60f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagegt-of-ltnethttpbindinggt"></a>&lt;message&gt; – &lt;netHttpBinding&gt;
Definuje nastavení pro zprávy úroveň zabezpečení [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<systém. ServiceModel >  
\<vazby >  
\<netHttpBinding >  
\<Vazba >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Nastaví zprávu algoritmy šifrování a klíč wrap. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, která určuje algoritmy a velikosti klíče. Tyto algoritmy mapovat platformám zadaným v specifikace jazyka zásady zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Určuje typ pověření, který se má použít při ověřování klienta pomocí zabezpečení na základě zpráv. Výchozí hodnota je `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|UserName|-Vyžaduje ověření klienta k serveru pomocí pověření uživatelského jména. Toto pověření musí být zadán pomocí <`clientCredentials`> elementu.<br />-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nepodporuje odesílání hodnotu hash hesla nebo odvozování klíče pomocí hesla a použití tyto klíče pro zabezpečení zpráv. Proto [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] vynucuje, aby přenos být zabezpečeny při použití pověření uživatelského jména. Pro `basicHttpBinding`, to vyžaduje nastavení připojení SSL.|  
|certifikát|Vyžaduje, aby na server používá certifikát ověření klienta. V takovém případě musí být zadán pomocí pověření klienta <`clientCredentials`> a <`clientCertificate`>. Kromě toho pokud používáte režim zabezpečení zprávy, klient musí být opatřena certifikát služby. Přihlašovací údaje služby v takovém případě musí být zadán pomocí <xref:System.ServiceModel.Description.ClientCredentials> – třída nebo `ClientCredentials` element chování a zadání službu certifikátu pomocí \<serviceCertificate > elementu – ServiceCredentials.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|<`security`> elementu <`netHttpBinding`>|Definuje možnosti zabezpečení pro <`netHttpBinding`> elementu.|  
  
## <a name="example"></a>Příklad  
 Tento příklad znázorňuje implementaci aplikace, která používá zabezpečení basicHttpBinding a zprávu. V následujícím příkladu konfigurace pro službu definici koncového bodu určuje basicHttpBinding a odkazuje na vazbu konfigurace s názvem `Binding1`. Certifikát, který služba používá k vlastnímu ověření klienta je nastavena v `behaviors` oddíl konfiguračního souboru pod `serviceCredentials` elementu. Režim ověřování, který se vztahuje na certifikát, který klient použije k vlastnímu ověření služby je také nastavit `behaviors` oddílu pod `clientCertificate` elementu.  
  
 Stejné podrobnosti vazby a zabezpečení jsou zadané v konfiguračním souboru klienta.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
