---
title: Zabezpečení zprávy s klientem Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: 794a3d8e118cadd2a2752e1bbf85ef930deb2f27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138642"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="c690c-102">Zabezpečení zprávy s klientem Windows</span><span class="sxs-lookup"><span data-stu-id="c690c-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="c690c-103">Tento scénář popisuje Windows Communication Foundation (WCF) klientem a serverem zabezpečené pomocí režim zabezpečených zpráv.</span><span class="sxs-lookup"><span data-stu-id="c690c-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="c690c-104">Klient a služba ověření pomocí přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="c690c-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="c690c-105">![Zabezpečení s klientem Windows zpráv](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="c690c-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="c690c-106">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c690c-106">Characteristic</span></span>|<span data-ttu-id="c690c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c690c-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c690c-108">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c690c-108">Security Mode</span></span>|<span data-ttu-id="c690c-109">Zpráva</span><span class="sxs-lookup"><span data-stu-id="c690c-109">Message</span></span>|  
|<span data-ttu-id="c690c-110">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="c690c-110">Interoperability</span></span>|<span data-ttu-id="c690c-111">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="c690c-111">WCF Only</span></span>|  
|<span data-ttu-id="c690c-112">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="c690c-112">Authentication (Server)</span></span>|<span data-ttu-id="c690c-113">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="c690c-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="c690c-114">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="c690c-114">Authentication (Client)</span></span>|<span data-ttu-id="c690c-115">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="c690c-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="c690c-116">Integrita</span><span class="sxs-lookup"><span data-stu-id="c690c-116">Integrity</span></span>|<span data-ttu-id="c690c-117">Ano, pomocí sdíleného bezpečnostní kontext</span><span class="sxs-lookup"><span data-stu-id="c690c-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="c690c-118">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="c690c-118">Confidentiality</span></span>|<span data-ttu-id="c690c-119">Ano, pomocí sdíleného bezpečnostní kontext</span><span class="sxs-lookup"><span data-stu-id="c690c-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="c690c-120">Přenos</span><span class="sxs-lookup"><span data-stu-id="c690c-120">Transport</span></span>|<span data-ttu-id="c690c-121">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="c690c-121">NET.TCP</span></span>|  
|<span data-ttu-id="c690c-122">Vazba</span><span class="sxs-lookup"><span data-stu-id="c690c-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="c690c-123">Služba</span><span class="sxs-lookup"><span data-stu-id="c690c-123">Service</span></span>  
 <span data-ttu-id="c690c-124">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="c690c-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c690c-125">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="c690c-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="c690c-126">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c690c-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="c690c-127">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="c690c-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c690c-128">Kód</span><span class="sxs-lookup"><span data-stu-id="c690c-128">Code</span></span>  
 <span data-ttu-id="c690c-129">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv k navázání zabezpečené kontextu s počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="c690c-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="c690c-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c690c-130">Configuration</span></span>  
 <span data-ttu-id="c690c-131">Následující konfigurace lze namísto kódu k nastavení služby:</span><span class="sxs-lookup"><span data-stu-id="c690c-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="c690c-132">Klient</span><span class="sxs-lookup"><span data-stu-id="c690c-132">Client</span></span>  
 <span data-ttu-id="c690c-133">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="c690c-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c690c-134">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="c690c-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="c690c-135">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="c690c-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="c690c-136">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c690c-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="c690c-137">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c690c-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="c690c-138">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c690c-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="c690c-139">Kód</span><span class="sxs-lookup"><span data-stu-id="c690c-139">Code</span></span>  
 <span data-ttu-id="c690c-140">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="c690c-140">The following code creates a client.</span></span> <span data-ttu-id="c690c-141">Vazba má režim zabezpečení zpráv a typu pověření klienta je nastavena na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="c690c-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="c690c-142">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c690c-142">Configuration</span></span>  
 <span data-ttu-id="c690c-143">Následující konfigurace se používá k nastavení vlastnosti klienta.</span><span class="sxs-lookup"><span data-stu-id="c690c-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"   
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">          
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c690c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c690c-144">See also</span></span>

- [<span data-ttu-id="c690c-145">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c690c-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="c690c-146">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="c690c-146">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
