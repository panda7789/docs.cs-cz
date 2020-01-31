---
title: Zabezpečení přenosu pomocí ověřování systému Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 6392ea0f17596406a8671a039bd78777d9e11e42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742644"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="16cf2-102">Zabezpečení přenosu pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="16cf2-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="16cf2-103">V následujícím scénáři se zobrazuje klient a služba Windows Communication Foundation (WCF) zabezpečené zabezpečením systému Windows.</span><span class="sxs-lookup"><span data-stu-id="16cf2-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="16cf2-104">Další informace o programování najdete v tématu [Postup: zabezpečení služby pomocí pověření systému Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="16cf2-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="16cf2-105">Intranetová webová služba zobrazuje informace o lidských zdrojích.</span><span class="sxs-lookup"><span data-stu-id="16cf2-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="16cf2-106">Klient je aplikace formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="16cf2-106">The client is a Windows Form application.</span></span> <span data-ttu-id="16cf2-107">Aplikace je nasazena v doméně s řadičem protokolu Kerberos zabezpečení domény.</span><span class="sxs-lookup"><span data-stu-id="16cf2-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Zabezpečení přenosu s ověřováním systému Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="16cf2-109">Charakteristiku</span><span class="sxs-lookup"><span data-stu-id="16cf2-109">Characteristic</span></span>|<span data-ttu-id="16cf2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="16cf2-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="16cf2-111">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="16cf2-111">Security Mode</span></span>|<span data-ttu-id="16cf2-112">Přepravu</span><span class="sxs-lookup"><span data-stu-id="16cf2-112">Transport</span></span>|  
|<span data-ttu-id="16cf2-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="16cf2-113">Interoperability</span></span>|<span data-ttu-id="16cf2-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="16cf2-114">WCF only</span></span>|  
|<span data-ttu-id="16cf2-115">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="16cf2-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="16cf2-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="16cf2-116">Authentication (Client)</span></span>|<span data-ttu-id="16cf2-117">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="16cf2-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="16cf2-118">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="16cf2-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="16cf2-119">Způsobilost</span><span class="sxs-lookup"><span data-stu-id="16cf2-119">Integrity</span></span>|<span data-ttu-id="16cf2-120">Ano</span><span class="sxs-lookup"><span data-stu-id="16cf2-120">Yes</span></span>|  
|<span data-ttu-id="16cf2-121">Chovávat</span><span class="sxs-lookup"><span data-stu-id="16cf2-121">Confidentiality</span></span>|<span data-ttu-id="16cf2-122">Ano</span><span class="sxs-lookup"><span data-stu-id="16cf2-122">Yes</span></span>|  
|<span data-ttu-id="16cf2-123">Přepravu</span><span class="sxs-lookup"><span data-stu-id="16cf2-123">Transport</span></span>|<span data-ttu-id="16cf2-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="16cf2-124">NET.TCP</span></span>|  
|<span data-ttu-id="16cf2-125">Vazba</span><span class="sxs-lookup"><span data-stu-id="16cf2-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="16cf2-126">Service</span><span class="sxs-lookup"><span data-stu-id="16cf2-126">Service</span></span>  
 <span data-ttu-id="16cf2-127">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="16cf2-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="16cf2-128">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="16cf2-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="16cf2-129">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="16cf2-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="16cf2-130">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="16cf2-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="16cf2-131">Kód</span><span class="sxs-lookup"><span data-stu-id="16cf2-131">Code</span></span>  
 <span data-ttu-id="16cf2-132">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení systému Windows.</span><span class="sxs-lookup"><span data-stu-id="16cf2-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="16cf2-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="16cf2-133">Configuration</span></span>  
 <span data-ttu-id="16cf2-134">K nastavení koncového bodu služby se dá použít následující konfigurace:</span><span class="sxs-lookup"><span data-stu-id="16cf2-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="16cf2-135">Klient</span><span class="sxs-lookup"><span data-stu-id="16cf2-135">Client</span></span>  
 <span data-ttu-id="16cf2-136">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="16cf2-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="16cf2-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="16cf2-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="16cf2-138">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="16cf2-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="16cf2-139">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="16cf2-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="16cf2-140">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="16cf2-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="16cf2-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="16cf2-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="16cf2-142">Kód</span><span class="sxs-lookup"><span data-stu-id="16cf2-142">Code</span></span>  
 <span data-ttu-id="16cf2-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="16cf2-143">The following code creates the client.</span></span> <span data-ttu-id="16cf2-144">Vazba je nakonfigurovaná tak, aby používala zabezpečení transportního režimu s přenosem TCP s typem přihlašovacích údajů klienta nastaveným na Windows.</span><span class="sxs-lookup"><span data-stu-id="16cf2-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="16cf2-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="16cf2-145">Configuration</span></span>  
 <span data-ttu-id="16cf2-146">Následující konfiguraci lze použít místo kódu k vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="16cf2-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16cf2-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16cf2-147">See also</span></span>

- [<span data-ttu-id="16cf2-148">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="16cf2-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="16cf2-149">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="16cf2-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="16cf2-150">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="16cf2-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
