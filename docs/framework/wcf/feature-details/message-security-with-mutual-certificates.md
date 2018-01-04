---
title: "Zabezpečení zpráv vzájemnými certifikáty"
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
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a60af220bf962e523a35bc5b8d8abca041a9fd46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="56b19-102">Zabezpečení zpráv vzájemnými certifikáty</span><span class="sxs-lookup"><span data-stu-id="56b19-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="56b19-103">Následující scénář ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpečené režim zabezpečení zprávy pomocí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="56b19-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client secured using message security mode.</span></span> <span data-ttu-id="56b19-104">Klienta a služby se ověřují pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="56b19-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="56b19-105">Tento scénář je umožňuje vzájemnou spolupráci, protože používá WS-zabezpečení s profilem tokenu certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="56b19-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56b19-106">Tento scénář neprovede vyjednávání certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="56b19-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="56b19-107">Certifikát služby musí být zadaný pro klienta předem žádné komunikace.</span><span class="sxs-lookup"><span data-stu-id="56b19-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="56b19-108">Certifikát serveru můžete distribuovat s aplikací nebo součástí out-of-band komunikace.</span><span class="sxs-lookup"><span data-stu-id="56b19-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="56b19-109">![Zpráva zabezpečení vzájemnými certifikáty](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="56b19-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="56b19-110">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="56b19-110">Characteristic</span></span>|<span data-ttu-id="56b19-111">Popis</span><span class="sxs-lookup"><span data-stu-id="56b19-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="56b19-112">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="56b19-112">Security Mode</span></span>|<span data-ttu-id="56b19-113">Zpráva</span><span class="sxs-lookup"><span data-stu-id="56b19-113">Message</span></span>|  
|<span data-ttu-id="56b19-114">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="56b19-114">Interoperability</span></span>|<span data-ttu-id="56b19-115">Ano, s WS-zabezpečení a X.509 certifikátu tokenu profil kompatibilní klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="56b19-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="56b19-116">Ověřování</span><span class="sxs-lookup"><span data-stu-id="56b19-116">Authentication</span></span>|<span data-ttu-id="56b19-117">Vzájemné ověřování klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="56b19-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="56b19-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="56b19-118">Integrity</span></span>|<span data-ttu-id="56b19-119">Ano</span><span class="sxs-lookup"><span data-stu-id="56b19-119">Yes</span></span>|  
|<span data-ttu-id="56b19-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="56b19-120">Confidentiality</span></span>|<span data-ttu-id="56b19-121">Ano</span><span class="sxs-lookup"><span data-stu-id="56b19-121">Yes</span></span>|  
|<span data-ttu-id="56b19-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="56b19-122">Transport</span></span>|<span data-ttu-id="56b19-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="56b19-123">HTTP</span></span>|  
|<span data-ttu-id="56b19-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="56b19-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="56b19-125">Služba</span><span class="sxs-lookup"><span data-stu-id="56b19-125">Service</span></span>  
 <span data-ttu-id="56b19-126">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="56b19-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="56b19-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="56b19-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="56b19-128">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="56b19-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="56b19-129">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="56b19-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="56b19-130">Kód</span><span class="sxs-lookup"><span data-stu-id="56b19-130">Code</span></span>  
 <span data-ttu-id="56b19-131">Následující kód vytvoří koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="56b19-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="56b19-132">Služba vyžaduje certifikát ke svému ověření.</span><span class="sxs-lookup"><span data-stu-id="56b19-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="56b19-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="56b19-133">Configuration</span></span>  
 <span data-ttu-id="56b19-134">Následující konfigurace lze namísto kód k vytvoření stejnou službu.</span><span class="sxs-lookup"><span data-stu-id="56b19-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="56b19-135">Klient</span><span class="sxs-lookup"><span data-stu-id="56b19-135">Client</span></span>  
 <span data-ttu-id="56b19-136">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="56b19-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="56b19-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="56b19-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="56b19-138">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="56b19-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="56b19-139">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="56b19-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="56b19-140">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="56b19-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="56b19-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="56b19-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="56b19-142">Kód</span><span class="sxs-lookup"><span data-stu-id="56b19-142">Code</span></span>  
 <span data-ttu-id="56b19-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="56b19-143">The following code creates the client.</span></span> <span data-ttu-id="56b19-144">Režim zabezpečení je nastaven na zprávu, a typu pověření klienta nastavena na certifikát.</span><span class="sxs-lookup"><span data-stu-id="56b19-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="56b19-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="56b19-145">Configuration</span></span>  
 <span data-ttu-id="56b19-146">Následující nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="56b19-146">The following configures the client.</span></span> <span data-ttu-id="56b19-147">Klientský certifikát musí být určen pomocí [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="56b19-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="56b19-148">Certifikát služby je zadána také pomocí [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="56b19-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56b19-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="56b19-149">See Also</span></span>  
 [<span data-ttu-id="56b19-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="56b19-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="56b19-151">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="56b19-151">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)  
 [<span data-ttu-id="56b19-152">Postupy: vytvoření a nainstalujte dočasných certifikátů ve službě WCF pro zabezpečení přenosu během vývoje</span><span class="sxs-lookup"><span data-stu-id="56b19-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](http://go.microsoft.com/fwlink/?LinkId=244264)
