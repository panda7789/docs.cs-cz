---
title: Zabezpečení zpráv vzájemnými certifikáty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: 263ec73af7f4a6f52c4570e17cd140b6afb53601
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637839"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="5d3ab-102">Zabezpečení zpráv vzájemnými certifikáty</span><span class="sxs-lookup"><span data-stu-id="5d3ab-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="5d3ab-103">Následující scénář ukazuje služby Windows Communication Foundation (WCF) a klient zabezpečené používají režim zabezpečených zpráv.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="5d3ab-104">Klient a služba se ověří pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="5d3ab-105">Tento scénář je interoperabilní, protože používá WS-Security se token profilu certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d3ab-106">Tento scénář neprovádí vyjednávání certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="5d3ab-107">Klientovi ještě před začátkem jakékoli komunikační musí být poskytnut certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="5d3ab-108">Certifikát serveru můžete distribuovat s aplikací nebo součástí out-of-band komunikace.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="5d3ab-109">![Zabezpečení pomocí vzájemných certifikátů zpráv](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="5d3ab-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="5d3ab-110">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5d3ab-110">Characteristic</span></span>|<span data-ttu-id="5d3ab-111">Popis</span><span class="sxs-lookup"><span data-stu-id="5d3ab-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5d3ab-112">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5d3ab-112">Security Mode</span></span>|<span data-ttu-id="5d3ab-113">Message</span><span class="sxs-lookup"><span data-stu-id="5d3ab-113">Message</span></span>|  
|<span data-ttu-id="5d3ab-114">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="5d3ab-114">Interoperability</span></span>|<span data-ttu-id="5d3ab-115">Ano, s WS-Security a X.509 certifikátu tokenu profilu kompatibilní klientů a služeb.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="5d3ab-116">Ověřování</span><span class="sxs-lookup"><span data-stu-id="5d3ab-116">Authentication</span></span>|<span data-ttu-id="5d3ab-117">Vzájemné ověřování klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="5d3ab-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="5d3ab-118">Integrity</span></span>|<span data-ttu-id="5d3ab-119">Ano</span><span class="sxs-lookup"><span data-stu-id="5d3ab-119">Yes</span></span>|  
|<span data-ttu-id="5d3ab-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="5d3ab-120">Confidentiality</span></span>|<span data-ttu-id="5d3ab-121">Ano</span><span class="sxs-lookup"><span data-stu-id="5d3ab-121">Yes</span></span>|  
|<span data-ttu-id="5d3ab-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="5d3ab-122">Transport</span></span>|<span data-ttu-id="5d3ab-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="5d3ab-123">HTTP</span></span>|  
|<span data-ttu-id="5d3ab-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="5d3ab-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="5d3ab-125">Služba</span><span class="sxs-lookup"><span data-stu-id="5d3ab-125">Service</span></span>  
 <span data-ttu-id="5d3ab-126">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5d3ab-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="5d3ab-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="5d3ab-128">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="5d3ab-129">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5d3ab-130">Kód</span><span class="sxs-lookup"><span data-stu-id="5d3ab-130">Code</span></span>  
 <span data-ttu-id="5d3ab-131">Následující kód vytvoří koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="5d3ab-132">Služba vyžaduje, aby certifikát ke svému ověření.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="5d3ab-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5d3ab-133">Configuration</span></span>  
 <span data-ttu-id="5d3ab-134">Následující konfigurace lze namísto kódu vytvořit ve stejné službě.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="5d3ab-135">Klient</span><span class="sxs-lookup"><span data-stu-id="5d3ab-135">Client</span></span>  
 <span data-ttu-id="5d3ab-136">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5d3ab-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="5d3ab-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="5d3ab-138">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="5d3ab-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="5d3ab-139">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5d3ab-140">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5d3ab-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5d3ab-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5d3ab-142">Kód</span><span class="sxs-lookup"><span data-stu-id="5d3ab-142">Code</span></span>  
 <span data-ttu-id="5d3ab-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-143">The following code creates the client.</span></span> <span data-ttu-id="5d3ab-144">Režim zabezpečení je nastavena na zprávu a typu pověření klienta je nastavena na certifikát.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="5d3ab-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5d3ab-145">Configuration</span></span>  
 <span data-ttu-id="5d3ab-146">Následující nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-146">The following configures the client.</span></span> <span data-ttu-id="5d3ab-147">Klientský certifikát musí být zadán pomocí [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="5d3ab-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="5d3ab-148">Kromě toho certifikátu služby je určen pomocí [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="5d3ab-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d3ab-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d3ab-149">See also</span></span>

- [<span data-ttu-id="5d3ab-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5d3ab-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="5d3ab-151">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="5d3ab-151">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
- [<span data-ttu-id="5d3ab-152">Postupy: Vytvoření a instalace dočasných certifikátů ve službě WCF pro zabezpečení přenosu během vývoje.</span><span class="sxs-lookup"><span data-stu-id="5d3ab-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](https://go.microsoft.com/fwlink/?LinkId=244264)
