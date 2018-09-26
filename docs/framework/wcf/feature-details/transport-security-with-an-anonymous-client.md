---
title: Zabezpečení přenosu s anonymním klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
author: BrucePerlerMS
ms.openlocfilehash: d09d2a2ad4e48e67f2d3930517a2ed3f8cc4403d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072823"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="1b000-102">Zabezpečení přenosu s anonymním klientem</span><span class="sxs-lookup"><span data-stu-id="1b000-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="1b000-103">Tento scénář Windows Communication Foundation (WCF) používá k zajištění důvěrnost a integrita zabezpečení přenosu (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="1b000-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="1b000-104">Server musí být ověřené pomocí certifikátu vrstvy SSL (Secure Sockets) a klienti musí důvěřovat certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="1b000-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="1b000-105">Klient není ověřována každý použitý mechanizmus a je proto anonymní.</span><span class="sxs-lookup"><span data-stu-id="1b000-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="1b000-106">Ukázková aplikace, najdete v části [zabezpečení přenosu WS](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="1b000-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> <span data-ttu-id="1b000-107">Další informace o zabezpečení přenosu, naleznete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b000-107">For more information about transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 <span data-ttu-id="1b000-108">Další informace o pomocí certifikátu služby najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="1b000-108">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="1b000-109">![Pomocí zabezpečení přenosu s anonymním klientem](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="1b000-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="1b000-110">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1b000-110">Characteristic</span></span>|<span data-ttu-id="1b000-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1b000-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1b000-112">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1b000-112">Security Mode</span></span>|<span data-ttu-id="1b000-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="1b000-113">Transport</span></span>|  
|<span data-ttu-id="1b000-114">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="1b000-114">Interoperability</span></span>|<span data-ttu-id="1b000-115">Existující webové služby a klienti</span><span class="sxs-lookup"><span data-stu-id="1b000-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="1b000-116">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="1b000-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="1b000-117">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="1b000-117">Authentication (Client)</span></span>|<span data-ttu-id="1b000-118">Ano</span><span class="sxs-lookup"><span data-stu-id="1b000-118">Yes</span></span><br /><br /> <span data-ttu-id="1b000-119">Úroveň aplikace (bez podpory WCF)</span><span class="sxs-lookup"><span data-stu-id="1b000-119">Application level (no WCF support)</span></span>|  
|<span data-ttu-id="1b000-120">Integrita</span><span class="sxs-lookup"><span data-stu-id="1b000-120">Integrity</span></span>|<span data-ttu-id="1b000-121">Ano</span><span class="sxs-lookup"><span data-stu-id="1b000-121">Yes</span></span>|  
|<span data-ttu-id="1b000-122">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="1b000-122">Confidentiality</span></span>|<span data-ttu-id="1b000-123">Ano</span><span class="sxs-lookup"><span data-stu-id="1b000-123">Yes</span></span>|  
|<span data-ttu-id="1b000-124">Přenos</span><span class="sxs-lookup"><span data-stu-id="1b000-124">Transport</span></span>|<span data-ttu-id="1b000-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="1b000-125">HTTPS</span></span>|  
|<span data-ttu-id="1b000-126">Vazba</span><span class="sxs-lookup"><span data-stu-id="1b000-126">Binding</span></span>|<span data-ttu-id="1b000-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="1b000-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="1b000-128">Služba</span><span class="sxs-lookup"><span data-stu-id="1b000-128">Service</span></span>  
 <span data-ttu-id="1b000-129">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="1b000-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="1b000-130">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="1b000-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="1b000-131">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1b000-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="1b000-132">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="1b000-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1b000-133">Kód</span><span class="sxs-lookup"><span data-stu-id="1b000-133">Code</span></span>  
 <span data-ttu-id="1b000-134">Následující kód ukazuje, jak vytvořit koncový bod pomocí zabezpečení přenosu:</span><span class="sxs-lookup"><span data-stu-id="1b000-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="1b000-135">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1b000-135">Configuration</span></span>  
 <span data-ttu-id="1b000-136">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1b000-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="1b000-137">Klient není ověřována každý použitý mechanizmus a proto je anonymní.</span><span class="sxs-lookup"><span data-stu-id="1b000-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="1b000-138">Klient</span><span class="sxs-lookup"><span data-stu-id="1b000-138">Client</span></span>  
 <span data-ttu-id="1b000-139">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="1b000-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="1b000-140">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="1b000-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="1b000-141">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="1b000-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="1b000-142">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="1b000-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="1b000-143">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1b000-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="1b000-144">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1b000-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="1b000-145">Kód</span><span class="sxs-lookup"><span data-stu-id="1b000-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="1b000-146">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1b000-146">Configuration</span></span>  
 <span data-ttu-id="1b000-147">Následující konfigurace lze namísto kódu k nastavení služby Azure.</span><span class="sxs-lookup"><span data-stu-id="1b000-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b000-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b000-148">See Also</span></span>  
 [<span data-ttu-id="1b000-149">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1b000-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="1b000-150">Zabezpečení přenosu WS</span><span class="sxs-lookup"><span data-stu-id="1b000-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="1b000-151">Přehled zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="1b000-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="1b000-152">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="1b000-152">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
