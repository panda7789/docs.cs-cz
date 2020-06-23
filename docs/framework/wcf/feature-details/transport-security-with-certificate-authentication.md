---
title: Zabezpečení přenosu s ověřováním certifikátu
description: Přečtěte si, jak WFC používá certifikáty pro ověřování serverů a klientů při použití zabezpečení přenosu.
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 3da1202a5ad3b953470b50dd5924b2ab45f301eb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244775"
---
# <a name="transport-security-with-certificate-authentication"></a>Zabezpečení přenosu s ověřováním certifikátu

Tento článek popisuje použití certifikátů X. 509 pro ověřování serverů a klientů při použití zabezpečení přenosu. Další informace o certifikátech X. 509 najdete v tématu [certifikáty s veřejným klíčem x. 509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Certifikáty musí vystavit certifikační autorita, což je často Vystavitel certifikátů třetích stran. V doméně systému Windows Server lze použít službu AD CS (Active Directory Certificate Services) k vystavování certifikátů klientským počítačům v doméně. V tomto scénáři je služba hostovaná v rámci služby Internetová informační služba (IIS), která je nakonfigurovaná s SSL (Secure Sockets Layer) (SSL). Služba je nakonfigurována pomocí certifikátu SSL (X. 509), který klientům umožňuje ověřit identitu serveru. Klient je také nakonfigurován s certifikátem X. 509, který umožňuje službě ověřit identitu klienta. Certifikát serveru musí být důvěryhodný pro klienta a certifikát klienta musí být důvěryhodný serverem. Skutečný způsob, jakým služba a klient ověřuje identitu druhé strany, je nad rámec tohoto článku. Další informace najdete v tématu [digitální podpis](https://en.wikipedia.org/wiki/Digital_signature) v Wikipedii.
  
 Tento scénář implementuje vzor zprávy žádosti nebo odpovědi, jak je znázorněno v následujícím diagramu.  
  
 ![Zabezpečený přenos pomocí certifikátů](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")  
  
 Další informace o používání certifikátu se službou najdete v tématu [práce s certifikáty](working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md). V následující tabulce jsou popsány různé charakteristiky scénáře.  
  
|Charakteristika|Description|  
|--------------------|-----------------|  
|Režim zabezpečení|Přenos|  
|Interoperabilita|Se stávajícími klienty a službami webové služby.|  
|Ověřování (Server)<br /><br /> Ověřování (klient)|Ano (pomocí certifikátu SSL)<br /><br /> Ano (pomocí certifikátu X. 509)|  
|Integrita dat|Ano|  
|Důvěrnost dat|Ano|  
|Přenos|HTTPS|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Konfigurace služby  
 Vzhledem k tomu, že je služba v tomto scénáři hostovaná v rámci služby IIS, je nakonfigurovaná s web.config souborem. Následující web.config ukazuje, jak nakonfigurovat <xref:System.ServiceModel.WSHttpBinding> pro použití zabezpečení přenosu a pověření klienta X. 509.  
  
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
  
 Případně můžete klienta nakonfigurovat v souboru App.config, jak je znázorněno v následujícím příkladu:  
  
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

- [Přehled zabezpečení](security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
