---
title: Zabezpečení přenosu s ověřováním certifikátu
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a4f29d9ac34437431a95a247ef1e7aa5c9084c36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499073"
---
# <a name="transport-security-with-certificate-authentication"></a>Zabezpečení přenosu s ověřováním certifikátu
Toto téma popisuje, když pomocí zabezpečení přenosu pomocí certifikátů X.509 pro server a ověření klienta. Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikáty X.509](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx). Certifikáty musí být vydaný certifikační autoritou, což se často stává třetích stran vystavitelů certifikátů. V doméně systému Windows Server Active Directory Certificate Services slouží k vydávání certifikátů pro klientské počítače v doméně. Další informace najdete v části [certifikační služby systému Windows 2008 R2](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). V tomto scénáři je služba hostována v části Internetové informační služby (IIS), který je konfigurován s vrstvy SSL (Secure Sockets). Služba je nakonfigurována pomocí certifikátu protokolu SSL (X.509), aby se klienti k ověření identity serveru. Klient je také nakonfigurovaný se certifikát X.509, který umožňuje službě k ověření identity klienta. Klient musí důvěřovat certifikátu serveru a certifikát klienta musí být důvěryhodný pro server. Skutečné mechanismů jak klienta a služby ověří identitu uživatele toho druhého je nad rámec tohoto tématu. Další informace najdete v části [digitální podpis na webu Wikipedia](http://go.microsoft.com/fwlink/?LinkId=253157).  
  
 Tento scénář implementuje vzor zprávu požadavku/odpovědi vidíte na následujícím diagramu.  
  
 ![Zabezpečení přenosu pomocí certifikátů](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Další informace o certifikát pomocí služby najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). Následující tabulka popisuje různé vlastnosti scénáře.  
  
|Vlastnosti|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení.|Přenos|  
|Interoperabilita|S existující klienty webové služby a služby.|  
|Ověřování (Server)<br /><br /> Ověřování (klient)|Ano (pomocí certifikátu protokolu SSL)<br /><br /> Ano (pomocí certifikátu X.509)|  
|Integritu dat|Ano|  
|Důvěrnost dat|Ano|  
|Přenos|HTTPS|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Konfigurace služby  
 Vzhledem k tomu, že služba v tomto scénáři je hostována v rámci služby IIS, je nakonfigurován pomocí souboru web.config. Následující soubor web.config ukazuje, jak nakonfigurovat <xref:System.ServiceModel.WSHttpBinding> sloužící k zabezpečení přenosů a pověření klienta X.509.  
  
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
 Klienta můžete nakonfigurovat v kódu nebo v souboru app.config. Následující příklad ukazuje, jak nakonfigurovat klienta v kódu.  
  
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
  
 Případně můžete nakonfigurovat klienta do souboru App.config, jak je znázorněno v následujícím příkladu:  
  
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
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
