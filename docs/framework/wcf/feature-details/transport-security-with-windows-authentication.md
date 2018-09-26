---
title: Zabezpečení přenosu pomocí ověřování systému Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
author: BrucePerlerMS
ms.openlocfilehash: babafe369ee9f5c9261e3b5c8bc749d3d1d39ec4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079859"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="f677e-102">Zabezpečení přenosu pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="f677e-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="f677e-103">Následující scénář ukazuje klienta Windows Communication Foundation (WCF) a služby zabezpečuje zabezpečení Windows.</span><span class="sxs-lookup"><span data-stu-id="f677e-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="f677e-104">Další informace o programování naleznete v tématu [postupy: zabezpečení služby pomocí pověření Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="f677e-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="f677e-105">Intranet webové služby zobrazí informace o lidských zdrojů.</span><span class="sxs-lookup"><span data-stu-id="f677e-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="f677e-106">Klient je aplikace Windows Form.</span><span class="sxs-lookup"><span data-stu-id="f677e-106">The client is a Windows Form application.</span></span> <span data-ttu-id="f677e-107">Aplikace je nasazená v doméně pomocí protokolu Kerberos řadiče domény zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f677e-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="f677e-108">![Zabezpečení s ověřováním Windows přenosu](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="f677e-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="f677e-109">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="f677e-109">Characteristic</span></span>|<span data-ttu-id="f677e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f677e-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f677e-111">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f677e-111">Security Mode</span></span>|<span data-ttu-id="f677e-112">Přenos</span><span class="sxs-lookup"><span data-stu-id="f677e-112">Transport</span></span>|  
|<span data-ttu-id="f677e-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="f677e-113">Interoperability</span></span>|<span data-ttu-id="f677e-114">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="f677e-114">WCF only</span></span>|  
|<span data-ttu-id="f677e-115">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="f677e-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="f677e-116">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="f677e-116">Authentication (Client)</span></span>|<span data-ttu-id="f677e-117">Ano (s použitím integrované ověřování Windows)</span><span class="sxs-lookup"><span data-stu-id="f677e-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="f677e-118">Ano (s použitím integrované ověřování Windows)</span><span class="sxs-lookup"><span data-stu-id="f677e-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="f677e-119">Integrita</span><span class="sxs-lookup"><span data-stu-id="f677e-119">Integrity</span></span>|<span data-ttu-id="f677e-120">Ano</span><span class="sxs-lookup"><span data-stu-id="f677e-120">Yes</span></span>|  
|<span data-ttu-id="f677e-121">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="f677e-121">Confidentiality</span></span>|<span data-ttu-id="f677e-122">Ano</span><span class="sxs-lookup"><span data-stu-id="f677e-122">Yes</span></span>|  
|<span data-ttu-id="f677e-123">Přenos</span><span class="sxs-lookup"><span data-stu-id="f677e-123">Transport</span></span>|<span data-ttu-id="f677e-124">SÍŤ. TCP</span><span class="sxs-lookup"><span data-stu-id="f677e-124">NET.TCP</span></span>|  
|<span data-ttu-id="f677e-125">Vazba</span><span class="sxs-lookup"><span data-stu-id="f677e-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f677e-126">Služba</span><span class="sxs-lookup"><span data-stu-id="f677e-126">Service</span></span>  
 <span data-ttu-id="f677e-127">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="f677e-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f677e-128">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="f677e-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="f677e-129">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f677e-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="f677e-130">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="f677e-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f677e-131">Kód</span><span class="sxs-lookup"><span data-stu-id="f677e-131">Code</span></span>  
 <span data-ttu-id="f677e-132">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení Windows.</span><span class="sxs-lookup"><span data-stu-id="f677e-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="f677e-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f677e-133">Configuration</span></span>  
 <span data-ttu-id="f677e-134">Následující konfigurace lze namísto kódu k nastavení koncového bodu služby:</span><span class="sxs-lookup"><span data-stu-id="f677e-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f677e-135">Klient</span><span class="sxs-lookup"><span data-stu-id="f677e-135">Client</span></span>  
 <span data-ttu-id="f677e-136">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="f677e-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f677e-137">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="f677e-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="f677e-138">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="f677e-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="f677e-139">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f677e-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="f677e-140">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f677e-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="f677e-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f677e-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="f677e-142">Kód</span><span class="sxs-lookup"><span data-stu-id="f677e-142">Code</span></span>  
 <span data-ttu-id="f677e-143">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="f677e-143">The following code creates the client.</span></span> <span data-ttu-id="f677e-144">Je vazba konfigurována pro použití režimu zabezpečení přenosu, s přenosu protokolu TCP s typu pověření klienta, nastavte na Windows.</span><span class="sxs-lookup"><span data-stu-id="f677e-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="f677e-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f677e-145">Configuration</span></span>  
 <span data-ttu-id="f677e-146">Následující konfigurace je použít místo kód pro vytvoření klienta.</span><span class="sxs-lookup"><span data-stu-id="f677e-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f677e-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="f677e-147">See Also</span></span>  
 [<span data-ttu-id="f677e-148">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f677e-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="f677e-149">Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows</span><span class="sxs-lookup"><span data-stu-id="f677e-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="f677e-150">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="f677e-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
