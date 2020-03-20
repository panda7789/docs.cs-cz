---
title: Nezabezpečený intranetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 2fa13a12a377cc16a95318367605d8b5d92769a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184687"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="8bc4b-102">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="8bc4b-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="8bc4b-103">Následující obrázek znázorňuje jednoduchou službu WCF (Windows Communication Foundation) vyvinutou za účelem poskytování informací o zabezpečené privátní síti aplikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="8bc4b-104">Zabezpečení není vyžadováno, protože data mají nízkou důležitost, očekává se, že síť bude ze své podstaty zabezpečená nebo zabezpečení poskytuje vrstva pod infrastrukturou WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Intranet nezabezpečené klienta a služby scénář.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="8bc4b-106">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="8bc4b-106">Characteristic</span></span>|<span data-ttu-id="8bc4b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8bc4b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8bc4b-108">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8bc4b-108">Security Mode</span></span>|<span data-ttu-id="8bc4b-109">Žádný</span><span class="sxs-lookup"><span data-stu-id="8bc4b-109">None</span></span>|  
|<span data-ttu-id="8bc4b-110">Přenos</span><span class="sxs-lookup"><span data-stu-id="8bc4b-110">Transport</span></span>|<span data-ttu-id="8bc4b-111">TCP</span><span class="sxs-lookup"><span data-stu-id="8bc4b-111">TCP</span></span>|  
|<span data-ttu-id="8bc4b-112">Vazba</span><span class="sxs-lookup"><span data-stu-id="8bc4b-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="8bc4b-113">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="8bc4b-113">Interoperability</span></span>|<span data-ttu-id="8bc4b-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="8bc4b-114">WCF only</span></span>|  
|<span data-ttu-id="8bc4b-115">Authentication</span><span class="sxs-lookup"><span data-stu-id="8bc4b-115">Authentication</span></span>|<span data-ttu-id="8bc4b-116">Žádný</span><span class="sxs-lookup"><span data-stu-id="8bc4b-116">None</span></span>|  
|<span data-ttu-id="8bc4b-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="8bc4b-117">Integrity</span></span>|<span data-ttu-id="8bc4b-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="8bc4b-118">None</span></span>|  
|<span data-ttu-id="8bc4b-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="8bc4b-119">Confidentiality</span></span>|<span data-ttu-id="8bc4b-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="8bc4b-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="8bc4b-121">Služba</span><span class="sxs-lookup"><span data-stu-id="8bc4b-121">Service</span></span>  
 <span data-ttu-id="8bc4b-122">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8bc4b-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="8bc4b-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="8bc4b-124">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="8bc4b-125">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8bc4b-126">kód</span><span class="sxs-lookup"><span data-stu-id="8bc4b-126">Code</span></span>  
 <span data-ttu-id="8bc4b-127">Následující kód ukazuje, jak vytvořit koncový bod bez zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="8bc4b-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="8bc4b-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8bc4b-128">Configuration</span></span>  
 <span data-ttu-id="8bc4b-129">Následující kód nastaví stejný koncový bod pomocí konfigurace:</span><span class="sxs-lookup"><span data-stu-id="8bc4b-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="8bc4b-130">Klient</span><span class="sxs-lookup"><span data-stu-id="8bc4b-130">Client</span></span>  
 <span data-ttu-id="8bc4b-131">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8bc4b-132">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="8bc4b-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="8bc4b-133">Vytvořte samostatného klienta pomocí kódu (a klientského kódu).</span><span class="sxs-lookup"><span data-stu-id="8bc4b-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="8bc4b-134">Vytvořte klienta, který nedefinuje žádné adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="8bc4b-135">Místo toho použijte konstruktor klienta, který bere název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="8bc4b-136">Například:</span><span class="sxs-lookup"><span data-stu-id="8bc4b-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="8bc4b-137">kód</span><span class="sxs-lookup"><span data-stu-id="8bc4b-137">Code</span></span>  
 <span data-ttu-id="8bc4b-138">Následující kód ukazuje základní wcf klienta, který přistupuje k nezabezpečené koncový bod pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="8bc4b-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="8bc4b-139">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8bc4b-139">Configuration</span></span>  
 <span data-ttu-id="8bc4b-140">Pro klienta platí následující konfigurační kód:</span><span class="sxs-lookup"><span data-stu-id="8bc4b-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bc4b-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bc4b-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="8bc4b-142">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8bc4b-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="8bc4b-143">[Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8bc4b-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
