---
title: Nezabezpečený internetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 4a84b32664c16dad48dd415e430134c5fb98303a
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211928"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="65c3c-102">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="65c3c-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="65c3c-103">Následující ilustrace znázorňuje příklad veřejného, nezabezpečeného klienta a služby Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="65c3c-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje nezabezpečený internetový scénář](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="65c3c-105">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="65c3c-105">Characteristic</span></span>|<span data-ttu-id="65c3c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="65c3c-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="65c3c-107">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65c3c-107">Security Mode</span></span>|<span data-ttu-id="65c3c-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="65c3c-108">None</span></span>|  
|<span data-ttu-id="65c3c-109">Doprava</span><span class="sxs-lookup"><span data-stu-id="65c3c-109">Transport</span></span>|<span data-ttu-id="65c3c-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="65c3c-110">HTTP</span></span>|  
|<span data-ttu-id="65c3c-111">Vazba</span><span class="sxs-lookup"><span data-stu-id="65c3c-111">Binding</span></span>|<span data-ttu-id="65c3c-112"><xref:System.ServiceModel.BasicHttpBinding> v kódu, nebo prvek [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="65c3c-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="65c3c-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="65c3c-113">Interoperability</span></span>|<span data-ttu-id="65c3c-114">S existujícími klienty a službami webové služby</span><span class="sxs-lookup"><span data-stu-id="65c3c-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="65c3c-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="65c3c-115">Authentication</span></span>|<span data-ttu-id="65c3c-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="65c3c-116">None</span></span>|  
|<span data-ttu-id="65c3c-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="65c3c-117">Integrity</span></span>|<span data-ttu-id="65c3c-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="65c3c-118">None</span></span>|  
|<span data-ttu-id="65c3c-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="65c3c-119">Confidentiality</span></span>|<span data-ttu-id="65c3c-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="65c3c-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="65c3c-121">Service</span><span class="sxs-lookup"><span data-stu-id="65c3c-121">Service</span></span>  
 <span data-ttu-id="65c3c-122">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="65c3c-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="65c3c-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="65c3c-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="65c3c-124">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="65c3c-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="65c3c-125">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="65c3c-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="65c3c-126">Kód</span><span class="sxs-lookup"><span data-stu-id="65c3c-126">Code</span></span>  
 <span data-ttu-id="65c3c-127">Následující kód ukazuje, jak vytvořit koncový bod bez zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="65c3c-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="65c3c-128">Ve výchozím nastavení má <xref:System.ServiceModel.BasicHttpBinding> režim zabezpečení nastavený na <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="65c3c-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="65c3c-129">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="65c3c-129">Service Configuration</span></span>  
 <span data-ttu-id="65c3c-130">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="65c3c-130">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="65c3c-131">Klient</span><span class="sxs-lookup"><span data-stu-id="65c3c-131">Client</span></span>  
 <span data-ttu-id="65c3c-132">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="65c3c-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="65c3c-133">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="65c3c-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="65c3c-134">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="65c3c-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="65c3c-135">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="65c3c-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="65c3c-136">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="65c3c-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="65c3c-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="65c3c-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="65c3c-138">Kód</span><span class="sxs-lookup"><span data-stu-id="65c3c-138">Code</span></span>  
 <span data-ttu-id="65c3c-139">Následující kód ukazuje základního klienta WCF, který přistupuje k nezabezpečenému koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="65c3c-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="65c3c-140">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="65c3c-140">Client Configuration</span></span>  
 <span data-ttu-id="65c3c-141">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="65c3c-141">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="65c3c-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65c3c-142">See also</span></span>

- [<span data-ttu-id="65c3c-143">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65c3c-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [<span data-ttu-id="65c3c-144">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65c3c-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="65c3c-145">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="65c3c-145">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
