---
title: "Zabezpečení přenosu s ověřováním certifikátu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: abff650bd7c0e613524e4903cc754b7ff4200328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="e2b9b-102">Zabezpečení přenosu s ověřováním certifikátu</span><span class="sxs-lookup"><span data-stu-id="e2b9b-102">Transport Security with Certificate Authentication</span></span>
<span data-ttu-id="e2b9b-103">Toto téma popisuje, když pomocí zabezpečení přenosu pomocí certifikátů X.509 pro server a ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-103">This topic discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="e2b9b-104">Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikáty X.509](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="e2b9b-104">For more information about X.509 certificates see [X.509 Public Key Certificates](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx).</span></span> <span data-ttu-id="e2b9b-105">Certifikáty musí být vydaný certifikační autoritou, což se často stává třetích stran vystavitelů certifikátů.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="e2b9b-106">V doméně systému Windows Server Active Directory Certificate Services slouží k vydávání certifikátů pro klientské počítače v doméně.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="e2b9b-107">Další informace najdete v části [certifikační služby systému Windows 2008 R2](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="e2b9b-107">For more information see [Windows 2008 R2 Certificate Services](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span></span> <span data-ttu-id="e2b9b-108">V tomto scénáři je služba hostována v části Internetové informační služby (IIS), který je konfigurován s vrstvy SSL (Secure Sockets).</span><span class="sxs-lookup"><span data-stu-id="e2b9b-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="e2b9b-109">Služba je nakonfigurována pomocí certifikátu protokolu SSL (X.509), aby se klienti k ověření identity serveru.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="e2b9b-110">Klient je také nakonfigurovaný se certifikát X.509, který umožňuje službě k ověření identity klienta.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="e2b9b-111">Klient musí důvěřovat certifikátu serveru a certifikát klienta musí být důvěryhodný pro server.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="e2b9b-112">Skutečné mechanismů jak klienta a služby ověří identitu uživatele toho druhého je nad rámec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this topic.</span></span> <span data-ttu-id="e2b9b-113">Další informace najdete v části [digitální podpis na webu Wikipedia](http://go.microsoft.com/fwlink/?LinkId=253157).</span><span class="sxs-lookup"><span data-stu-id="e2b9b-113">For more information see [Digital Signature on Wikipedia](http://go.microsoft.com/fwlink/?LinkId=253157).</span></span>  
  
 <span data-ttu-id="e2b9b-114">Tento scénář implementuje vzor zprávu požadavku/odpovědi vidíte na následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="e2b9b-115">![Zabezpečení přenosu pomocí certifikátů](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="e2b9b-115">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2b9b-116">pomocí certifikátu se službou, najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="e2b9b-116"> using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="e2b9b-117">Následující tabulka popisuje různé vlastnosti scénáře.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="e2b9b-118">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e2b9b-118">Characteristic</span></span>|<span data-ttu-id="e2b9b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e2b9b-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e2b9b-120">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-120">Security Mode</span></span>|<span data-ttu-id="e2b9b-121">Přenos</span><span class="sxs-lookup"><span data-stu-id="e2b9b-121">Transport</span></span>|  
|<span data-ttu-id="e2b9b-122">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="e2b9b-122">Interoperability</span></span>|<span data-ttu-id="e2b9b-123">S existující klienty webové služby a služby.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="e2b9b-124">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="e2b9b-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="e2b9b-125">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="e2b9b-125">Authentication (Client)</span></span>|<span data-ttu-id="e2b9b-126">Ano (pomocí certifikátu protokolu SSL)</span><span class="sxs-lookup"><span data-stu-id="e2b9b-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="e2b9b-127">Ano (pomocí certifikátu X.509)</span><span class="sxs-lookup"><span data-stu-id="e2b9b-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="e2b9b-128">Integritu dat</span><span class="sxs-lookup"><span data-stu-id="e2b9b-128">Data Integrity</span></span>|<span data-ttu-id="e2b9b-129">Ano</span><span class="sxs-lookup"><span data-stu-id="e2b9b-129">Yes</span></span>|  
|<span data-ttu-id="e2b9b-130">Důvěrnost dat</span><span class="sxs-lookup"><span data-stu-id="e2b9b-130">Data Confidentiality</span></span>|<span data-ttu-id="e2b9b-131">Ano</span><span class="sxs-lookup"><span data-stu-id="e2b9b-131">Yes</span></span>|  
|<span data-ttu-id="e2b9b-132">Přenos</span><span class="sxs-lookup"><span data-stu-id="e2b9b-132">Transport</span></span>|<span data-ttu-id="e2b9b-133">PROTOKOL HTTPS</span><span class="sxs-lookup"><span data-stu-id="e2b9b-133">HTTPS</span></span>|  
|<span data-ttu-id="e2b9b-134">Vazba</span><span class="sxs-lookup"><span data-stu-id="e2b9b-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="e2b9b-135">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="e2b9b-135">Configure the Service</span></span>  
 <span data-ttu-id="e2b9b-136">Vzhledem k tomu, že služba v tomto scénáři je hostována v rámci služby IIS, je nakonfigurován pomocí souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="e2b9b-137">Následující soubor web.config ukazuje, jak nakonfigurovat <xref:System.ServiceModel.WSHttpBinding> sloužící k zabezpečení přenosů a pověření klienta X.509.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="e2b9b-138">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="e2b9b-138">Configure the Client</span></span>  
 <span data-ttu-id="e2b9b-139">Klienta můžete nakonfigurovat v kódu nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="e2b9b-140">Následující příklad ukazuje, jak nakonfigurovat klienta v kódu.</span><span class="sxs-lookup"><span data-stu-id="e2b9b-140">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="e2b9b-141">Případně můžete nakonfigurovat klienta do souboru App.config, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e2b9b-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2b9b-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2b9b-142">See Also</span></span>  
 [<span data-ttu-id="e2b9b-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e2b9b-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e2b9b-144">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="e2b9b-144">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
