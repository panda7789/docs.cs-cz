---
title: Nezabezpečený intranetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
author: BrucePerlerMS
ms.openlocfilehash: e09f7c8483e1a3ca330bbee995c2d59f9005f207
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48265618"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="e26b6-102">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="e26b6-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="e26b6-103">Následující obrázek znázorňuje jednoduchý služby Windows Communication Foundation (WCF) vyvinuta poskytují informace o zabezpečené privátní sítě pro aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="e26b6-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="e26b6-104">Zabezpečení není povinné, protože data jsou s nízkou důležitostí, síť má být ze své podstaty bezpečné nebo poskytuje zabezpečení vrstvy pod infrastruktura WCF.</span><span class="sxs-lookup"><span data-stu-id="e26b6-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 <span data-ttu-id="e26b6-105">![Nezabezpečený intranetový klient a služba scénář](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="e26b6-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="e26b6-106">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e26b6-106">Characteristic</span></span>|<span data-ttu-id="e26b6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e26b6-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e26b6-108">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e26b6-108">Security Mode</span></span>|<span data-ttu-id="e26b6-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="e26b6-109">None</span></span>|  
|<span data-ttu-id="e26b6-110">Přenos</span><span class="sxs-lookup"><span data-stu-id="e26b6-110">Transport</span></span>|<span data-ttu-id="e26b6-111">TCP</span><span class="sxs-lookup"><span data-stu-id="e26b6-111">TCP</span></span>|  
|<span data-ttu-id="e26b6-112">Vazba</span><span class="sxs-lookup"><span data-stu-id="e26b6-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="e26b6-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="e26b6-113">Interoperability</span></span>|<span data-ttu-id="e26b6-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="e26b6-114">WCF only</span></span>|  
|<span data-ttu-id="e26b6-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="e26b6-115">Authentication</span></span>|<span data-ttu-id="e26b6-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e26b6-116">None</span></span>|  
|<span data-ttu-id="e26b6-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="e26b6-117">Integrity</span></span>|<span data-ttu-id="e26b6-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="e26b6-118">None</span></span>|  
|<span data-ttu-id="e26b6-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="e26b6-119">Confidentiality</span></span>|<span data-ttu-id="e26b6-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="e26b6-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="e26b6-121">Služba</span><span class="sxs-lookup"><span data-stu-id="e26b6-121">Service</span></span>  
 <span data-ttu-id="e26b6-122">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="e26b6-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e26b6-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="e26b6-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="e26b6-124">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e26b6-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="e26b6-125">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="e26b6-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e26b6-126">Kód</span><span class="sxs-lookup"><span data-stu-id="e26b6-126">Code</span></span>  
 <span data-ttu-id="e26b6-127">Následující kód ukazuje, jak vytvořit koncový bod se zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="e26b6-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="e26b6-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e26b6-128">Configuration</span></span>  
 <span data-ttu-id="e26b6-129">Následující kód nastaví stejný koncový bod pomocí konfigurace:</span><span class="sxs-lookup"><span data-stu-id="e26b6-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="e26b6-130">Klient</span><span class="sxs-lookup"><span data-stu-id="e26b6-130">Client</span></span>  
 <span data-ttu-id="e26b6-131">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="e26b6-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e26b6-132">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="e26b6-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="e26b6-133">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="e26b6-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="e26b6-134">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e26b6-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e26b6-135">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e26b6-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e26b6-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e26b6-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="e26b6-137">Kód</span><span class="sxs-lookup"><span data-stu-id="e26b6-137">Code</span></span>  
 <span data-ttu-id="e26b6-138">Následující kód ukazuje základní klienta WCF, který přistupuje k koncový bod zabezpečená pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="e26b6-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="e26b6-139">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e26b6-139">Configuration</span></span>  
 <span data-ttu-id="e26b6-140">Následující kód konfigurace platí pro klienta:</span><span class="sxs-lookup"><span data-stu-id="e26b6-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e26b6-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="e26b6-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="e26b6-142">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e26b6-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e26b6-143">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="e26b6-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
