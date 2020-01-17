---
title: Zabezpečení zpráv vzájemnými certifikáty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: e784e254fb9314e69457d81a70400f7be30d9c13
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211995"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="9454b-102">Zabezpečení zpráv vzájemnými certifikáty</span><span class="sxs-lookup"><span data-stu-id="9454b-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="9454b-103">Následující scénář ukazuje službu Windows Communication Foundation (WCF) a klienta zabezpečený pomocí režimu zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="9454b-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="9454b-104">Klient a služba jsou ověřovány pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9454b-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="9454b-105">Tento scénář je interoperabilní, protože používá protokol WS-Security s profilem certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9454b-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9454b-106">Tento scénář neprovádí vyjednávání certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="9454b-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="9454b-107">Certifikát služby je nutné poskytnout klientovi předem v jakékoli komunikaci.</span><span class="sxs-lookup"><span data-stu-id="9454b-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="9454b-108">Certifikát serveru se dá distribuovat s aplikací nebo se poskytuje při komunikaci mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="9454b-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="9454b-109">![Zabezpečení zpráv pomocí vzájemně vydaných certifikátů](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="9454b-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="9454b-110">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="9454b-110">Characteristic</span></span>|<span data-ttu-id="9454b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="9454b-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9454b-112">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9454b-112">Security Mode</span></span>|<span data-ttu-id="9454b-113">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9454b-113">Message</span></span>|  
|<span data-ttu-id="9454b-114">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="9454b-114">Interoperability</span></span>|<span data-ttu-id="9454b-115">Ano, s klienty a službami kompatibilními s profilem certifikátů WS-Security a X. 509.</span><span class="sxs-lookup"><span data-stu-id="9454b-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="9454b-116">Ověřování</span><span class="sxs-lookup"><span data-stu-id="9454b-116">Authentication</span></span>|<span data-ttu-id="9454b-117">Vzájemné ověřování serveru a klienta.</span><span class="sxs-lookup"><span data-stu-id="9454b-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="9454b-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="9454b-118">Integrity</span></span>|<span data-ttu-id="9454b-119">Ano</span><span class="sxs-lookup"><span data-stu-id="9454b-119">Yes</span></span>|  
|<span data-ttu-id="9454b-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="9454b-120">Confidentiality</span></span>|<span data-ttu-id="9454b-121">Ano</span><span class="sxs-lookup"><span data-stu-id="9454b-121">Yes</span></span>|  
|<span data-ttu-id="9454b-122">Doprava</span><span class="sxs-lookup"><span data-stu-id="9454b-122">Transport</span></span>|<span data-ttu-id="9454b-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="9454b-123">HTTP</span></span>|  
|<span data-ttu-id="9454b-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="9454b-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="9454b-125">Service</span><span class="sxs-lookup"><span data-stu-id="9454b-125">Service</span></span>  
 <span data-ttu-id="9454b-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="9454b-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9454b-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="9454b-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="9454b-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9454b-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="9454b-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="9454b-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9454b-130">Kód</span><span class="sxs-lookup"><span data-stu-id="9454b-130">Code</span></span>  
 <span data-ttu-id="9454b-131">Následující kód ukazuje vytvoření koncového bodu služby, který používá zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="9454b-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="9454b-132">Služba vyžaduje certifikát pro vlastní ověření.</span><span class="sxs-lookup"><span data-stu-id="9454b-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="9454b-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9454b-133">Configuration</span></span>  
 <span data-ttu-id="9454b-134">Následující konfiguraci lze použít místo kódu k vytvoření stejné služby.</span><span class="sxs-lookup"><span data-stu-id="9454b-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"   
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="9454b-135">Klient</span><span class="sxs-lookup"><span data-stu-id="9454b-135">Client</span></span>  
 <span data-ttu-id="9454b-136">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="9454b-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9454b-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="9454b-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="9454b-138">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="9454b-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="9454b-139">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="9454b-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="9454b-140">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="9454b-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="9454b-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9454b-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="9454b-142">Kód</span><span class="sxs-lookup"><span data-stu-id="9454b-142">Code</span></span>  
 <span data-ttu-id="9454b-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="9454b-143">The following code creates the client.</span></span> <span data-ttu-id="9454b-144">Režim zabezpečení je nastavený na zpráva a jako typ přihlašovacích údajů klienta se nastaví certifikát.</span><span class="sxs-lookup"><span data-stu-id="9454b-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="9454b-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9454b-145">Configuration</span></span>  
 <span data-ttu-id="9454b-146">Následující nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="9454b-146">The following configures the client.</span></span> <span data-ttu-id="9454b-147">Certifikát klienta musí být zadaný pomocí [\<ClientCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="9454b-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="9454b-148">Certifikát služby je také určen pomocí [\<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="9454b-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9454b-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9454b-149">See also</span></span>

- [<span data-ttu-id="9454b-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9454b-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="9454b-151">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9454b-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="9454b-152">[Postupy: vytváření a instalace dočasných certifikátů ve službě WCF pro zabezpečení přenosu během vývoje](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="9454b-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
