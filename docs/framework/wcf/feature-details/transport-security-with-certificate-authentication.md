---
title: Zabezpečení přenosu s ověřováním certifikátu
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: b31694e41e6e6568feb0cb32364b291657269488
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618552"
---
# <a name="transport-security-with-certificate-authentication"></a>Zabezpečení přenosu s ověřováním certifikátu
Toto téma popisuje, při použití zabezpečení přenosu pomocí certifikátů X.509 pro ověření klienta a serveru. Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikátů X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Certifikáty musí být vystavené certifikační autority, což se často stává třetích stran vystavitelů certifikátů. V doméně systému Windows Server Active Directory Certificate Services slouží k vydávání certifikátů pro klientské počítače v doméně. Další informace najdete v části [Windows 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). V tomto scénáři je služba hostována v části Internetová informační služba (), který je nakonfigurovaný s vrstvy SSL (Secure Sockets). Služba je nakonfigurována s certifikátem protokolu SSL (X.509) a umožňuje klientům ověřit identitu serveru. Klient je také nakonfigurováno s certifikát X.509, který umožňuje službě k ověření identity klienta. Klient musí důvěřovat certifikátu serveru a server musí důvěřovat certifikátu klienta. Skutečné mechanismu jak klienta a služby ověří identitu uživatele toho druhého je nad rámec tohoto tématu. Další informace najdete v části [digitální podpis v encyklopedii Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).  
  
 Tento scénář implementuje vzoru zprávy požadavku/odpovědi, jak je znázorněno v následujícím diagramu.  
  
 ![Vyžádání bezpečného přenosu pomocí certifikátů](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Další informace o pomocí certifikátu služby najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [jak: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). Následující tabulka popisuje vlastnosti různé scénáře.  
  
|Vlastnost|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Přenos|  
|Interoperabilita|S existující klienty webové služby a služby.|  
|Ověření (Server)<br /><br /> Ověření (klient)|Ano (použití certifikátu SSL)<br /><br /> Ano (pomocí certifikátu X.509)|  
|Integrita dat|Ano|  
|Zajištění anonymity dat.|Ano|  
|Přenos|HTTPS|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Konfigurace služby  
 Protože služba v tomto scénáři je hostována v rámci služby IIS, je nakonfigurován se souborem web.config. Následující soubor web.config ukazuje postup při konfiguraci <xref:System.ServiceModel.WSHttpBinding> použít k zabezpečení přenosů a přihlašovací údaje klienta X.509.  
  
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
 Klientovi lze nastavit v kódu nebo v souboru app.config. Následující příklad ukazuje, jak nakonfigurovat klienta v kódu.  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
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
  
## <a name="see-also"></a>Viz také:
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
