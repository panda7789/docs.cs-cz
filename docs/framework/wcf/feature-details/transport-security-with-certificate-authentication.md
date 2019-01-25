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
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="b59f6-102">Zabezpečení přenosu s ověřováním certifikátu</span><span class="sxs-lookup"><span data-stu-id="b59f6-102">Transport Security with Certificate Authentication</span></span>
<span data-ttu-id="b59f6-103">Toto téma popisuje, při použití zabezpečení přenosu pomocí certifikátů X.509 pro ověření klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="b59f6-103">This topic discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="b59f6-104">Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikátů X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="b59f6-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="b59f6-105">Certifikáty musí být vystavené certifikační autority, což se často stává třetích stran vystavitelů certifikátů.</span><span class="sxs-lookup"><span data-stu-id="b59f6-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="b59f6-106">V doméně systému Windows Server Active Directory Certificate Services slouží k vydávání certifikátů pro klientské počítače v doméně.</span><span class="sxs-lookup"><span data-stu-id="b59f6-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="b59f6-107">Další informace najdete v části [Windows 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="b59f6-107">For more information see [Windows 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span></span> <span data-ttu-id="b59f6-108">V tomto scénáři je služba hostována v části Internetová informační služba (), který je nakonfigurovaný s vrstvy SSL (Secure Sockets).</span><span class="sxs-lookup"><span data-stu-id="b59f6-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="b59f6-109">Služba je nakonfigurována s certifikátem protokolu SSL (X.509) a umožňuje klientům ověřit identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="b59f6-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="b59f6-110">Klient je také nakonfigurováno s certifikát X.509, který umožňuje službě k ověření identity klienta.</span><span class="sxs-lookup"><span data-stu-id="b59f6-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="b59f6-111">Klient musí důvěřovat certifikátu serveru a server musí důvěřovat certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="b59f6-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="b59f6-112">Skutečné mechanismu jak klienta a služby ověří identitu uživatele toho druhého je nad rámec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b59f6-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this topic.</span></span> <span data-ttu-id="b59f6-113">Další informace najdete v části [digitální podpis v encyklopedii Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).</span><span class="sxs-lookup"><span data-stu-id="b59f6-113">For more information see [Digital Signature on Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).</span></span>  
  
 <span data-ttu-id="b59f6-114">Tento scénář implementuje vzoru zprávy požadavku/odpovědi, jak je znázorněno v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="b59f6-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="b59f6-115">![Vyžádání bezpečného přenosu pomocí certifikátů](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="b59f6-115">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="b59f6-116">Další informace o pomocí certifikátu služby najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [jak: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="b59f6-116">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="b59f6-117">Následující tabulka popisuje vlastnosti různé scénáře.</span><span class="sxs-lookup"><span data-stu-id="b59f6-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="b59f6-118">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b59f6-118">Characteristic</span></span>|<span data-ttu-id="b59f6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b59f6-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b59f6-120">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b59f6-120">Security Mode</span></span>|<span data-ttu-id="b59f6-121">Přenos</span><span class="sxs-lookup"><span data-stu-id="b59f6-121">Transport</span></span>|  
|<span data-ttu-id="b59f6-122">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b59f6-122">Interoperability</span></span>|<span data-ttu-id="b59f6-123">S existující klienty webové služby a služby.</span><span class="sxs-lookup"><span data-stu-id="b59f6-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="b59f6-124">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="b59f6-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="b59f6-125">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="b59f6-125">Authentication (Client)</span></span>|<span data-ttu-id="b59f6-126">Ano (použití certifikátu SSL)</span><span class="sxs-lookup"><span data-stu-id="b59f6-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="b59f6-127">Ano (pomocí certifikátu X.509)</span><span class="sxs-lookup"><span data-stu-id="b59f6-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="b59f6-128">Integrita dat</span><span class="sxs-lookup"><span data-stu-id="b59f6-128">Data Integrity</span></span>|<span data-ttu-id="b59f6-129">Ano</span><span class="sxs-lookup"><span data-stu-id="b59f6-129">Yes</span></span>|  
|<span data-ttu-id="b59f6-130">Zajištění anonymity dat.</span><span class="sxs-lookup"><span data-stu-id="b59f6-130">Data Confidentiality</span></span>|<span data-ttu-id="b59f6-131">Ano</span><span class="sxs-lookup"><span data-stu-id="b59f6-131">Yes</span></span>|  
|<span data-ttu-id="b59f6-132">Přenos</span><span class="sxs-lookup"><span data-stu-id="b59f6-132">Transport</span></span>|<span data-ttu-id="b59f6-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="b59f6-133">HTTPS</span></span>|  
|<span data-ttu-id="b59f6-134">Vazba</span><span class="sxs-lookup"><span data-stu-id="b59f6-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="b59f6-135">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="b59f6-135">Configure the Service</span></span>  
 <span data-ttu-id="b59f6-136">Protože služba v tomto scénáři je hostována v rámci služby IIS, je nakonfigurován se souborem web.config.</span><span class="sxs-lookup"><span data-stu-id="b59f6-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="b59f6-137">Následující soubor web.config ukazuje postup při konfiguraci <xref:System.ServiceModel.WSHttpBinding> použít k zabezpečení přenosů a přihlašovací údaje klienta X.509.</span><span class="sxs-lookup"><span data-stu-id="b59f6-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="b59f6-138">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="b59f6-138">Configure the Client</span></span>  
 <span data-ttu-id="b59f6-139">Klientovi lze nastavit v kódu nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="b59f6-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="b59f6-140">Následující příklad ukazuje, jak nakonfigurovat klienta v kódu.</span><span class="sxs-lookup"><span data-stu-id="b59f6-140">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="b59f6-141">Případně můžete nakonfigurovat klienta v souboru App.config, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b59f6-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b59f6-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b59f6-142">See also</span></span>
- [<span data-ttu-id="b59f6-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b59f6-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="b59f6-144">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="b59f6-144">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
