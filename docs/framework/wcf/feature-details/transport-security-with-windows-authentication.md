---
title: Zabezpečení přenosu pomocí ověřování systému Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: d335cd47de68dccdbb6af7f402d1182fcd811a7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184319"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="4549b-102">Zabezpečení přenosu pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="4549b-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="4549b-103">Následující scénář ukazuje klienta a služby WCF (Windows Communication Foundation) zabezpečené zabezpečením systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4549b-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="4549b-104">Další informace o programování naleznete v [tématu How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="4549b-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="4549b-105">Webová služba intranet zobrazuje informace o lidských zdrojích.</span><span class="sxs-lookup"><span data-stu-id="4549b-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="4549b-106">Klient je aplikace Windows Form.</span><span class="sxs-lookup"><span data-stu-id="4549b-106">The client is a Windows Form application.</span></span> <span data-ttu-id="4549b-107">Aplikace je nasazena v doméně s řadičem Kerberos, který doménu zabezpečuje.</span><span class="sxs-lookup"><span data-stu-id="4549b-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Zabezpečení přenosu pomocí ověřování systému Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="4549b-109">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="4549b-109">Characteristic</span></span>|<span data-ttu-id="4549b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4549b-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4549b-111">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4549b-111">Security Mode</span></span>|<span data-ttu-id="4549b-112">Přenos</span><span class="sxs-lookup"><span data-stu-id="4549b-112">Transport</span></span>|  
|<span data-ttu-id="4549b-113">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="4549b-113">Interoperability</span></span>|<span data-ttu-id="4549b-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="4549b-114">WCF only</span></span>|  
|<span data-ttu-id="4549b-115">Ověřování (server)</span><span class="sxs-lookup"><span data-stu-id="4549b-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="4549b-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="4549b-116">Authentication (Client)</span></span>|<span data-ttu-id="4549b-117">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="4549b-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="4549b-118">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="4549b-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="4549b-119">Integrita</span><span class="sxs-lookup"><span data-stu-id="4549b-119">Integrity</span></span>|<span data-ttu-id="4549b-120">Ano</span><span class="sxs-lookup"><span data-stu-id="4549b-120">Yes</span></span>|  
|<span data-ttu-id="4549b-121">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="4549b-121">Confidentiality</span></span>|<span data-ttu-id="4549b-122">Ano</span><span class="sxs-lookup"><span data-stu-id="4549b-122">Yes</span></span>|  
|<span data-ttu-id="4549b-123">Přenos</span><span class="sxs-lookup"><span data-stu-id="4549b-123">Transport</span></span>|<span data-ttu-id="4549b-124">Čisté. Tcp</span><span class="sxs-lookup"><span data-stu-id="4549b-124">NET.TCP</span></span>|  
|<span data-ttu-id="4549b-125">Vazba</span><span class="sxs-lookup"><span data-stu-id="4549b-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="4549b-126">Služba</span><span class="sxs-lookup"><span data-stu-id="4549b-126">Service</span></span>  
 <span data-ttu-id="4549b-127">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="4549b-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4549b-128">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="4549b-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="4549b-129">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4549b-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="4549b-130">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="4549b-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4549b-131">kód</span><span class="sxs-lookup"><span data-stu-id="4549b-131">Code</span></span>  
 <span data-ttu-id="4549b-132">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4549b-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="4549b-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="4549b-133">Configuration</span></span>  
 <span data-ttu-id="4549b-134">K nastavení koncového bodu služby lze místo kódu použít následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="4549b-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="4549b-135">Klient</span><span class="sxs-lookup"><span data-stu-id="4549b-135">Client</span></span>  
 <span data-ttu-id="4549b-136">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="4549b-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4549b-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="4549b-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="4549b-138">Vytvořte samostatného klienta pomocí kódu (a klientského kódu).</span><span class="sxs-lookup"><span data-stu-id="4549b-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="4549b-139">Vytvořte klienta, který nedefinuje žádné adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4549b-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="4549b-140">Místo toho použijte konstruktor klienta, který bere název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="4549b-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="4549b-141">Například:</span><span class="sxs-lookup"><span data-stu-id="4549b-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="4549b-142">kód</span><span class="sxs-lookup"><span data-stu-id="4549b-142">Code</span></span>  
 <span data-ttu-id="4549b-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="4549b-143">The following code creates the client.</span></span> <span data-ttu-id="4549b-144">Vazba je nakonfigurována tak, aby používala zabezpečení režimu přenosu s přenosem TCP s typem pověření klienta nastaveným na systém Windows.</span><span class="sxs-lookup"><span data-stu-id="4549b-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="4549b-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="4549b-145">Configuration</span></span>  
 <span data-ttu-id="4549b-146">Následující konfiguraci lze použít namísto kódu k vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="4549b-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4549b-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="4549b-147">See also</span></span>

- [<span data-ttu-id="4549b-148">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4549b-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="4549b-149">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="4549b-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="4549b-150">[Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4549b-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
