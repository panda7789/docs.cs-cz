---
title: Zabezpečení přenosu pomocí ověřování systému Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 96fce3cb56cf328e0fbb589113e3ac24519de557
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125444"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="202b8-102">Zabezpečení přenosu pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="202b8-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="202b8-103">Následující scénář ukazuje klienta Windows Communication Foundation (WCF) a služby zabezpečuje zabezpečení Windows.</span><span class="sxs-lookup"><span data-stu-id="202b8-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="202b8-104">Další informace o programování naleznete v tématu [jak: Zabezpečení služby pomocí pověření Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="202b8-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="202b8-105">Intranet webové služby zobrazí informace o lidských zdrojů.</span><span class="sxs-lookup"><span data-stu-id="202b8-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="202b8-106">Klient je aplikace Windows Form.</span><span class="sxs-lookup"><span data-stu-id="202b8-106">The client is a Windows Form application.</span></span> <span data-ttu-id="202b8-107">Aplikace je nasazená v doméně pomocí protokolu Kerberos řadiče domény zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="202b8-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Zabezpečení přenosu pomocí ověřování Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="202b8-109">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="202b8-109">Characteristic</span></span>|<span data-ttu-id="202b8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="202b8-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="202b8-111">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="202b8-111">Security Mode</span></span>|<span data-ttu-id="202b8-112">Přenos</span><span class="sxs-lookup"><span data-stu-id="202b8-112">Transport</span></span>|  
|<span data-ttu-id="202b8-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="202b8-113">Interoperability</span></span>|<span data-ttu-id="202b8-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="202b8-114">WCF only</span></span>|  
|<span data-ttu-id="202b8-115">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="202b8-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="202b8-116">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="202b8-116">Authentication (Client)</span></span>|<span data-ttu-id="202b8-117">Ano (s použitím integrované ověřování Windows)</span><span class="sxs-lookup"><span data-stu-id="202b8-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="202b8-118">Ano (s použitím integrované ověřování Windows)</span><span class="sxs-lookup"><span data-stu-id="202b8-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="202b8-119">Integrita</span><span class="sxs-lookup"><span data-stu-id="202b8-119">Integrity</span></span>|<span data-ttu-id="202b8-120">Ano</span><span class="sxs-lookup"><span data-stu-id="202b8-120">Yes</span></span>|  
|<span data-ttu-id="202b8-121">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="202b8-121">Confidentiality</span></span>|<span data-ttu-id="202b8-122">Ano</span><span class="sxs-lookup"><span data-stu-id="202b8-122">Yes</span></span>|  
|<span data-ttu-id="202b8-123">Přenos</span><span class="sxs-lookup"><span data-stu-id="202b8-123">Transport</span></span>|<span data-ttu-id="202b8-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="202b8-124">NET.TCP</span></span>|  
|<span data-ttu-id="202b8-125">Vazba</span><span class="sxs-lookup"><span data-stu-id="202b8-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="202b8-126">Služba</span><span class="sxs-lookup"><span data-stu-id="202b8-126">Service</span></span>  
 <span data-ttu-id="202b8-127">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="202b8-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="202b8-128">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="202b8-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="202b8-129">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="202b8-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="202b8-130">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="202b8-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="202b8-131">Kód</span><span class="sxs-lookup"><span data-stu-id="202b8-131">Code</span></span>  
 <span data-ttu-id="202b8-132">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení Windows.</span><span class="sxs-lookup"><span data-stu-id="202b8-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="202b8-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="202b8-133">Configuration</span></span>  
 <span data-ttu-id="202b8-134">Následující konfigurace lze namísto kódu k nastavení koncového bodu služby:</span><span class="sxs-lookup"><span data-stu-id="202b8-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="202b8-135">Klient</span><span class="sxs-lookup"><span data-stu-id="202b8-135">Client</span></span>  
 <span data-ttu-id="202b8-136">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="202b8-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="202b8-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="202b8-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="202b8-138">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="202b8-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="202b8-139">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="202b8-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="202b8-140">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="202b8-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="202b8-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="202b8-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="202b8-142">Kód</span><span class="sxs-lookup"><span data-stu-id="202b8-142">Code</span></span>  
 <span data-ttu-id="202b8-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="202b8-143">The following code creates the client.</span></span> <span data-ttu-id="202b8-144">Je vazba konfigurována pro použití režimu zabezpečení přenosu, s přenosu protokolu TCP s typu pověření klienta, nastavte na Windows.</span><span class="sxs-lookup"><span data-stu-id="202b8-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="202b8-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="202b8-145">Configuration</span></span>  
 <span data-ttu-id="202b8-146">Následující konfigurace je použít místo kód pro vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="202b8-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="202b8-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="202b8-147">See also</span></span>
- [<span data-ttu-id="202b8-148">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="202b8-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="202b8-149">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="202b8-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [<span data-ttu-id="202b8-150">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="202b8-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
