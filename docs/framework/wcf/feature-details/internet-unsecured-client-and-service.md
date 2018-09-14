---
title: Nezabezpečený internetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b2c71af169018f272a6ca538bba9191f9ddbc0dd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519231"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="36167-102">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="36167-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="36167-103">Následující obrázek znázorňuje příklad veřejné, zabezpečená klienta Windows Communication Foundation (WCF) a služby.</span><span class="sxs-lookup"><span data-stu-id="36167-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service.</span></span>  
  
 <span data-ttu-id="36167-104">![Zabezpečená scénář cleint a službu Internet](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span><span class="sxs-lookup"><span data-stu-id="36167-104">![Unsecured Internet cleint and service scenario](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span></span>  
  
|<span data-ttu-id="36167-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="36167-105">Characteristic</span></span>|<span data-ttu-id="36167-106">Popis</span><span class="sxs-lookup"><span data-stu-id="36167-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="36167-107">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="36167-107">Security Mode</span></span>|<span data-ttu-id="36167-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="36167-108">None</span></span>|  
|<span data-ttu-id="36167-109">Přenos</span><span class="sxs-lookup"><span data-stu-id="36167-109">Transport</span></span>|<span data-ttu-id="36167-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="36167-110">HTTP</span></span>|  
|<span data-ttu-id="36167-111">Vazba</span><span class="sxs-lookup"><span data-stu-id="36167-111">Binding</span></span>|<span data-ttu-id="36167-112"><xref:System.ServiceModel.BasicHttpBinding> v kódu nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="36167-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="36167-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="36167-113">Interoperability</span></span>|<span data-ttu-id="36167-114">Stávající klienty webové služby a služby</span><span class="sxs-lookup"><span data-stu-id="36167-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="36167-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="36167-115">Authentication</span></span>|<span data-ttu-id="36167-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="36167-116">None</span></span>|  
|<span data-ttu-id="36167-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="36167-117">Integrity</span></span>|<span data-ttu-id="36167-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="36167-118">None</span></span>|  
|<span data-ttu-id="36167-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="36167-119">Confidentiality</span></span>|<span data-ttu-id="36167-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="36167-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="36167-121">Služba</span><span class="sxs-lookup"><span data-stu-id="36167-121">Service</span></span>  
 <span data-ttu-id="36167-122">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="36167-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="36167-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="36167-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="36167-124">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="36167-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="36167-125">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="36167-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="36167-126">Kód</span><span class="sxs-lookup"><span data-stu-id="36167-126">Code</span></span>  
 <span data-ttu-id="36167-127">Následující kód ukazuje, jak vytvořit koncový bod se zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="36167-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="36167-128">Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> má režim zabezpečení nastavený na <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="36167-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="36167-129">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="36167-129">Service Configuration</span></span>  
 <span data-ttu-id="36167-130">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="36167-130">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="36167-131">Klient</span><span class="sxs-lookup"><span data-stu-id="36167-131">Client</span></span>  
 <span data-ttu-id="36167-132">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="36167-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="36167-133">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="36167-133">Do one of the following:</span></span>  
  
-   <span data-ttu-id="36167-134">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="36167-134">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="36167-135">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="36167-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="36167-136">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="36167-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="36167-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="36167-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="36167-138">Kód</span><span class="sxs-lookup"><span data-stu-id="36167-138">Code</span></span>  
 <span data-ttu-id="36167-139">Následující kód ukazuje základní klienta WCF, který přistupuje k nezabezpečené koncový bod.</span><span class="sxs-lookup"><span data-stu-id="36167-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="36167-140">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="36167-140">Client Configuration</span></span>  
 <span data-ttu-id="36167-141">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="36167-141">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36167-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="36167-142">See Also</span></span>  
 [<span data-ttu-id="36167-143">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="36167-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [<span data-ttu-id="36167-144">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="36167-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="36167-145">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="36167-145">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
