---
title: "Zabezpečení zpráv pomocí klientských certifikátů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: afc1e0def03040acaa5cffe3f67339a61cda7d5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="5426c-102">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="5426c-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="5426c-103">Následující scénář ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby zabezpečené pomocí režim zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="5426c-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured using message security mode.</span></span> <span data-ttu-id="5426c-104">Klienta a služby se ověřují pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="5426c-104">Both the client and the service are authenticated with certificates.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="5426c-105">[Distribuované aplikace zabezpečení](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="5426c-105"> [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="5426c-106">Ukázkovou aplikaci, najdete v části [certifikát zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="5426c-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="5426c-107">![Klient s certifikátem](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="5426c-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="5426c-108">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5426c-108">Characteristic</span></span>|<span data-ttu-id="5426c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5426c-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5426c-110">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5426c-110">Security Mode</span></span>|<span data-ttu-id="5426c-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5426c-111">Message</span></span>|  
|<span data-ttu-id="5426c-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="5426c-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="5426c-113">pouze</span><span class="sxs-lookup"><span data-stu-id="5426c-113"> only</span></span>|  
|<span data-ttu-id="5426c-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="5426c-114">Authentication (Server)</span></span>|<span data-ttu-id="5426c-115">Pomocí certifikátu služby</span><span class="sxs-lookup"><span data-stu-id="5426c-115">Using service certificate</span></span>|  
|<span data-ttu-id="5426c-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="5426c-116">Authentication (Client)</span></span>|<span data-ttu-id="5426c-117">Pomocí klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="5426c-117">Using client certificate</span></span>|  
|<span data-ttu-id="5426c-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="5426c-118">Integrity</span></span>|<span data-ttu-id="5426c-119">Ano</span><span class="sxs-lookup"><span data-stu-id="5426c-119">Yes</span></span>|  
|<span data-ttu-id="5426c-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="5426c-120">Confidentiality</span></span>|<span data-ttu-id="5426c-121">Ano</span><span class="sxs-lookup"><span data-stu-id="5426c-121">Yes</span></span>|  
|<span data-ttu-id="5426c-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="5426c-122">Transport</span></span>|<span data-ttu-id="5426c-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="5426c-123">HTTP</span></span>|  
|<span data-ttu-id="5426c-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="5426c-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="5426c-125">Služba</span><span class="sxs-lookup"><span data-stu-id="5426c-125">Service</span></span>  
 <span data-ttu-id="5426c-126">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="5426c-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5426c-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="5426c-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5426c-128">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5426c-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5426c-129">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="5426c-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5426c-130">Kód</span><span class="sxs-lookup"><span data-stu-id="5426c-130">Code</span></span>  
 <span data-ttu-id="5426c-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá k navázání zabezpečeného kontextu zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="5426c-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="5426c-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5426c-132">Configuration</span></span>  
 <span data-ttu-id="5426c-133">Následující konfigurace můžete použít místo kód.</span><span class="sxs-lookup"><span data-stu-id="5426c-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="5426c-134">Klient</span><span class="sxs-lookup"><span data-stu-id="5426c-134">Client</span></span>  
 <span data-ttu-id="5426c-135">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="5426c-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5426c-136">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="5426c-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5426c-137">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="5426c-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="5426c-138">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="5426c-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5426c-139">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5426c-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5426c-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5426c-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5426c-141">Kód</span><span class="sxs-lookup"><span data-stu-id="5426c-141">Code</span></span>  
 <span data-ttu-id="5426c-142">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="5426c-142">The following code creates the client.</span></span> <span data-ttu-id="5426c-143">Vazba je režim zabezpečení zpráv a typu pověření klienta nastavena na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="5426c-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="5426c-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5426c-144">Configuration</span></span>  
 <span data-ttu-id="5426c-145">Následující konfigurace Určuje certifikát klienta pomocí chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="5426c-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="5426c-146">Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="5426c-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="5426c-147">Kód také používá <`identity`> elementu, který chcete zadat systému DNS (Domain Name) identity očekávané serveru.</span><span class="sxs-lookup"><span data-stu-id="5426c-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5426c-148">identity, najdete v části [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5426c-148"> identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5426c-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="5426c-149">See Also</span></span>  
 [<span data-ttu-id="5426c-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5426c-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="5426c-151">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="5426c-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5426c-152">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="5426c-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="5426c-153">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="5426c-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
