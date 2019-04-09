---
title: Nezabezpečený internetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: ca6b028ef20095d6faeb125151772eedf1500fa0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133754"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="78b1d-102">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="78b1d-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="78b1d-103">Následující obrázek znázorňuje příklad veřejné, zabezpečená klienta Windows Communication Foundation (WCF) a služby:</span><span class="sxs-lookup"><span data-stu-id="78b1d-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Snímek obrazovky zobrazující nezabezpečené scénáře Internet](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="78b1d-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="78b1d-105">Characteristic</span></span>|<span data-ttu-id="78b1d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="78b1d-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="78b1d-107">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="78b1d-107">Security Mode</span></span>|<span data-ttu-id="78b1d-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="78b1d-108">None</span></span>|  
|<span data-ttu-id="78b1d-109">Přenos</span><span class="sxs-lookup"><span data-stu-id="78b1d-109">Transport</span></span>|<span data-ttu-id="78b1d-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="78b1d-110">HTTP</span></span>|  
|<span data-ttu-id="78b1d-111">Vazba</span><span class="sxs-lookup"><span data-stu-id="78b1d-111">Binding</span></span>|<xref:System.ServiceModel.BasicHttpBinding> <span data-ttu-id="78b1d-112">v kódu nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="78b1d-112">in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="78b1d-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="78b1d-113">Interoperability</span></span>|<span data-ttu-id="78b1d-114">Stávající klienty webové služby a služby</span><span class="sxs-lookup"><span data-stu-id="78b1d-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="78b1d-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="78b1d-115">Authentication</span></span>|<span data-ttu-id="78b1d-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="78b1d-116">None</span></span>|  
|<span data-ttu-id="78b1d-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="78b1d-117">Integrity</span></span>|<span data-ttu-id="78b1d-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="78b1d-118">None</span></span>|  
|<span data-ttu-id="78b1d-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="78b1d-119">Confidentiality</span></span>|<span data-ttu-id="78b1d-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="78b1d-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="78b1d-121">Služba</span><span class="sxs-lookup"><span data-stu-id="78b1d-121">Service</span></span>  
 <span data-ttu-id="78b1d-122">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="78b1d-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="78b1d-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="78b1d-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="78b1d-124">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="78b1d-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="78b1d-125">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="78b1d-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78b1d-126">Kód</span><span class="sxs-lookup"><span data-stu-id="78b1d-126">Code</span></span>  
 <span data-ttu-id="78b1d-127">Následující kód ukazuje, jak vytvořit koncový bod se zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="78b1d-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="78b1d-128">Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> má režim zabezpečení nastavený na <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="78b1d-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="78b1d-129">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="78b1d-129">Service Configuration</span></span>  
 <span data-ttu-id="78b1d-130">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="78b1d-130">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="78b1d-131">Klient</span><span class="sxs-lookup"><span data-stu-id="78b1d-131">Client</span></span>  
 <span data-ttu-id="78b1d-132">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="78b1d-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="78b1d-133">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="78b1d-133">Do one of the following:</span></span>  
  
-   <span data-ttu-id="78b1d-134">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="78b1d-134">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="78b1d-135">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="78b1d-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="78b1d-136">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="78b1d-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="78b1d-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="78b1d-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="78b1d-138">Kód</span><span class="sxs-lookup"><span data-stu-id="78b1d-138">Code</span></span>  
 <span data-ttu-id="78b1d-139">Následující kód ukazuje základní klienta WCF, který přistupuje k nezabezpečené koncový bod.</span><span class="sxs-lookup"><span data-stu-id="78b1d-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="78b1d-140">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="78b1d-140">Client Configuration</span></span>  
 <span data-ttu-id="78b1d-141">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="78b1d-141">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78b1d-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78b1d-142">See also</span></span>

- [<span data-ttu-id="78b1d-143">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="78b1d-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [<span data-ttu-id="78b1d-144">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="78b1d-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="78b1d-145">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="78b1d-145">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
