---
title: Zabezpečení zpráv pomocí klientských certifikátů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 3660877194931c2be5b9b1c9aa54e2595701697f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184648"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="67722-102">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="67722-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="67722-103">Následující scénář ukazuje klienta a služby WCF (Windows Communication Foundation) zabezpečené pomocí režimu zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="67722-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="67722-104">Klient i služba jsou ověřeni pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="67722-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="67722-105">Další informace naleznete v [tématu Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="67722-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Snímek obrazovky, který zobrazuje klienta s certifikátem.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="67722-107">Ukázková aplikace naleznete v tématu [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="67722-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="67722-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="67722-108">Characteristic</span></span>|<span data-ttu-id="67722-109">Popis</span><span class="sxs-lookup"><span data-stu-id="67722-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="67722-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67722-110">Security Mode</span></span>|<span data-ttu-id="67722-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="67722-111">Message</span></span>|  
|<span data-ttu-id="67722-112">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="67722-112">Interoperability</span></span>|<span data-ttu-id="67722-113">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="67722-113">WCF only</span></span>|  
|<span data-ttu-id="67722-114">Ověřování (server)</span><span class="sxs-lookup"><span data-stu-id="67722-114">Authentication (Server)</span></span>|<span data-ttu-id="67722-115">Použití servisního certifikátu</span><span class="sxs-lookup"><span data-stu-id="67722-115">Using service certificate</span></span>|  
|<span data-ttu-id="67722-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="67722-116">Authentication (Client)</span></span>|<span data-ttu-id="67722-117">Použití klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="67722-117">Using client certificate</span></span>|  
|<span data-ttu-id="67722-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="67722-118">Integrity</span></span>|<span data-ttu-id="67722-119">Ano</span><span class="sxs-lookup"><span data-stu-id="67722-119">Yes</span></span>|  
|<span data-ttu-id="67722-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="67722-120">Confidentiality</span></span>|<span data-ttu-id="67722-121">Ano</span><span class="sxs-lookup"><span data-stu-id="67722-121">Yes</span></span>|  
|<span data-ttu-id="67722-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="67722-122">Transport</span></span>|<span data-ttu-id="67722-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="67722-123">HTTP</span></span>|  
|<span data-ttu-id="67722-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="67722-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="67722-125">Služba</span><span class="sxs-lookup"><span data-stu-id="67722-125">Service</span></span>  
 <span data-ttu-id="67722-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="67722-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="67722-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="67722-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="67722-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="67722-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="67722-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="67722-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="67722-130">kód</span><span class="sxs-lookup"><span data-stu-id="67722-130">Code</span></span>  
 <span data-ttu-id="67722-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k vytvoření zabezpečeného kontextu.</span><span class="sxs-lookup"><span data-stu-id="67722-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="67722-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="67722-132">Configuration</span></span>  
 <span data-ttu-id="67722-133">Následující konfiguraci lze použít namísto kódu.</span><span class="sxs-lookup"><span data-stu-id="67722-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="67722-134">Klient</span><span class="sxs-lookup"><span data-stu-id="67722-134">Client</span></span>  
 <span data-ttu-id="67722-135">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="67722-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="67722-136">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="67722-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="67722-137">Vytvořte samostatného klienta pomocí kódu (a klientského kódu).</span><span class="sxs-lookup"><span data-stu-id="67722-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="67722-138">Vytvořte klienta, který nedefinuje žádné adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="67722-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="67722-139">Místo toho použijte konstruktor klienta, který bere název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="67722-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="67722-140">Například:</span><span class="sxs-lookup"><span data-stu-id="67722-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="67722-141">kód</span><span class="sxs-lookup"><span data-stu-id="67722-141">Code</span></span>  
 <span data-ttu-id="67722-142">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="67722-142">The following code creates the client.</span></span> <span data-ttu-id="67722-143">Vazba je zabezpečení režimu zprávy a typ `Certificate`pověření klienta je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="67722-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="67722-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="67722-144">Configuration</span></span>  
 <span data-ttu-id="67722-145">Následující konfigurace určuje klientský certifikát pomocí chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="67722-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="67722-146">Další informace o certifikátech naleznete v [tématu Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="67722-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="67722-147">Kód také používá `identity` <> prvek k určení dns (DOMAIN Name System) očekávané identity serveru.</span><span class="sxs-lookup"><span data-stu-id="67722-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="67722-148">Další informace o identitě naleznete v [tématu Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="67722-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67722-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="67722-149">See also</span></span>

- [<span data-ttu-id="67722-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67722-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="67722-151">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="67722-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="67722-152">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="67722-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- <span data-ttu-id="67722-153">[Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="67722-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
