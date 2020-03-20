---
title: Zabezpečení zpráv vzájemnými certifikáty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: e2aaf1a5e6ae1074a81c08fc798f22ea5e9ce139
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184613"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="67852-102">Zabezpečení zpráv vzájemnými certifikáty</span><span class="sxs-lookup"><span data-stu-id="67852-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="67852-103">Následující scénář ukazuje službu WCF (Windows Communication Foundation) a klienta zabezpečeného pomocí režimu zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="67852-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="67852-104">Klient a služba jsou ověřeni pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="67852-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="67852-105">Tento scénář je interoperabilní, protože používá WS-Security s profilem tokenu certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="67852-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67852-106">Tento scénář neprovádí vyjednávání certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="67852-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="67852-107">Servisní certifikát musí být klientovi poskytnut před jakoukolikomunikací.</span><span class="sxs-lookup"><span data-stu-id="67852-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="67852-108">Certifikát serveru může být distribuován s aplikací nebo poskytnut v neintegrované komunikaci.</span><span class="sxs-lookup"><span data-stu-id="67852-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="67852-109">![Zabezpečení zpráv se vzájemnými certifikáty](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="67852-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="67852-110">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="67852-110">Characteristic</span></span>|<span data-ttu-id="67852-111">Popis</span><span class="sxs-lookup"><span data-stu-id="67852-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="67852-112">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67852-112">Security Mode</span></span>|<span data-ttu-id="67852-113">Zpráva</span><span class="sxs-lookup"><span data-stu-id="67852-113">Message</span></span>|  
|<span data-ttu-id="67852-114">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="67852-114">Interoperability</span></span>|<span data-ttu-id="67852-115">Ano, s ws-security a X.509 token token u klientů a služeb.</span><span class="sxs-lookup"><span data-stu-id="67852-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="67852-116">Authentication</span><span class="sxs-lookup"><span data-stu-id="67852-116">Authentication</span></span>|<span data-ttu-id="67852-117">Vzájemné ověřování serveru a klienta.</span><span class="sxs-lookup"><span data-stu-id="67852-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="67852-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="67852-118">Integrity</span></span>|<span data-ttu-id="67852-119">Ano</span><span class="sxs-lookup"><span data-stu-id="67852-119">Yes</span></span>|  
|<span data-ttu-id="67852-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="67852-120">Confidentiality</span></span>|<span data-ttu-id="67852-121">Ano</span><span class="sxs-lookup"><span data-stu-id="67852-121">Yes</span></span>|  
|<span data-ttu-id="67852-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="67852-122">Transport</span></span>|<span data-ttu-id="67852-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="67852-123">HTTP</span></span>|  
|<span data-ttu-id="67852-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="67852-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="67852-125">Služba</span><span class="sxs-lookup"><span data-stu-id="67852-125">Service</span></span>  
 <span data-ttu-id="67852-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="67852-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="67852-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="67852-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="67852-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="67852-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="67852-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="67852-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="67852-130">kód</span><span class="sxs-lookup"><span data-stu-id="67852-130">Code</span></span>  
 <span data-ttu-id="67852-131">Následující kód ukazuje vytvoří koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="67852-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="67852-132">Služba vyžaduje certifikát k ověření sám.</span><span class="sxs-lookup"><span data-stu-id="67852-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="67852-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="67852-133">Configuration</span></span>  
 <span data-ttu-id="67852-134">Následující konfiguraci lze použít namísto kódu k vytvoření stejné služby.</span><span class="sxs-lookup"><span data-stu-id="67852-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="67852-135">Klient</span><span class="sxs-lookup"><span data-stu-id="67852-135">Client</span></span>  
 <span data-ttu-id="67852-136">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="67852-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="67852-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="67852-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="67852-138">Vytvořte samostatného klienta pomocí kódu (a klientského kódu).</span><span class="sxs-lookup"><span data-stu-id="67852-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="67852-139">Vytvořte klienta, který nedefinuje žádné adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="67852-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="67852-140">Místo toho použijte konstruktor klienta, který bere název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="67852-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="67852-141">Například:</span><span class="sxs-lookup"><span data-stu-id="67852-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="67852-142">kód</span><span class="sxs-lookup"><span data-stu-id="67852-142">Code</span></span>  
 <span data-ttu-id="67852-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="67852-143">The following code creates the client.</span></span> <span data-ttu-id="67852-144">Režim zabezpečení je nastaven na Message a typ pověření klienta je nastaven na certifikát.</span><span class="sxs-lookup"><span data-stu-id="67852-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="67852-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="67852-145">Configuration</span></span>  
 <span data-ttu-id="67852-146">Následující konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="67852-146">The following configures the client.</span></span> <span data-ttu-id="67852-147">Klientský certifikát musí být zadán pomocí [ \<klientského certifikátu>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="67852-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="67852-148">Certifikát služby je také určen pomocí [ \<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="67852-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67852-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="67852-149">See also</span></span>

- [<span data-ttu-id="67852-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67852-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="67852-151">[Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="67852-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="67852-152">[Postup: Vytvoření a instalace dočasných certifikátů v wcf pro zabezpečení přenosu během vývoje](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="67852-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
