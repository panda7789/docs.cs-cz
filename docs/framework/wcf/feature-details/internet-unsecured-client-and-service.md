---
title: Nezabezpečený internetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 0b02d1efc98f02390555861871d280f9800ced1e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598876"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="44ba1-102">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="44ba1-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="44ba1-103">Následující ilustrace znázorňuje příklad veřejného, nezabezpečeného klienta a služby Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="44ba1-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje nezabezpečený internetový scénář](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="44ba1-105">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="44ba1-105">Characteristic</span></span>|<span data-ttu-id="44ba1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="44ba1-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="44ba1-107">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="44ba1-107">Security Mode</span></span>|<span data-ttu-id="44ba1-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="44ba1-108">None</span></span>|  
|<span data-ttu-id="44ba1-109">Přenos</span><span class="sxs-lookup"><span data-stu-id="44ba1-109">Transport</span></span>|<span data-ttu-id="44ba1-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="44ba1-110">HTTP</span></span>|  
|<span data-ttu-id="44ba1-111">Vazba</span><span class="sxs-lookup"><span data-stu-id="44ba1-111">Binding</span></span>|<span data-ttu-id="44ba1-112"><xref:System.ServiceModel.BasicHttpBinding>v kódu nebo [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) elementu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="44ba1-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="44ba1-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="44ba1-113">Interoperability</span></span>|<span data-ttu-id="44ba1-114">S existujícími klienty a službami webové služby</span><span class="sxs-lookup"><span data-stu-id="44ba1-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="44ba1-115">Authentication</span><span class="sxs-lookup"><span data-stu-id="44ba1-115">Authentication</span></span>|<span data-ttu-id="44ba1-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="44ba1-116">None</span></span>|  
|<span data-ttu-id="44ba1-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="44ba1-117">Integrity</span></span>|<span data-ttu-id="44ba1-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="44ba1-118">None</span></span>|  
|<span data-ttu-id="44ba1-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="44ba1-119">Confidentiality</span></span>|<span data-ttu-id="44ba1-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="44ba1-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="44ba1-121">Služba</span><span class="sxs-lookup"><span data-stu-id="44ba1-121">Service</span></span>  
 <span data-ttu-id="44ba1-122">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="44ba1-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="44ba1-123">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="44ba1-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="44ba1-124">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="44ba1-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="44ba1-125">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="44ba1-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="44ba1-126">Kód</span><span class="sxs-lookup"><span data-stu-id="44ba1-126">Code</span></span>  
 <span data-ttu-id="44ba1-127">Následující kód ukazuje, jak vytvořit koncový bod bez zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="44ba1-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="44ba1-128">Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> má režim zabezpečení nastaven na hodnotu <xref:System.ServiceModel.BasicHttpSecurityMode.None> .</span><span class="sxs-lookup"><span data-stu-id="44ba1-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="44ba1-129">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="44ba1-129">Service Configuration</span></span>  
 <span data-ttu-id="44ba1-130">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="44ba1-130">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="44ba1-131">Klient</span><span class="sxs-lookup"><span data-stu-id="44ba1-131">Client</span></span>  
 <span data-ttu-id="44ba1-132">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="44ba1-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="44ba1-133">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="44ba1-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="44ba1-134">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="44ba1-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="44ba1-135">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="44ba1-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="44ba1-136">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="44ba1-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="44ba1-137">Například:</span><span class="sxs-lookup"><span data-stu-id="44ba1-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="44ba1-138">Kód</span><span class="sxs-lookup"><span data-stu-id="44ba1-138">Code</span></span>  
 <span data-ttu-id="44ba1-139">Následující kód ukazuje základního klienta WCF, který přistupuje k nezabezpečenému koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="44ba1-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="44ba1-140">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="44ba1-140">Client Configuration</span></span>  
 <span data-ttu-id="44ba1-141">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="44ba1-141">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44ba1-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="44ba1-142">See also</span></span>

- [<span data-ttu-id="44ba1-143">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="44ba1-143">Common Security Scenarios</span></span>](common-security-scenarios.md)
- [<span data-ttu-id="44ba1-144">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="44ba1-144">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="44ba1-145">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="44ba1-145">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
