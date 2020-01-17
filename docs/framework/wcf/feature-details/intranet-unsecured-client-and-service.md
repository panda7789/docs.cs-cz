---
title: Nezabezpečený intranetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 1ffd0421195b0339ad966b661c229e5a5ebb94ec
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212090"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="a1215-102">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="a1215-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="a1215-103">Následující ilustrace znázorňuje jednoduchou službu Windows Communication Foundation (WCF) vyvinutou pro poskytování informací o zabezpečené privátní síti pro aplikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="a1215-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="a1215-104">Zabezpečení není vyžadováno, protože data mají nízkou důležitost, očekává se, že síť bude podstatně zabezpečená, nebo že zabezpečení je zajištěno vrstvou pod infrastrukturou WCF.</span><span class="sxs-lookup"><span data-stu-id="a1215-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Intranetový nezabezpečený scénář klienta a služby.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="a1215-106">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="a1215-106">Characteristic</span></span>|<span data-ttu-id="a1215-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1215-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a1215-108">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a1215-108">Security Mode</span></span>|<span data-ttu-id="a1215-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1215-109">None</span></span>|  
|<span data-ttu-id="a1215-110">Doprava</span><span class="sxs-lookup"><span data-stu-id="a1215-110">Transport</span></span>|<span data-ttu-id="a1215-111">TCP</span><span class="sxs-lookup"><span data-stu-id="a1215-111">TCP</span></span>|  
|<span data-ttu-id="a1215-112">Vazba</span><span class="sxs-lookup"><span data-stu-id="a1215-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="a1215-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="a1215-113">Interoperability</span></span>|<span data-ttu-id="a1215-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="a1215-114">WCF only</span></span>|  
|<span data-ttu-id="a1215-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="a1215-115">Authentication</span></span>|<span data-ttu-id="a1215-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1215-116">None</span></span>|  
|<span data-ttu-id="a1215-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="a1215-117">Integrity</span></span>|<span data-ttu-id="a1215-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1215-118">None</span></span>|  
|<span data-ttu-id="a1215-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="a1215-119">Confidentiality</span></span>|<span data-ttu-id="a1215-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1215-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="a1215-121">Service</span><span class="sxs-lookup"><span data-stu-id="a1215-121">Service</span></span>  
 <span data-ttu-id="a1215-122">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="a1215-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a1215-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a1215-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="a1215-124">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a1215-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="a1215-125">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="a1215-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a1215-126">Kód</span><span class="sxs-lookup"><span data-stu-id="a1215-126">Code</span></span>  
 <span data-ttu-id="a1215-127">Následující kód ukazuje, jak vytvořit koncový bod bez zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="a1215-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="a1215-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a1215-128">Configuration</span></span>  
 <span data-ttu-id="a1215-129">Následující kód nastaví stejný koncový bod pomocí konfigurace:</span><span class="sxs-lookup"><span data-stu-id="a1215-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="a1215-130">Klient</span><span class="sxs-lookup"><span data-stu-id="a1215-130">Client</span></span>  
 <span data-ttu-id="a1215-131">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="a1215-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a1215-132">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a1215-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="a1215-133">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="a1215-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="a1215-134">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="a1215-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a1215-135">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="a1215-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a1215-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a1215-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="a1215-137">Kód</span><span class="sxs-lookup"><span data-stu-id="a1215-137">Code</span></span>  
 <span data-ttu-id="a1215-138">Následující kód ukazuje základního klienta WCF, který přistupuje k nezabezpečenému koncovému bodu pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="a1215-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="a1215-139">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a1215-139">Configuration</span></span>  
 <span data-ttu-id="a1215-140">Následující konfigurační kód platí pro klienta:</span><span class="sxs-lookup"><span data-stu-id="a1215-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1215-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1215-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="a1215-142">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a1215-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="a1215-143">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a1215-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
