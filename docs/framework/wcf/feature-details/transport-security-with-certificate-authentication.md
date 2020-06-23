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
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="53116-103">Zabezpečení přenosu s ověřováním certifikátu</span><span class="sxs-lookup"><span data-stu-id="53116-103">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="53116-104">Tento článek popisuje použití certifikátů X. 509 pro ověřování serverů a klientů při použití zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="53116-104">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="53116-105">Další informace o certifikátech X. 509 najdete v tématu [certifikáty s veřejným klíčem x. 509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="53116-105">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="53116-106">Certifikáty musí vystavit certifikační autorita, což je často Vystavitel certifikátů třetích stran.</span><span class="sxs-lookup"><span data-stu-id="53116-106">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="53116-107">V doméně systému Windows Server lze použít službu AD CS (Active Directory Certificate Services) k vystavování certifikátů klientským počítačům v doméně.</span><span class="sxs-lookup"><span data-stu-id="53116-107">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="53116-108">V tomto scénáři je služba hostovaná v rámci služby Internetová informační služba (IIS), která je nakonfigurovaná s SSL (Secure Sockets Layer) (SSL).</span><span class="sxs-lookup"><span data-stu-id="53116-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="53116-109">Služba je nakonfigurována pomocí certifikátu SSL (X. 509), který klientům umožňuje ověřit identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="53116-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="53116-110">Klient je také nakonfigurován s certifikátem X. 509, který umožňuje službě ověřit identitu klienta.</span><span class="sxs-lookup"><span data-stu-id="53116-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="53116-111">Certifikát serveru musí být důvěryhodný pro klienta a certifikát klienta musí být důvěryhodný serverem.</span><span class="sxs-lookup"><span data-stu-id="53116-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="53116-112">Skutečný způsob, jakým služba a klient ověřuje identitu druhé strany, je nad rámec tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="53116-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="53116-113">Další informace najdete v tématu [digitální podpis](https://en.wikipedia.org/wiki/Digital_signature) v Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="53116-113">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="53116-114">Tento scénář implementuje vzor zprávy žádosti nebo odpovědi, jak je znázorněno v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="53116-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="53116-115">![Zabezpečený přenos pomocí certifikátů](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="53116-115">![Secure transfer using certificates](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="53116-116">Další informace o používání certifikátu se službou najdete v tématu [práce s certifikáty](working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="53116-116">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="53116-117">V následující tabulce jsou popsány různé charakteristiky scénáře.</span><span class="sxs-lookup"><span data-stu-id="53116-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="53116-118">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="53116-118">Characteristic</span></span>|<span data-ttu-id="53116-119">Description</span><span class="sxs-lookup"><span data-stu-id="53116-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="53116-120">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="53116-120">Security Mode</span></span>|<span data-ttu-id="53116-121">Přenos</span><span class="sxs-lookup"><span data-stu-id="53116-121">Transport</span></span>|  
|<span data-ttu-id="53116-122">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="53116-122">Interoperability</span></span>|<span data-ttu-id="53116-123">Se stávajícími klienty a službami webové služby.</span><span class="sxs-lookup"><span data-stu-id="53116-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="53116-124">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="53116-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="53116-125">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="53116-125">Authentication (Client)</span></span>|<span data-ttu-id="53116-126">Ano (pomocí certifikátu SSL)</span><span class="sxs-lookup"><span data-stu-id="53116-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="53116-127">Ano (pomocí certifikátu X. 509)</span><span class="sxs-lookup"><span data-stu-id="53116-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="53116-128">Integrita dat</span><span class="sxs-lookup"><span data-stu-id="53116-128">Data Integrity</span></span>|<span data-ttu-id="53116-129">Ano</span><span class="sxs-lookup"><span data-stu-id="53116-129">Yes</span></span>|  
|<span data-ttu-id="53116-130">Důvěrnost dat</span><span class="sxs-lookup"><span data-stu-id="53116-130">Data Confidentiality</span></span>|<span data-ttu-id="53116-131">Ano</span><span class="sxs-lookup"><span data-stu-id="53116-131">Yes</span></span>|  
|<span data-ttu-id="53116-132">Přenos</span><span class="sxs-lookup"><span data-stu-id="53116-132">Transport</span></span>|<span data-ttu-id="53116-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="53116-133">HTTPS</span></span>|  
|<span data-ttu-id="53116-134">Vazba</span><span class="sxs-lookup"><span data-stu-id="53116-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="53116-135">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="53116-135">Configure the Service</span></span>  
 <span data-ttu-id="53116-136">Vzhledem k tomu, že je služba v tomto scénáři hostovaná v rámci služby IIS, je nakonfigurovaná s web.config souborem.</span><span class="sxs-lookup"><span data-stu-id="53116-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="53116-137">Následující web.config ukazuje, jak nakonfigurovat <xref:System.ServiceModel.WSHttpBinding> pro použití zabezpečení přenosu a pověření klienta X. 509.</span><span class="sxs-lookup"><span data-stu-id="53116-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="53116-138">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="53116-138">Configure the Client</span></span>  
 <span data-ttu-id="53116-139">Klienta lze nakonfigurovat v kódu nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="53116-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="53116-140">Následující příklad ukazuje, jak nakonfigurovat klienta v kódu.</span><span class="sxs-lookup"><span data-stu-id="53116-140">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="53116-141">Případně můžete klienta nakonfigurovat v souboru App.config, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="53116-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53116-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="53116-142">See also</span></span>

- [<span data-ttu-id="53116-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="53116-143">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="53116-144">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="53116-144">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
