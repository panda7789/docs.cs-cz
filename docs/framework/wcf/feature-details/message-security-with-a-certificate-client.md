---
title: Zabezpečení zpráv pomocí klientských certifikátů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 4b282062040ccfc18534ad88effc4c0f1972c5a6
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212057"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="df350-102">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="df350-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="df350-103">Následující scénář zobrazuje klienta a službu Windows Communication Foundation (WCF) zabezpečený pomocí režimu zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="df350-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="df350-104">Klient i služba jsou ověřovány pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="df350-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="df350-105">Další informace najdete v tématu [zabezpečení distribuované aplikace](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="df350-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Snímek obrazovky zobrazující klienta s certifikátem](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="df350-107">Ukázkovou aplikaci najdete v tématu [certifikát zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="df350-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="df350-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="df350-108">Characteristic</span></span>|<span data-ttu-id="df350-109">Popis</span><span class="sxs-lookup"><span data-stu-id="df350-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="df350-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="df350-110">Security Mode</span></span>|<span data-ttu-id="df350-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="df350-111">Message</span></span>|  
|<span data-ttu-id="df350-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="df350-112">Interoperability</span></span>|<span data-ttu-id="df350-113">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="df350-113">WCF only</span></span>|  
|<span data-ttu-id="df350-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="df350-114">Authentication (Server)</span></span>|<span data-ttu-id="df350-115">Použití certifikátu služby</span><span class="sxs-lookup"><span data-stu-id="df350-115">Using service certificate</span></span>|  
|<span data-ttu-id="df350-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="df350-116">Authentication (Client)</span></span>|<span data-ttu-id="df350-117">Použití klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="df350-117">Using client certificate</span></span>|  
|<span data-ttu-id="df350-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="df350-118">Integrity</span></span>|<span data-ttu-id="df350-119">Ano</span><span class="sxs-lookup"><span data-stu-id="df350-119">Yes</span></span>|  
|<span data-ttu-id="df350-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="df350-120">Confidentiality</span></span>|<span data-ttu-id="df350-121">Ano</span><span class="sxs-lookup"><span data-stu-id="df350-121">Yes</span></span>|  
|<span data-ttu-id="df350-122">Doprava</span><span class="sxs-lookup"><span data-stu-id="df350-122">Transport</span></span>|<span data-ttu-id="df350-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="df350-123">HTTP</span></span>|  
|<span data-ttu-id="df350-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="df350-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="df350-125">Service</span><span class="sxs-lookup"><span data-stu-id="df350-125">Service</span></span>  
 <span data-ttu-id="df350-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="df350-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="df350-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="df350-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="df350-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="df350-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="df350-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="df350-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="df350-130">Kód</span><span class="sxs-lookup"><span data-stu-id="df350-130">Code</span></span>  
 <span data-ttu-id="df350-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k vytvoření zabezpečeného kontextu.</span><span class="sxs-lookup"><span data-stu-id="df350-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="df350-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="df350-132">Configuration</span></span>  
 <span data-ttu-id="df350-133">Místo kódu lze použít následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="df350-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="df350-134">Klient</span><span class="sxs-lookup"><span data-stu-id="df350-134">Client</span></span>  
 <span data-ttu-id="df350-135">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="df350-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="df350-136">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="df350-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="df350-137">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="df350-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="df350-138">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="df350-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="df350-139">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="df350-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="df350-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="df350-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="df350-141">Kód</span><span class="sxs-lookup"><span data-stu-id="df350-141">Code</span></span>  
 <span data-ttu-id="df350-142">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="df350-142">The following code creates the client.</span></span> <span data-ttu-id="df350-143">Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="df350-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="df350-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="df350-144">Configuration</span></span>  
 <span data-ttu-id="df350-145">Následující konfigurace určuje klientský certifikát pomocí chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="df350-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="df350-146">Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="df350-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="df350-147">Kód také používá <`identity`> element k určení systému DNS (Domain Name System) očekávané identity serveru.</span><span class="sxs-lookup"><span data-stu-id="df350-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="df350-148">Další informace o identitě najdete v tématu [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="df350-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df350-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df350-149">See also</span></span>

- [<span data-ttu-id="df350-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="df350-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="df350-151">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="df350-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="df350-152">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="df350-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- <span data-ttu-id="df350-153">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="df350-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
