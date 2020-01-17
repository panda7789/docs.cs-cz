---
title: Zabezpečení zprávy s klientem Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: d3c1661acf4d4aa2de8b6eca7015c74ba7f80af1
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212015"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="a2604-102">Zabezpečení zprávy s klientem Windows</span><span class="sxs-lookup"><span data-stu-id="a2604-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="a2604-103">Tento scénář ukazuje klienta služby Windows Communication Foundation (WCF) a server zabezpečený režimem zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="a2604-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="a2604-104">Klient a služba jsou ověřovány pomocí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a2604-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="a2604-105">![Zabezpečení zpráv pomocí klienta Windows](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="a2604-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="a2604-106">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="a2604-106">Characteristic</span></span>|<span data-ttu-id="a2604-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a2604-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a2604-108">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a2604-108">Security Mode</span></span>|<span data-ttu-id="a2604-109">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a2604-109">Message</span></span>|  
|<span data-ttu-id="a2604-110">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="a2604-110">Interoperability</span></span>|<span data-ttu-id="a2604-111">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="a2604-111">WCF Only</span></span>|  
|<span data-ttu-id="a2604-112">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="a2604-112">Authentication (Server)</span></span>|<span data-ttu-id="a2604-113">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="a2604-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="a2604-114">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="a2604-114">Authentication (Client)</span></span>|<span data-ttu-id="a2604-115">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="a2604-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="a2604-116">Integrita</span><span class="sxs-lookup"><span data-stu-id="a2604-116">Integrity</span></span>|<span data-ttu-id="a2604-117">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a2604-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="a2604-118">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="a2604-118">Confidentiality</span></span>|<span data-ttu-id="a2604-119">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a2604-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="a2604-120">Doprava</span><span class="sxs-lookup"><span data-stu-id="a2604-120">Transport</span></span>|<span data-ttu-id="a2604-121">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="a2604-121">NET.TCP</span></span>|  
|<span data-ttu-id="a2604-122">Vazba</span><span class="sxs-lookup"><span data-stu-id="a2604-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="a2604-123">Service</span><span class="sxs-lookup"><span data-stu-id="a2604-123">Service</span></span>  
 <span data-ttu-id="a2604-124">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="a2604-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a2604-125">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a2604-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="a2604-126">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a2604-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="a2604-127">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="a2604-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a2604-128">Kód</span><span class="sxs-lookup"><span data-stu-id="a2604-128">Code</span></span>  
 <span data-ttu-id="a2604-129">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k navázání zabezpečeného kontextu s počítačem s Windows.</span><span class="sxs-lookup"><span data-stu-id="a2604-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="a2604-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a2604-130">Configuration</span></span>  
 <span data-ttu-id="a2604-131">K nastavení služby je možné použít následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="a2604-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="a2604-132">Klient</span><span class="sxs-lookup"><span data-stu-id="a2604-132">Client</span></span>  
 <span data-ttu-id="a2604-133">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="a2604-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a2604-134">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a2604-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="a2604-135">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="a2604-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="a2604-136">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="a2604-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a2604-137">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="a2604-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a2604-138">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a2604-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="a2604-139">Kód</span><span class="sxs-lookup"><span data-stu-id="a2604-139">Code</span></span>  
 <span data-ttu-id="a2604-140">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="a2604-140">The following code creates a client.</span></span> <span data-ttu-id="a2604-141">Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="a2604-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="a2604-142">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a2604-142">Configuration</span></span>  
 <span data-ttu-id="a2604-143">Následující konfigurace se používá k nastavení vlastností klienta.</span><span class="sxs-lookup"><span data-stu-id="a2604-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2604-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2604-144">See also</span></span>

- [<span data-ttu-id="a2604-145">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a2604-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="a2604-146">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a2604-146">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
