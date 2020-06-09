---
title: Nezabezpečený intranetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 591f7db0f6b4e928a991961d3bc7c404f41028bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579277"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="42184-102">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="42184-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="42184-103">Následující ilustrace znázorňuje jednoduchou službu Windows Communication Foundation (WCF) vyvinutou pro poskytování informací o zabezpečené privátní síti pro aplikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="42184-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="42184-104">Zabezpečení není vyžadováno, protože data mají nízkou důležitost, očekává se, že síť bude podstatně zabezpečená, nebo že zabezpečení je zajištěno vrstvou pod infrastrukturou WCF.</span><span class="sxs-lookup"><span data-stu-id="42184-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Intranetový nezabezpečený scénář klienta a služby.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="42184-106">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="42184-106">Characteristic</span></span>|<span data-ttu-id="42184-107">Popis</span><span class="sxs-lookup"><span data-stu-id="42184-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="42184-108">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42184-108">Security Mode</span></span>|<span data-ttu-id="42184-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="42184-109">None</span></span>|  
|<span data-ttu-id="42184-110">Přenos</span><span class="sxs-lookup"><span data-stu-id="42184-110">Transport</span></span>|<span data-ttu-id="42184-111">TCP</span><span class="sxs-lookup"><span data-stu-id="42184-111">TCP</span></span>|  
|<span data-ttu-id="42184-112">Vazba</span><span class="sxs-lookup"><span data-stu-id="42184-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="42184-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="42184-113">Interoperability</span></span>|<span data-ttu-id="42184-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="42184-114">WCF only</span></span>|  
|<span data-ttu-id="42184-115">Authentication</span><span class="sxs-lookup"><span data-stu-id="42184-115">Authentication</span></span>|<span data-ttu-id="42184-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="42184-116">None</span></span>|  
|<span data-ttu-id="42184-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="42184-117">Integrity</span></span>|<span data-ttu-id="42184-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="42184-118">None</span></span>|  
|<span data-ttu-id="42184-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="42184-119">Confidentiality</span></span>|<span data-ttu-id="42184-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="42184-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="42184-121">Služba</span><span class="sxs-lookup"><span data-stu-id="42184-121">Service</span></span>  
 <span data-ttu-id="42184-122">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="42184-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="42184-123">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="42184-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="42184-124">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="42184-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="42184-125">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="42184-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="42184-126">Kód</span><span class="sxs-lookup"><span data-stu-id="42184-126">Code</span></span>  
 <span data-ttu-id="42184-127">Následující kód ukazuje, jak vytvořit koncový bod bez zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="42184-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="42184-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="42184-128">Configuration</span></span>  
 <span data-ttu-id="42184-129">Následující kód nastaví stejný koncový bod pomocí konfigurace:</span><span class="sxs-lookup"><span data-stu-id="42184-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="42184-130">Klient</span><span class="sxs-lookup"><span data-stu-id="42184-130">Client</span></span>  
 <span data-ttu-id="42184-131">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="42184-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="42184-132">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="42184-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="42184-133">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="42184-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="42184-134">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="42184-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="42184-135">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="42184-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="42184-136">Například:</span><span class="sxs-lookup"><span data-stu-id="42184-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="42184-137">Kód</span><span class="sxs-lookup"><span data-stu-id="42184-137">Code</span></span>  
 <span data-ttu-id="42184-138">Následující kód ukazuje základního klienta WCF, který přistupuje k nezabezpečenému koncovému bodu pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="42184-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="42184-139">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="42184-139">Configuration</span></span>  
 <span data-ttu-id="42184-140">Následující konfigurační kód platí pro klienta:</span><span class="sxs-lookup"><span data-stu-id="42184-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42184-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="42184-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="42184-142">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42184-142">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="42184-143">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="42184-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
