---
title: Zabezpečení zpráv pomocí klientských certifikátů
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: 16
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 6e31c7a9e53e8b918661c0c6c544e697e2a772e6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="98278-102">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="98278-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="98278-103">Následující scénář ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby zabezpečené pomocí režim zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="98278-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured using message security mode.</span></span> <span data-ttu-id="98278-104">Klienta a služby se ověřují pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="98278-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="98278-105">Další informace najdete v tématu [zabezpečení distribuované aplikace](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="98278-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="98278-106">Ukázkovou aplikaci, najdete v části [certifikát zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="98278-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="98278-107">![Klient s certifikátem](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="98278-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="98278-108">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="98278-108">Characteristic</span></span>|<span data-ttu-id="98278-109">Popis</span><span class="sxs-lookup"><span data-stu-id="98278-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="98278-110">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="98278-110">Security Mode</span></span>|<span data-ttu-id="98278-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="98278-111">Message</span></span>|  
|<span data-ttu-id="98278-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="98278-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="98278-113"> Pouze</span><span class="sxs-lookup"><span data-stu-id="98278-113"> only</span></span>|  
|<span data-ttu-id="98278-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="98278-114">Authentication (Server)</span></span>|<span data-ttu-id="98278-115">Pomocí certifikátu služby</span><span class="sxs-lookup"><span data-stu-id="98278-115">Using service certificate</span></span>|  
|<span data-ttu-id="98278-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="98278-116">Authentication (Client)</span></span>|<span data-ttu-id="98278-117">Pomocí klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="98278-117">Using client certificate</span></span>|  
|<span data-ttu-id="98278-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="98278-118">Integrity</span></span>|<span data-ttu-id="98278-119">Ano</span><span class="sxs-lookup"><span data-stu-id="98278-119">Yes</span></span>|  
|<span data-ttu-id="98278-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="98278-120">Confidentiality</span></span>|<span data-ttu-id="98278-121">Ano</span><span class="sxs-lookup"><span data-stu-id="98278-121">Yes</span></span>|  
|<span data-ttu-id="98278-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="98278-122">Transport</span></span>|<span data-ttu-id="98278-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="98278-123">HTTP</span></span>|  
|<span data-ttu-id="98278-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="98278-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="98278-125">Služba</span><span class="sxs-lookup"><span data-stu-id="98278-125">Service</span></span>  
 <span data-ttu-id="98278-126">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="98278-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="98278-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="98278-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="98278-128">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="98278-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="98278-129">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="98278-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="98278-130">Kód</span><span class="sxs-lookup"><span data-stu-id="98278-130">Code</span></span>  
 <span data-ttu-id="98278-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá k navázání zabezpečeného kontextu zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="98278-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="98278-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="98278-132">Configuration</span></span>  
 <span data-ttu-id="98278-133">Následující konfigurace můžete použít místo kód.</span><span class="sxs-lookup"><span data-stu-id="98278-133">The following configuration can be used instead of the code.</span></span>  
  
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
                  bindingConfiguration="MessageAndCerficiateClient"   
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
  
## <a name="client"></a><span data-ttu-id="98278-134">Klient</span><span class="sxs-lookup"><span data-stu-id="98278-134">Client</span></span>  
 <span data-ttu-id="98278-135">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="98278-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="98278-136">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="98278-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="98278-137">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="98278-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="98278-138">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="98278-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="98278-139">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="98278-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="98278-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="98278-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="98278-141">Kód</span><span class="sxs-lookup"><span data-stu-id="98278-141">Code</span></span>  
 <span data-ttu-id="98278-142">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="98278-142">The following code creates the client.</span></span> <span data-ttu-id="98278-143">Vazba je režim zabezpečení zpráv a typu pověření klienta nastavena na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="98278-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="98278-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="98278-144">Configuration</span></span>  
 <span data-ttu-id="98278-145">Následující konfigurace Určuje certifikát klienta pomocí chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="98278-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="98278-146">Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="98278-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="98278-147">Kód také používá <`identity`> elementu, který chcete zadat systému DNS (Domain Name) identity očekávané serveru.</span><span class="sxs-lookup"><span data-stu-id="98278-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="98278-148">Další informace o identitě najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="98278-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98278-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="98278-149">See Also</span></span>  
 [<span data-ttu-id="98278-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="98278-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="98278-151">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="98278-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="98278-152">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="98278-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="98278-153">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="98278-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
