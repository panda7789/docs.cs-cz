---
title: Zabezpečení přenosu s ověřováním certifikátu
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: ad2f0922afbd94e1699b383cf2fc9762771b637d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184320"
---
# <a name="transport-security-with-certificate-authentication"></a>Zabezpečení přenosu s ověřováním certifikátu

Tento článek popisuje použití certifikátů X.509 pro ověřování serveru a klienta při použití zabezpečení přenosu. Další informace o certifikátech X.509 naleznete v [tématu Certifikáty veřejného klíče X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Certifikáty musí být vydány certifikačníautoritou, která je často vystavitelem certifikátů třetí stranou. V doméně systému Windows Server lze službu AD Certificate Services použít k vydávání certifikátů klientským počítačům v doméně. V tomto scénáři je služba hostována v rámci Internetové informační služby (IIS), která je nakonfigurována s vrstvou SSL (Secure Sockets L). Služba je konfigurována s certifikátem SSL (X.509), který klientům umožňuje ověřit identitu serveru. Klient je také nakonfigurován s certifikátem X.509, který umožňuje službě ověřit identitu klienta. Certifikát serveru musí být klientem důvěryhodný a certifikát klienta musí být důvěryhodný serverem. Skutečná mechanika, jak služba a klient ověřuje navzájem identity je nad rámec tohoto článku. Další informace naleznete [v tématu Digitální podpis](https://en.wikipedia.org/wiki/Digital_signature) na Wikipedii.
  
 Tento scénář implementuje vzor zprávy požadavek/odpověď, jak je znázorněno v následujícím diagramu.  
  
 ![Zabezpečený přenos pomocí certifikátů](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0ea872a291c")  
  
 Další informace o použití certifikátu se službou naleznete v [tématu Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [Postup: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). Následující tabulka popisuje různé charakteristiky scénáře.  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Přenos|  
|Vzájemná funkční spolupráce|S existujícími klienty a službami webových služeb.|  
|Ověřování (server)<br /><br /> Ověřování (klient)|Ano (pomocí certifikátu SSL)<br /><br /> Ano (pomocí certifikátu X.509)|  
|Integrita dat|Ano|  
|Důvěrnost údajů|Ano|  
|Přenos|HTTPS|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Konfigurace služby  
 Vzhledem k tomu, že služba v tomto scénáři je hostována ve službě IIS, je nakonfigurována se souborem web.config. Následující web.config ukazuje, jak <xref:System.ServiceModel.WSHttpBinding> nakonfigurovat zabezpečení přenosu a pověření klienta X.509.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a>Konfigurace klienta  
 Klienta lze nakonfigurovat v kódu nebo v souboru app.config. Následující příklad ukazuje, jak nakonfigurovat klienta v kódu.  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 Případně můžete nakonfigurovat klienta v souboru App.config, jak je znázorněno v následujícím příkladu:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
