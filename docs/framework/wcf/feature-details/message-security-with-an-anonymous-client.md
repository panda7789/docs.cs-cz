---
title: "Zabezpečení zpráv s anonymním klientem"
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
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: edf1dd36fe8c0f3e6c1ae8087d1bacbc00cf307a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="599f1-102">Zabezpečení zpráv s anonymním klientem</span><span class="sxs-lookup"><span data-stu-id="599f1-102">Message Security with an Anonymous Client</span></span>
<span data-ttu-id="599f1-103">Následující příklad ukazuje klienta a služby zabezpečené [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="599f1-103">The following scenario shows a client and service secured by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message security.</span></span> <span data-ttu-id="599f1-104">Návrh cílem je používat zabezpečení zpráv, nikoli zabezpečení přenosu, tak, aby v budoucnu může podporovat model bohatší založené na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="599f1-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="599f1-105">pomocí bohaté deklarace pro ověřování, najdete v tématu [správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="599f1-105"> using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="599f1-106">Ukázkovou aplikaci, najdete v části [zpráva zabezpečení anonymní](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="599f1-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>  
  
 <span data-ttu-id="599f1-107">![Zpráva zabezpečení s klientem anynymous](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="599f1-107">![Message security with an anynymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>  
  
|<span data-ttu-id="599f1-108">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="599f1-108">Characteristic</span></span>|<span data-ttu-id="599f1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="599f1-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="599f1-110">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="599f1-110">Security Mode</span></span>|<span data-ttu-id="599f1-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="599f1-111">Message</span></span>|  
|<span data-ttu-id="599f1-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="599f1-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="599f1-113">pouze</span><span class="sxs-lookup"><span data-stu-id="599f1-113"> only</span></span>|  
|<span data-ttu-id="599f1-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="599f1-114">Authentication (Server)</span></span>|<span data-ttu-id="599f1-115">Počáteční vyjednávání vyžaduje ověřování serveru, ale není ověření klienta</span><span class="sxs-lookup"><span data-stu-id="599f1-115">Initial negotiation requires server authentication, but not client authentication</span></span>|  
|<span data-ttu-id="599f1-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="599f1-116">Authentication (Client)</span></span>|<span data-ttu-id="599f1-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="599f1-117">None</span></span>|  
|<span data-ttu-id="599f1-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="599f1-118">Integrity</span></span>|<span data-ttu-id="599f1-119">Ano, kontextu sdílené zabezpečení</span><span class="sxs-lookup"><span data-stu-id="599f1-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="599f1-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="599f1-120">Confidentiality</span></span>|<span data-ttu-id="599f1-121">Ano, kontextu sdílené zabezpečení</span><span class="sxs-lookup"><span data-stu-id="599f1-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="599f1-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="599f1-122">Transport</span></span>|<span data-ttu-id="599f1-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="599f1-123">HTTP</span></span>|  
  
## <a name="service"></a><span data-ttu-id="599f1-124">Služba</span><span class="sxs-lookup"><span data-stu-id="599f1-124">Service</span></span>  
 <span data-ttu-id="599f1-125">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="599f1-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="599f1-126">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="599f1-126">Do one of the following:</span></span>  
  
-   <span data-ttu-id="599f1-127">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="599f1-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="599f1-128">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="599f1-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="599f1-129">Kód</span><span class="sxs-lookup"><span data-stu-id="599f1-129">Code</span></span>  
 <span data-ttu-id="599f1-130">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="599f1-130">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a><span data-ttu-id="599f1-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="599f1-131">Configuration</span></span>  
 <span data-ttu-id="599f1-132">Následující konfigurace můžete použít místo kód.</span><span class="sxs-lookup"><span data-stu-id="599f1-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="599f1-133">Element chování služby slouží k určení certifikát, který se používá k ověření služby klienta.</span><span class="sxs-lookup"><span data-stu-id="599f1-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="599f1-134">Service element musíte zadat chování pomocí `behaviorConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="599f1-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="599f1-135">Element vazby Určuje, že je typu pověření klienta `None`, umožňuje anonymní klientům používat službu.</span><span class="sxs-lookup"><span data-stu-id="599f1-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="599f1-136">Klient</span><span class="sxs-lookup"><span data-stu-id="599f1-136">Client</span></span>  
 <span data-ttu-id="599f1-137">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="599f1-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="599f1-138">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="599f1-138">Do one of the following:</span></span>  
  
-   <span data-ttu-id="599f1-139">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="599f1-139">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="599f1-140">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="599f1-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="599f1-141">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="599f1-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="599f1-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="599f1-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="599f1-143">Kód</span><span class="sxs-lookup"><span data-stu-id="599f1-143">Code</span></span>  
 <span data-ttu-id="599f1-144">Následující kód vytvoří instanci klienta.</span><span class="sxs-lookup"><span data-stu-id="599f1-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="599f1-145">Vazba používá režim zabezpečení zpráv a typu pověření klienta je nastavena na hodnotu none.</span><span class="sxs-lookup"><span data-stu-id="599f1-145">The binding uses message mode security, and the client credential type is set to none.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a><span data-ttu-id="599f1-146">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="599f1-146">Configuration</span></span>  
 <span data-ttu-id="599f1-147">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="599f1-147">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_ICalculator"   
        contract="ICalculator"  
        name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="599f1-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="599f1-148">See Also</span></span>  
 [<span data-ttu-id="599f1-149">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="599f1-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="599f1-150">Zabezpečení distribuované aplikace</span><span class="sxs-lookup"><span data-stu-id="599f1-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="599f1-151">Zabezpečení zpráv anonymní</span><span class="sxs-lookup"><span data-stu-id="599f1-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [<span data-ttu-id="599f1-152">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="599f1-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="599f1-153">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="599f1-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
