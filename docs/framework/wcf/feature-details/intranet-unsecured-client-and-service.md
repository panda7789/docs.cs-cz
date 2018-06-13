---
title: Nezabezpečený intranetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d08e8b5f9a22fc558af6f8f7c2ca3049e4a692ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492245"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="a1872-102">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="a1872-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="a1872-103">Následující obrázek znázorňuje jednoduchý vyvinuté tak, aby poskytují informace o zabezpečení privátní sítě pro aplikace WCF služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a1872-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="a1872-104">Zabezpečení není vyžadována, protože data je nízkou důležitostí, sítě musí být ze své podstaty zabezpečení nebo zabezpečení zajišťuje vrstvu pod infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="a1872-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 <span data-ttu-id="a1872-105">![Nezabezpečený intranetový klient a služba scénář](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="a1872-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="a1872-106">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a1872-106">Characteristic</span></span>|<span data-ttu-id="a1872-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1872-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a1872-108">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a1872-108">Security Mode</span></span>|<span data-ttu-id="a1872-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1872-109">None</span></span>|  
|<span data-ttu-id="a1872-110">Přenos</span><span class="sxs-lookup"><span data-stu-id="a1872-110">Transport</span></span>|<span data-ttu-id="a1872-111">TCP</span><span class="sxs-lookup"><span data-stu-id="a1872-111">TCP</span></span>|  
|<span data-ttu-id="a1872-112">Vazba</span><span class="sxs-lookup"><span data-stu-id="a1872-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="a1872-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="a1872-113">Interoperability</span></span>|<span data-ttu-id="a1872-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="a1872-114">WCF only</span></span>|  
|<span data-ttu-id="a1872-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="a1872-115">Authentication</span></span>|<span data-ttu-id="a1872-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1872-116">None</span></span>|  
|<span data-ttu-id="a1872-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="a1872-117">Integrity</span></span>|<span data-ttu-id="a1872-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1872-118">None</span></span>|  
|<span data-ttu-id="a1872-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="a1872-119">Confidentiality</span></span>|<span data-ttu-id="a1872-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1872-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="a1872-121">Služba</span><span class="sxs-lookup"><span data-stu-id="a1872-121">Service</span></span>  
 <span data-ttu-id="a1872-122">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="a1872-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a1872-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a1872-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="a1872-124">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a1872-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="a1872-125">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="a1872-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a1872-126">Kód</span><span class="sxs-lookup"><span data-stu-id="a1872-126">Code</span></span>  
 <span data-ttu-id="a1872-127">Následující kód ukazuje, jak vytvořit koncový bod se zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="a1872-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="a1872-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a1872-128">Configuration</span></span>  
 <span data-ttu-id="a1872-129">Následující kód nastaví stejný koncový bod pomocí konfigurace:</span><span class="sxs-lookup"><span data-stu-id="a1872-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="a1872-130">Klient</span><span class="sxs-lookup"><span data-stu-id="a1872-130">Client</span></span>  
 <span data-ttu-id="a1872-131">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="a1872-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a1872-132">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a1872-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="a1872-133">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="a1872-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="a1872-134">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="a1872-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a1872-135">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a1872-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a1872-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a1872-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="a1872-137">Kód</span><span class="sxs-lookup"><span data-stu-id="a1872-137">Code</span></span>  
 <span data-ttu-id="a1872-138">Následující kód ukazuje základní klienta WCF, který přistupuje k zabezpečená koncový bod pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="a1872-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="a1872-139">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a1872-139">Configuration</span></span>  
 <span data-ttu-id="a1872-140">Následující kód konfigurace platí pro klienta:</span><span class="sxs-lookup"><span data-stu-id="a1872-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1872-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1872-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="a1872-142">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a1872-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="a1872-143">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="a1872-143">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
