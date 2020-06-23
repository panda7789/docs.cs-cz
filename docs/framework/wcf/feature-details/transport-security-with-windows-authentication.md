---
title: Zabezpečení přenosu pomocí ověřování systému Windows
description: Přečtěte si tento scénář, který ukazuje klienta nebo službu WCF zabezpečené zabezpečením systému Windows. V tomto příkladu bude intranetová služba zobrazovat informace o lidských zdrojích.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: b6134d4cbdff0c1adea704a7f3aaff7e40fd75ec
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244761"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="f7702-104">Zabezpečení přenosu pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="f7702-104">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="f7702-105">V následujícím scénáři se zobrazuje klient a služba Windows Communication Foundation (WCF) zabezpečené zabezpečením systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f7702-105">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="f7702-106">Další informace o programování najdete v tématu [Postup: zabezpečení služby pomocí pověření systému Windows](../how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="f7702-106">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="f7702-107">Intranetová webová služba zobrazuje informace o lidských zdrojích.</span><span class="sxs-lookup"><span data-stu-id="f7702-107">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="f7702-108">Klient je aplikace formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="f7702-108">The client is a Windows Form application.</span></span> <span data-ttu-id="f7702-109">Aplikace je nasazena v doméně s řadičem protokolu Kerberos zabezpečení domény.</span><span class="sxs-lookup"><span data-stu-id="f7702-109">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Zabezpečení přenosu s ověřováním systému Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="f7702-111">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="f7702-111">Characteristic</span></span>|<span data-ttu-id="f7702-112">Description</span><span class="sxs-lookup"><span data-stu-id="f7702-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f7702-113">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f7702-113">Security Mode</span></span>|<span data-ttu-id="f7702-114">Přenos</span><span class="sxs-lookup"><span data-stu-id="f7702-114">Transport</span></span>|  
|<span data-ttu-id="f7702-115">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="f7702-115">Interoperability</span></span>|<span data-ttu-id="f7702-116">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="f7702-116">WCF only</span></span>|  
|<span data-ttu-id="f7702-117">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="f7702-117">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="f7702-118">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="f7702-118">Authentication (Client)</span></span>|<span data-ttu-id="f7702-119">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="f7702-119">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="f7702-120">Ano (pomocí integrovaného ověřování systému Windows)</span><span class="sxs-lookup"><span data-stu-id="f7702-120">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="f7702-121">Integrita</span><span class="sxs-lookup"><span data-stu-id="f7702-121">Integrity</span></span>|<span data-ttu-id="f7702-122">Ano</span><span class="sxs-lookup"><span data-stu-id="f7702-122">Yes</span></span>|  
|<span data-ttu-id="f7702-123">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="f7702-123">Confidentiality</span></span>|<span data-ttu-id="f7702-124">Ano</span><span class="sxs-lookup"><span data-stu-id="f7702-124">Yes</span></span>|  
|<span data-ttu-id="f7702-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="f7702-125">Transport</span></span>|<span data-ttu-id="f7702-126">Pohyby. PROTOKOLU</span><span class="sxs-lookup"><span data-stu-id="f7702-126">NET.TCP</span></span>|  
|<span data-ttu-id="f7702-127">Vazba</span><span class="sxs-lookup"><span data-stu-id="f7702-127">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f7702-128">Služba</span><span class="sxs-lookup"><span data-stu-id="f7702-128">Service</span></span>  
 <span data-ttu-id="f7702-129">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="f7702-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f7702-130">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="f7702-130">Do one of the following:</span></span>  
  
- <span data-ttu-id="f7702-131">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f7702-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="f7702-132">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="f7702-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f7702-133">Kód</span><span class="sxs-lookup"><span data-stu-id="f7702-133">Code</span></span>  
 <span data-ttu-id="f7702-134">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f7702-134">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="f7702-135">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f7702-135">Configuration</span></span>  
 <span data-ttu-id="f7702-136">K nastavení koncového bodu služby se dá použít následující konfigurace:</span><span class="sxs-lookup"><span data-stu-id="f7702-136">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f7702-137">Klient</span><span class="sxs-lookup"><span data-stu-id="f7702-137">Client</span></span>  
 <span data-ttu-id="f7702-138">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="f7702-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f7702-139">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="f7702-139">Do one of the following:</span></span>  
  
- <span data-ttu-id="f7702-140">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="f7702-140">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="f7702-141">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f7702-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="f7702-142">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="f7702-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="f7702-143">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f7702-143">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="f7702-144">Kód</span><span class="sxs-lookup"><span data-stu-id="f7702-144">Code</span></span>  
 <span data-ttu-id="f7702-145">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="f7702-145">The following code creates the client.</span></span> <span data-ttu-id="f7702-146">Vazba je nakonfigurovaná tak, aby používala zabezpečení transportního režimu s přenosem TCP s typem přihlašovacích údajů klienta nastaveným na Windows.</span><span class="sxs-lookup"><span data-stu-id="f7702-146">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="f7702-147">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f7702-147">Configuration</span></span>  
 <span data-ttu-id="f7702-148">Následující konfiguraci lze použít místo kódu k vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="f7702-148">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7702-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7702-149">See also</span></span>

- [<span data-ttu-id="f7702-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f7702-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="f7702-151">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="f7702-151">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="f7702-152">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f7702-152">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
