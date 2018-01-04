---
title: "Zabezpečení přenosu pomocí ověřování systému Windows"
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
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4f5f81617a8962eeb8748e2c5c35ea34f7a1705f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="11713-102">Zabezpečení přenosu pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="11713-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="11713-103">Následující scénář ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby Zabezpečené zabezpečení systému Windows.</span><span class="sxs-lookup"><span data-stu-id="11713-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured by Windows security.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="11713-104">programování, najdete v části [postupy: zabezpečení služby s pověřeními Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="11713-104"> programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="11713-105">Intranet webové služby zobrazí informace lidských zdrojů.</span><span class="sxs-lookup"><span data-stu-id="11713-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="11713-106">Klient je aplikace formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="11713-106">The client is a Windows Form application.</span></span> <span data-ttu-id="11713-107">Aplikace je nasazená v doméně pomocí protokolu Kerberos řadiče domény zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="11713-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="11713-108">![Zabezpečení pomocí ověřování systému Windows Transport](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="11713-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="11713-109">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="11713-109">Characteristic</span></span>|<span data-ttu-id="11713-110">Popis</span><span class="sxs-lookup"><span data-stu-id="11713-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="11713-111">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="11713-111">Security Mode</span></span>|<span data-ttu-id="11713-112">Přenos</span><span class="sxs-lookup"><span data-stu-id="11713-112">Transport</span></span>|  
|<span data-ttu-id="11713-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="11713-113">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="11713-114">pouze</span><span class="sxs-lookup"><span data-stu-id="11713-114"> only</span></span>|  
|<span data-ttu-id="11713-115">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="11713-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="11713-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="11713-116">Authentication (Client)</span></span>|<span data-ttu-id="11713-117">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="11713-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="11713-118">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="11713-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="11713-119">Integrita</span><span class="sxs-lookup"><span data-stu-id="11713-119">Integrity</span></span>|<span data-ttu-id="11713-120">Ano</span><span class="sxs-lookup"><span data-stu-id="11713-120">Yes</span></span>|  
|<span data-ttu-id="11713-121">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="11713-121">Confidentiality</span></span>|<span data-ttu-id="11713-122">Ano</span><span class="sxs-lookup"><span data-stu-id="11713-122">Yes</span></span>|  
|<span data-ttu-id="11713-123">Přenos</span><span class="sxs-lookup"><span data-stu-id="11713-123">Transport</span></span>|<span data-ttu-id="11713-124">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="11713-124">NET.TCP</span></span>|  
|<span data-ttu-id="11713-125">Vazba</span><span class="sxs-lookup"><span data-stu-id="11713-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="11713-126">Služba</span><span class="sxs-lookup"><span data-stu-id="11713-126">Service</span></span>  
 <span data-ttu-id="11713-127">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="11713-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="11713-128">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="11713-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="11713-129">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="11713-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="11713-130">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="11713-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="11713-131">Kód</span><span class="sxs-lookup"><span data-stu-id="11713-131">Code</span></span>  
 <span data-ttu-id="11713-132">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení systému Windows.</span><span class="sxs-lookup"><span data-stu-id="11713-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="11713-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="11713-133">Configuration</span></span>  
 <span data-ttu-id="11713-134">Místo kód nastavit koncový bod služby lze použít následující konfigurace:</span><span class="sxs-lookup"><span data-stu-id="11713-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="11713-135">Klient</span><span class="sxs-lookup"><span data-stu-id="11713-135">Client</span></span>  
 <span data-ttu-id="11713-136">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="11713-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="11713-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="11713-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="11713-138">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="11713-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="11713-139">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="11713-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="11713-140">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="11713-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="11713-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="11713-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="11713-142">Kód</span><span class="sxs-lookup"><span data-stu-id="11713-142">Code</span></span>  
 <span data-ttu-id="11713-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="11713-143">The following code creates the client.</span></span> <span data-ttu-id="11713-144">Vazba je nakonfigurována pro použití režimu zabezpečení přenosu, s přenos TCP, s typu pověření klienta, který je nastaven na hodnotu Windows.</span><span class="sxs-lookup"><span data-stu-id="11713-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="11713-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="11713-145">Configuration</span></span>  
 <span data-ttu-id="11713-146">Následující konfigurace můžete použít místo kód pro vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="11713-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11713-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="11713-147">See Also</span></span>  
 [<span data-ttu-id="11713-148">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="11713-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="11713-149">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="11713-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="11713-150">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="11713-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
