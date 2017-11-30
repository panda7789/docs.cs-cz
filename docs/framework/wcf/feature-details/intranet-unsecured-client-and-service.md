---
title: "Nezabezpečený intranetový klient a služba"
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
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9a3faa27d54f2aa67cd974bc1827d71163e411b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="2a142-102">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="2a142-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="2a142-103">Následující obrázek znázorňuje jednoduchý [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby vyvinuté tak, aby poskytují informace o do zabezpečené privátní sítě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="2a142-103">The following illustration depicts a simple [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service developed to provide information on a secure private network to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="2a142-104">Zabezpečení není vyžadována, protože data je nízkou důležitostí, sítě musí být ze své podstaty zabezpečené nebo zajišťuje vrstvu zabezpečení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="2a142-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure.</span></span>  
  
 <span data-ttu-id="2a142-105">![Nezabezpečený intranetový klient a služba scénář](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="2a142-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="2a142-106">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2a142-106">Characteristic</span></span>|<span data-ttu-id="2a142-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2a142-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2a142-108">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2a142-108">Security Mode</span></span>|<span data-ttu-id="2a142-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a142-109">None</span></span>|  
|<span data-ttu-id="2a142-110">Přenos</span><span class="sxs-lookup"><span data-stu-id="2a142-110">Transport</span></span>|<span data-ttu-id="2a142-111">TCP</span><span class="sxs-lookup"><span data-stu-id="2a142-111">TCP</span></span>|  
|<span data-ttu-id="2a142-112">Vazba</span><span class="sxs-lookup"><span data-stu-id="2a142-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="2a142-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="2a142-113">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2a142-114">pouze</span><span class="sxs-lookup"><span data-stu-id="2a142-114"> only</span></span>|  
|<span data-ttu-id="2a142-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="2a142-115">Authentication</span></span>|<span data-ttu-id="2a142-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a142-116">None</span></span>|  
|<span data-ttu-id="2a142-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="2a142-117">Integrity</span></span>|<span data-ttu-id="2a142-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a142-118">None</span></span>|  
|<span data-ttu-id="2a142-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="2a142-119">Confidentiality</span></span>|<span data-ttu-id="2a142-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a142-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="2a142-121">Služba</span><span class="sxs-lookup"><span data-stu-id="2a142-121">Service</span></span>  
 <span data-ttu-id="2a142-122">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="2a142-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2a142-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="2a142-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="2a142-124">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="2a142-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="2a142-125">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="2a142-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2a142-126">Kód</span><span class="sxs-lookup"><span data-stu-id="2a142-126">Code</span></span>  
 <span data-ttu-id="2a142-127">Následující kód ukazuje, jak vytvořit koncový bod se zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="2a142-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="2a142-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2a142-128">Configuration</span></span>  
 <span data-ttu-id="2a142-129">Následující kód nastaví stejný koncový bod pomocí konfigurace:</span><span class="sxs-lookup"><span data-stu-id="2a142-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="2a142-130">Klient</span><span class="sxs-lookup"><span data-stu-id="2a142-130">Client</span></span>  
 <span data-ttu-id="2a142-131">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="2a142-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2a142-132">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="2a142-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="2a142-133">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="2a142-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="2a142-134">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="2a142-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="2a142-135">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2a142-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="2a142-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2a142-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="2a142-137">Kód</span><span class="sxs-lookup"><span data-stu-id="2a142-137">Code</span></span>  
 <span data-ttu-id="2a142-138">Následující kód ukazuje základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, který přistupuje k zabezpečená koncový bod pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="2a142-138">The following code shows a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="2a142-139">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2a142-139">Configuration</span></span>  
 <span data-ttu-id="2a142-140">Následující kód konfigurace platí pro klienta:</span><span class="sxs-lookup"><span data-stu-id="2a142-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a142-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a142-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="2a142-142">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2a142-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="2a142-143">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="2a142-143">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
