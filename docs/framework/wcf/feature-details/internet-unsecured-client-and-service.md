---
title: Nezabezpečený internetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 7eb640576bc00bc767ba16f8dc4a5d5952a479c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184730"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="600bc-102">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="600bc-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="600bc-103">Následující obrázek znázorňuje příklad veřejného, nezabezpečeného klienta a služby WCF (Windows Communication Foundation):</span><span class="sxs-lookup"><span data-stu-id="600bc-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Snímek obrazovky s nezabezpečeným internetovým scénářem](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="600bc-105">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="600bc-105">Characteristic</span></span>|<span data-ttu-id="600bc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="600bc-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="600bc-107">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="600bc-107">Security Mode</span></span>|<span data-ttu-id="600bc-108">Žádný</span><span class="sxs-lookup"><span data-stu-id="600bc-108">None</span></span>|  
|<span data-ttu-id="600bc-109">Přenos</span><span class="sxs-lookup"><span data-stu-id="600bc-109">Transport</span></span>|<span data-ttu-id="600bc-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="600bc-110">HTTP</span></span>|  
|<span data-ttu-id="600bc-111">Vazba</span><span class="sxs-lookup"><span data-stu-id="600bc-111">Binding</span></span>|<span data-ttu-id="600bc-112"><xref:System.ServiceModel.BasicHttpBinding>v kódu nebo [ \<základníhttpbinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) prvek v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="600bc-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="600bc-113">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="600bc-113">Interoperability</span></span>|<span data-ttu-id="600bc-114">Se stávajícími klienty a službami webových služeb</span><span class="sxs-lookup"><span data-stu-id="600bc-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="600bc-115">Authentication</span><span class="sxs-lookup"><span data-stu-id="600bc-115">Authentication</span></span>|<span data-ttu-id="600bc-116">Žádný</span><span class="sxs-lookup"><span data-stu-id="600bc-116">None</span></span>|  
|<span data-ttu-id="600bc-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="600bc-117">Integrity</span></span>|<span data-ttu-id="600bc-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="600bc-118">None</span></span>|  
|<span data-ttu-id="600bc-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="600bc-119">Confidentiality</span></span>|<span data-ttu-id="600bc-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="600bc-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="600bc-121">Služba</span><span class="sxs-lookup"><span data-stu-id="600bc-121">Service</span></span>  
 <span data-ttu-id="600bc-122">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="600bc-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="600bc-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="600bc-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="600bc-124">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="600bc-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="600bc-125">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="600bc-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="600bc-126">kód</span><span class="sxs-lookup"><span data-stu-id="600bc-126">Code</span></span>  
 <span data-ttu-id="600bc-127">Následující kód ukazuje, jak vytvořit koncový bod bez zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="600bc-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="600bc-128">Ve výchozím <xref:System.ServiceModel.BasicHttpBinding> nastavení je režim <xref:System.ServiceModel.BasicHttpSecurityMode.None>zabezpečení nastaven na .</span><span class="sxs-lookup"><span data-stu-id="600bc-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="600bc-129">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="600bc-129">Service Configuration</span></span>  
 <span data-ttu-id="600bc-130">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="600bc-130">The following code sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="600bc-131">Klient</span><span class="sxs-lookup"><span data-stu-id="600bc-131">Client</span></span>  
 <span data-ttu-id="600bc-132">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="600bc-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="600bc-133">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="600bc-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="600bc-134">Vytvořte samostatného klienta pomocí kódu (a klientského kódu).</span><span class="sxs-lookup"><span data-stu-id="600bc-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="600bc-135">Vytvořte klienta, který nedefinuje žádné adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="600bc-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="600bc-136">Místo toho použijte konstruktor klienta, který bere název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="600bc-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="600bc-137">Například:</span><span class="sxs-lookup"><span data-stu-id="600bc-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="600bc-138">kód</span><span class="sxs-lookup"><span data-stu-id="600bc-138">Code</span></span>  
 <span data-ttu-id="600bc-139">Následující kód ukazuje základní wcf klienta, který přistupuje k nezabezpečené koncový bod.</span><span class="sxs-lookup"><span data-stu-id="600bc-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="600bc-140">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="600bc-140">Client Configuration</span></span>  
 <span data-ttu-id="600bc-141">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="600bc-141">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="600bc-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="600bc-142">See also</span></span>

- [<span data-ttu-id="600bc-143">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="600bc-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [<span data-ttu-id="600bc-144">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="600bc-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="600bc-145">[Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="600bc-145">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
