---
title: "Zabezpečení zprávy s klientem Windows"
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
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c480706fee27e7023eae5b493b0ca007b4757e97
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="41de3-102">Zabezpečení zprávy s klientem Windows</span><span class="sxs-lookup"><span data-stu-id="41de3-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="41de3-103">Tento scénář popisuje, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientem a serverem zabezpečené pomocí režim zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="41de3-103">This scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and server secured by message security mode.</span></span> <span data-ttu-id="41de3-104">Klient a služba, se ověřují pomocí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="41de3-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="41de3-105">![Zpráva zabezpečení s klientem Windows](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="41de3-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="41de3-106">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="41de3-106">Characteristic</span></span>|<span data-ttu-id="41de3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="41de3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="41de3-108">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="41de3-108">Security Mode</span></span>|<span data-ttu-id="41de3-109">Zpráva</span><span class="sxs-lookup"><span data-stu-id="41de3-109">Message</span></span>|  
|<span data-ttu-id="41de3-110">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="41de3-110">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="41de3-111">Pouze</span><span class="sxs-lookup"><span data-stu-id="41de3-111"> Only</span></span>|  
|<span data-ttu-id="41de3-112">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="41de3-112">Authentication (Server)</span></span>|<span data-ttu-id="41de3-113">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="41de3-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="41de3-114">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="41de3-114">Authentication (Client)</span></span>|<span data-ttu-id="41de3-115">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="41de3-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="41de3-116">Integrita</span><span class="sxs-lookup"><span data-stu-id="41de3-116">Integrity</span></span>|<span data-ttu-id="41de3-117">Ano, kontextu sdílené zabezpečení</span><span class="sxs-lookup"><span data-stu-id="41de3-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="41de3-118">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="41de3-118">Confidentiality</span></span>|<span data-ttu-id="41de3-119">Ano, kontextu sdílené zabezpečení</span><span class="sxs-lookup"><span data-stu-id="41de3-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="41de3-120">Přenos</span><span class="sxs-lookup"><span data-stu-id="41de3-120">Transport</span></span>|<span data-ttu-id="41de3-121">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="41de3-121">NET.TCP</span></span>|  
|<span data-ttu-id="41de3-122">Vazba</span><span class="sxs-lookup"><span data-stu-id="41de3-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="41de3-123">Služba</span><span class="sxs-lookup"><span data-stu-id="41de3-123">Service</span></span>  
 <span data-ttu-id="41de3-124">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="41de3-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="41de3-125">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="41de3-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="41de3-126">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="41de3-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="41de3-127">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="41de3-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="41de3-128">Kód</span><span class="sxs-lookup"><span data-stu-id="41de3-128">Code</span></span>  
 <span data-ttu-id="41de3-129">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k navázání zabezpečeného kontext s počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="41de3-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="41de3-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="41de3-130">Configuration</span></span>  
 <span data-ttu-id="41de3-131">Místo kód nastavit službu lze použít následující konfigurace:</span><span class="sxs-lookup"><span data-stu-id="41de3-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="41de3-132">Klient</span><span class="sxs-lookup"><span data-stu-id="41de3-132">Client</span></span>  
 <span data-ttu-id="41de3-133">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="41de3-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="41de3-134">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="41de3-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="41de3-135">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="41de3-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="41de3-136">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="41de3-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="41de3-137">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="41de3-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="41de3-138">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41de3-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="41de3-139">Kód</span><span class="sxs-lookup"><span data-stu-id="41de3-139">Code</span></span>  
 <span data-ttu-id="41de3-140">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="41de3-140">The following code creates a client.</span></span> <span data-ttu-id="41de3-141">Vazba je režim zabezpečení zpráv a typu pověření klienta nastavena na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="41de3-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="41de3-142">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="41de3-142">Configuration</span></span>  
 <span data-ttu-id="41de3-143">Následující konfigurace slouží k nastavení vlastnosti klienta.</span><span class="sxs-lookup"><span data-stu-id="41de3-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"   
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">          
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41de3-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="41de3-144">See Also</span></span>  
 [<span data-ttu-id="41de3-145">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="41de3-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="41de3-146">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="41de3-146">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
