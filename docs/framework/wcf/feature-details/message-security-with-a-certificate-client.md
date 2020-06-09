---
title: Zabezpečení zpráv pomocí klientských certifikátů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 2b2717bc68da9f07cd38e10a5d75b2a7df9add45
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602632"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="57127-102">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="57127-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="57127-103">Následující scénář zobrazuje klienta a službu Windows Communication Foundation (WCF) zabezpečený pomocí režimu zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="57127-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="57127-104">Klient i služba jsou ověřovány pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="57127-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="57127-105">Další informace najdete v tématu [zabezpečení distribuované aplikace](distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="57127-105">For more information, see [Distributed Application Security](distributed-application-security.md).</span></span>

 ![Snímek obrazovky zobrazující klienta s certifikátem](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="57127-107">Ukázkovou aplikaci najdete v tématu [certifikát zabezpečení zpráv](../samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="57127-107">For a sample application, see [Message Security Certificate](../samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="57127-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="57127-108">Characteristic</span></span>|<span data-ttu-id="57127-109">Popis</span><span class="sxs-lookup"><span data-stu-id="57127-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="57127-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="57127-110">Security Mode</span></span>|<span data-ttu-id="57127-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="57127-111">Message</span></span>|  
|<span data-ttu-id="57127-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="57127-112">Interoperability</span></span>|<span data-ttu-id="57127-113">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="57127-113">WCF only</span></span>|  
|<span data-ttu-id="57127-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="57127-114">Authentication (Server)</span></span>|<span data-ttu-id="57127-115">Použití certifikátu služby</span><span class="sxs-lookup"><span data-stu-id="57127-115">Using service certificate</span></span>|  
|<span data-ttu-id="57127-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="57127-116">Authentication (Client)</span></span>|<span data-ttu-id="57127-117">Použití klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="57127-117">Using client certificate</span></span>|  
|<span data-ttu-id="57127-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="57127-118">Integrity</span></span>|<span data-ttu-id="57127-119">Yes</span><span class="sxs-lookup"><span data-stu-id="57127-119">Yes</span></span>|  
|<span data-ttu-id="57127-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="57127-120">Confidentiality</span></span>|<span data-ttu-id="57127-121">Yes</span><span class="sxs-lookup"><span data-stu-id="57127-121">Yes</span></span>|  
|<span data-ttu-id="57127-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="57127-122">Transport</span></span>|<span data-ttu-id="57127-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="57127-123">HTTP</span></span>|  
|<span data-ttu-id="57127-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="57127-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="57127-125">Služba</span><span class="sxs-lookup"><span data-stu-id="57127-125">Service</span></span>  
 <span data-ttu-id="57127-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="57127-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="57127-127">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="57127-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="57127-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="57127-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="57127-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="57127-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="57127-130">Kód</span><span class="sxs-lookup"><span data-stu-id="57127-130">Code</span></span>  
 <span data-ttu-id="57127-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k vytvoření zabezpečeného kontextu.</span><span class="sxs-lookup"><span data-stu-id="57127-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="57127-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="57127-132">Configuration</span></span>  
 <span data-ttu-id="57127-133">Místo kódu lze použít následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="57127-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="57127-134">Klient</span><span class="sxs-lookup"><span data-stu-id="57127-134">Client</span></span>  
 <span data-ttu-id="57127-135">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="57127-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="57127-136">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="57127-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="57127-137">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="57127-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="57127-138">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="57127-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="57127-139">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="57127-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="57127-140">Například:</span><span class="sxs-lookup"><span data-stu-id="57127-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="57127-141">Kód</span><span class="sxs-lookup"><span data-stu-id="57127-141">Code</span></span>  
 <span data-ttu-id="57127-142">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="57127-142">The following code creates the client.</span></span> <span data-ttu-id="57127-143">Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na hodnotu `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="57127-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="57127-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="57127-144">Configuration</span></span>  
 <span data-ttu-id="57127-145">Následující konfigurace určuje klientský certifikát pomocí chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="57127-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="57127-146">Další informace o certifikátech najdete v tématu [práce s certifikáty](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="57127-146">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="57127-147">Kód také používá <`identity`> element k určení systému DNS (Domain Name System) očekávané identity serveru.</span><span class="sxs-lookup"><span data-stu-id="57127-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="57127-148">Další informace o identitě najdete v tématu [Identita a ověřování služby](service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="57127-148">For more information about identity, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57127-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="57127-149">See also</span></span>

- [<span data-ttu-id="57127-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="57127-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="57127-151">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="57127-151">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [<span data-ttu-id="57127-152">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="57127-152">Working with Certificates</span></span>](working-with-certificates.md)
- <span data-ttu-id="57127-153">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="57127-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
