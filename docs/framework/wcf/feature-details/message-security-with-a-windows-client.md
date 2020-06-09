---
title: Zabezpečení zprávy s klientem Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: dcb311523c6ec41b62f6e69fe6bc7635b9d49708
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595229"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="67660-102">Zabezpečení zprávy s klientem Windows</span><span class="sxs-lookup"><span data-stu-id="67660-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="67660-103">Tento scénář ukazuje klienta služby Windows Communication Foundation (WCF) a server zabezpečený režimem zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="67660-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="67660-104">Klient a služba jsou ověřovány pomocí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="67660-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="67660-105">![Zabezpečení zpráv pomocí klienta Windows](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="67660-105">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="67660-106">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="67660-106">Characteristic</span></span>|<span data-ttu-id="67660-107">Popis</span><span class="sxs-lookup"><span data-stu-id="67660-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="67660-108">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67660-108">Security Mode</span></span>|<span data-ttu-id="67660-109">Zpráva</span><span class="sxs-lookup"><span data-stu-id="67660-109">Message</span></span>|  
|<span data-ttu-id="67660-110">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="67660-110">Interoperability</span></span>|<span data-ttu-id="67660-111">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="67660-111">WCF Only</span></span>|  
|<span data-ttu-id="67660-112">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="67660-112">Authentication (Server)</span></span>|<span data-ttu-id="67660-113">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="67660-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="67660-114">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="67660-114">Authentication (Client)</span></span>|<span data-ttu-id="67660-115">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="67660-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="67660-116">Integrita</span><span class="sxs-lookup"><span data-stu-id="67660-116">Integrity</span></span>|<span data-ttu-id="67660-117">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67660-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="67660-118">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="67660-118">Confidentiality</span></span>|<span data-ttu-id="67660-119">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67660-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="67660-120">Přenos</span><span class="sxs-lookup"><span data-stu-id="67660-120">Transport</span></span>|<span data-ttu-id="67660-121">Pohyby. PROTOKOLU</span><span class="sxs-lookup"><span data-stu-id="67660-121">NET.TCP</span></span>|  
|<span data-ttu-id="67660-122">Vazba</span><span class="sxs-lookup"><span data-stu-id="67660-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="67660-123">Služba</span><span class="sxs-lookup"><span data-stu-id="67660-123">Service</span></span>  
 <span data-ttu-id="67660-124">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="67660-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="67660-125">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="67660-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="67660-126">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="67660-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="67660-127">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="67660-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="67660-128">Kód</span><span class="sxs-lookup"><span data-stu-id="67660-128">Code</span></span>  
 <span data-ttu-id="67660-129">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k navázání zabezpečeného kontextu s počítačem s Windows.</span><span class="sxs-lookup"><span data-stu-id="67660-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="67660-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="67660-130">Configuration</span></span>  
 <span data-ttu-id="67660-131">K nastavení služby je možné použít následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="67660-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="67660-132">Klient</span><span class="sxs-lookup"><span data-stu-id="67660-132">Client</span></span>  
 <span data-ttu-id="67660-133">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="67660-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="67660-134">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="67660-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="67660-135">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="67660-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="67660-136">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="67660-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="67660-137">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="67660-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="67660-138">Například:</span><span class="sxs-lookup"><span data-stu-id="67660-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="67660-139">Kód</span><span class="sxs-lookup"><span data-stu-id="67660-139">Code</span></span>  
 <span data-ttu-id="67660-140">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="67660-140">The following code creates a client.</span></span> <span data-ttu-id="67660-141">Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na hodnotu `Windows` .</span><span class="sxs-lookup"><span data-stu-id="67660-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="67660-142">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="67660-142">Configuration</span></span>  
 <span data-ttu-id="67660-143">Následující konfigurace se používá k nastavení vlastností klienta.</span><span class="sxs-lookup"><span data-stu-id="67660-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67660-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="67660-144">See also</span></span>

- [<span data-ttu-id="67660-145">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67660-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="67660-146">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="67660-146">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
