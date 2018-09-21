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
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481640"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="64f4a-102">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="64f4a-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="64f4a-103">Následující obrázek znázorňuje příklad veřejné, zabezpečená klienta Windows Communication Foundation (WCF) a služby.</span><span class="sxs-lookup"><span data-stu-id="64f4a-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service.</span></span>  
  
 <span data-ttu-id="64f4a-104">![Zabezpečená scénář cleint a službu Internet](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span><span class="sxs-lookup"><span data-stu-id="64f4a-104">![Unsecured Internet cleint and service scenario](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span></span>  
  
|<span data-ttu-id="64f4a-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="64f4a-105">Characteristic</span></span>|<span data-ttu-id="64f4a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="64f4a-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="64f4a-107">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="64f4a-107">Security Mode</span></span>|<span data-ttu-id="64f4a-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="64f4a-108">None</span></span>|  
|<span data-ttu-id="64f4a-109">Přenos</span><span class="sxs-lookup"><span data-stu-id="64f4a-109">Transport</span></span>|<span data-ttu-id="64f4a-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="64f4a-110">HTTP</span></span>|  
|<span data-ttu-id="64f4a-111">Vazba</span><span class="sxs-lookup"><span data-stu-id="64f4a-111">Binding</span></span>|<span data-ttu-id="64f4a-112"><xref:System.ServiceModel.BasicHttpBinding> v kódu nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="64f4a-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="64f4a-113">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="64f4a-113">Interoperability</span></span>|<span data-ttu-id="64f4a-114">Stávající klienty webové služby a služby</span><span class="sxs-lookup"><span data-stu-id="64f4a-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="64f4a-115">Ověřování</span><span class="sxs-lookup"><span data-stu-id="64f4a-115">Authentication</span></span>|<span data-ttu-id="64f4a-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="64f4a-116">None</span></span>|  
|<span data-ttu-id="64f4a-117">Integrita</span><span class="sxs-lookup"><span data-stu-id="64f4a-117">Integrity</span></span>|<span data-ttu-id="64f4a-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="64f4a-118">None</span></span>|  
|<span data-ttu-id="64f4a-119">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="64f4a-119">Confidentiality</span></span>|<span data-ttu-id="64f4a-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="64f4a-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="64f4a-121">Služba</span><span class="sxs-lookup"><span data-stu-id="64f4a-121">Service</span></span>  
 <span data-ttu-id="64f4a-122">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="64f4a-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="64f4a-123">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="64f4a-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="64f4a-124">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="64f4a-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="64f4a-125">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="64f4a-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="64f4a-126">Kód</span><span class="sxs-lookup"><span data-stu-id="64f4a-126">Code</span></span>  
 <span data-ttu-id="64f4a-127">Následující kód ukazuje, jak vytvořit koncový bod se zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="64f4a-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="64f4a-128">Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> má režim zabezpečení nastavený na <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="64f4a-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="64f4a-129">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="64f4a-129">Service Configuration</span></span>  
 <span data-ttu-id="64f4a-130">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="64f4a-130">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="64f4a-131">Klient</span><span class="sxs-lookup"><span data-stu-id="64f4a-131">Client</span></span>  
 <span data-ttu-id="64f4a-132">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="64f4a-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="64f4a-133">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="64f4a-133">Do one of the following:</span></span>  
  
-   <span data-ttu-id="64f4a-134">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="64f4a-134">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="64f4a-135">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="64f4a-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="64f4a-136">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="64f4a-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="64f4a-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="64f4a-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="64f4a-138">Kód</span><span class="sxs-lookup"><span data-stu-id="64f4a-138">Code</span></span>  
 <span data-ttu-id="64f4a-139">Následující kód ukazuje základní klienta WCF, který přistupuje k nezabezpečené koncový bod.</span><span class="sxs-lookup"><span data-stu-id="64f4a-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="64f4a-140">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="64f4a-140">Client Configuration</span></span>  
 <span data-ttu-id="64f4a-141">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="64f4a-141">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64f4a-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="64f4a-142">See Also</span></span>  
 [<span data-ttu-id="64f4a-143">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="64f4a-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [<span data-ttu-id="64f4a-144">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="64f4a-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="64f4a-145">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="64f4a-145">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
