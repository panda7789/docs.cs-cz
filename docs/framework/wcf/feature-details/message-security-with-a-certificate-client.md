---
title: Zabezpečení zpráv pomocí klientských certifikátů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 1393879c58609c501da5b2d413073328bee6d05d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785978"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="9b306-102">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="9b306-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="9b306-103">Následující scénář ukazuje klienta Windows Communication Foundation (WCF) a služby Zabezpečené používají režim zabezpečených zpráv.</span><span class="sxs-lookup"><span data-stu-id="9b306-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="9b306-104">Klient a služba se ověří pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9b306-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="9b306-105">Další informace najdete v tématu [zabezpečení distribuované aplikace](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="9b306-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Snímek obrazovky zobrazující klienta pomocí certifikátu.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="9b306-107">Ukázková aplikace, najdete v části [certifikát zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="9b306-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="9b306-108">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="9b306-108">Characteristic</span></span>|<span data-ttu-id="9b306-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9b306-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9b306-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b306-110">Security Mode</span></span>|<span data-ttu-id="9b306-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9b306-111">Message</span></span>|  
|<span data-ttu-id="9b306-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="9b306-112">Interoperability</span></span>|<span data-ttu-id="9b306-113">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="9b306-113">WCF only</span></span>|  
|<span data-ttu-id="9b306-114">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="9b306-114">Authentication (Server)</span></span>|<span data-ttu-id="9b306-115">Pomocí certifikátu služby</span><span class="sxs-lookup"><span data-stu-id="9b306-115">Using service certificate</span></span>|  
|<span data-ttu-id="9b306-116">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="9b306-116">Authentication (Client)</span></span>|<span data-ttu-id="9b306-117">Pomocí klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="9b306-117">Using client certificate</span></span>|  
|<span data-ttu-id="9b306-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="9b306-118">Integrity</span></span>|<span data-ttu-id="9b306-119">Ano</span><span class="sxs-lookup"><span data-stu-id="9b306-119">Yes</span></span>|  
|<span data-ttu-id="9b306-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="9b306-120">Confidentiality</span></span>|<span data-ttu-id="9b306-121">Ano</span><span class="sxs-lookup"><span data-stu-id="9b306-121">Yes</span></span>|  
|<span data-ttu-id="9b306-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="9b306-122">Transport</span></span>|<span data-ttu-id="9b306-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="9b306-123">HTTP</span></span>|  
|<span data-ttu-id="9b306-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="9b306-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="9b306-125">Služba</span><span class="sxs-lookup"><span data-stu-id="9b306-125">Service</span></span>  
 <span data-ttu-id="9b306-126">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="9b306-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9b306-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="9b306-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="9b306-128">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9b306-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="9b306-129">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="9b306-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9b306-130">Kód</span><span class="sxs-lookup"><span data-stu-id="9b306-130">Code</span></span>  
 <span data-ttu-id="9b306-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který se používá k navázání zabezpečené kontextu zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="9b306-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="9b306-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9b306-132">Configuration</span></span>  
 <span data-ttu-id="9b306-133">Následující konfigurace je možné použít místo kódu.</span><span class="sxs-lookup"><span data-stu-id="9b306-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="9b306-134">Klient</span><span class="sxs-lookup"><span data-stu-id="9b306-134">Client</span></span>  
 <span data-ttu-id="9b306-135">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="9b306-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9b306-136">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="9b306-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="9b306-137">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="9b306-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="9b306-138">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="9b306-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="9b306-139">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9b306-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="9b306-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9b306-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="9b306-141">Kód</span><span class="sxs-lookup"><span data-stu-id="9b306-141">Code</span></span>  
 <span data-ttu-id="9b306-142">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="9b306-142">The following code creates the client.</span></span> <span data-ttu-id="9b306-143">Vazba má režim zabezpečení zpráv a typu pověření klienta je nastavena na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="9b306-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="9b306-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9b306-144">Configuration</span></span>  
 <span data-ttu-id="9b306-145">Určuje následující konfiguraci klientského certifikátu pomocí chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9b306-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="9b306-146">Další informace o certifikátech najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9b306-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="9b306-147">Kód také pomocí <`identity`> element k určení systému DNS (Domain Name) identity očekávané serveru.</span><span class="sxs-lookup"><span data-stu-id="9b306-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="9b306-148">Další informace o identitě najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9b306-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b306-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b306-149">See also</span></span>

- [<span data-ttu-id="9b306-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b306-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="9b306-151">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="9b306-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9b306-152">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="9b306-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9b306-153">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="9b306-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
