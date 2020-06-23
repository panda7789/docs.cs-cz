---
title: Zabezpečení přenosu pomocí anonymního klienta
description: Projděte si tento scénář WCF, který používá zabezpečení přenosu k ověření serveru pomocí certifikátu, který důvěřuje klientovi. Klient není ověřen.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245008"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="76174-104">Zabezpečení přenosu pomocí anonymního klienta</span><span class="sxs-lookup"><span data-stu-id="76174-104">Transport security with an anonymous client</span></span>

<span data-ttu-id="76174-105">Tento scénář Windows Communication Foundation (WCF) používá k zajištění důvěrnosti a integrity zabezpečení přenosu (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="76174-105">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="76174-106">Server musí být ověřený s certifikátem SSL (Secure Sockets Layer) (SSL) a klienti musí důvěřovat certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="76174-106">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="76174-107">Klient není ověřen žádným mechanismem a proto je anonymní.</span><span class="sxs-lookup"><span data-stu-id="76174-107">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="76174-108">Ukázkovou aplikaci najdete v tématu [zabezpečení přenosu v protokolu WS](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="76174-108">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="76174-109">Další informace o zabezpečení přenosu najdete v tématu [Přehled zabezpečení přenosu](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="76174-109">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="76174-110">Další informace o používání certifikátu se službou najdete v tématu [práce s certifikáty](working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="76174-110">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Použití zabezpečení přenosu u anonymního klienta](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="76174-112">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="76174-112">Characteristic</span></span>|<span data-ttu-id="76174-113">Description</span><span class="sxs-lookup"><span data-stu-id="76174-113">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="76174-114">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76174-114">Security Mode</span></span>|<span data-ttu-id="76174-115">Přenos</span><span class="sxs-lookup"><span data-stu-id="76174-115">Transport</span></span>|
|<span data-ttu-id="76174-116">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="76174-116">Interoperability</span></span>|<span data-ttu-id="76174-117">Se stávajícími webovými službami a klienty</span><span class="sxs-lookup"><span data-stu-id="76174-117">With existing Web services and clients</span></span>|
|<span data-ttu-id="76174-118">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="76174-118">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="76174-119">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="76174-119">Authentication (Client)</span></span>|<span data-ttu-id="76174-120">Ano</span><span class="sxs-lookup"><span data-stu-id="76174-120">Yes</span></span><br /><br /> <span data-ttu-id="76174-121">Úroveň aplikace (žádná podpora WCF)</span><span class="sxs-lookup"><span data-stu-id="76174-121">Application level (no WCF support)</span></span>|
|<span data-ttu-id="76174-122">Integrita</span><span class="sxs-lookup"><span data-stu-id="76174-122">Integrity</span></span>|<span data-ttu-id="76174-123">Ano</span><span class="sxs-lookup"><span data-stu-id="76174-123">Yes</span></span>|
|<span data-ttu-id="76174-124">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="76174-124">Confidentiality</span></span>|<span data-ttu-id="76174-125">Ano</span><span class="sxs-lookup"><span data-stu-id="76174-125">Yes</span></span>|
|<span data-ttu-id="76174-126">Přenos</span><span class="sxs-lookup"><span data-stu-id="76174-126">Transport</span></span>|<span data-ttu-id="76174-127">HTTPS</span><span class="sxs-lookup"><span data-stu-id="76174-127">HTTPS</span></span>|
|<span data-ttu-id="76174-128">Vazba</span><span class="sxs-lookup"><span data-stu-id="76174-128">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="76174-129">Služba</span><span class="sxs-lookup"><span data-stu-id="76174-129">Service</span></span>

<span data-ttu-id="76174-130">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="76174-130">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="76174-131">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="76174-131">Do one of the following:</span></span>

- <span data-ttu-id="76174-132">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="76174-132">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="76174-133">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="76174-133">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="76174-134">Kód</span><span class="sxs-lookup"><span data-stu-id="76174-134">Code</span></span>

<span data-ttu-id="76174-135">Následující kód ukazuje, jak vytvořit koncový bod pomocí zabezpečení přenosu:</span><span class="sxs-lookup"><span data-stu-id="76174-135">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="76174-136">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="76174-136">Configuration</span></span>

<span data-ttu-id="76174-137">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="76174-137">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="76174-138">Klient není ověřen žádným mechanismem a proto je anonymní.</span><span class="sxs-lookup"><span data-stu-id="76174-138">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
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

## <a name="client"></a><span data-ttu-id="76174-139">Klient</span><span class="sxs-lookup"><span data-stu-id="76174-139">Client</span></span>

<span data-ttu-id="76174-140">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="76174-140">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="76174-141">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="76174-141">Do one of the following:</span></span>

- <span data-ttu-id="76174-142">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="76174-142">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="76174-143">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="76174-143">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="76174-144">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="76174-144">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="76174-145">Příklad:</span><span class="sxs-lookup"><span data-stu-id="76174-145">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="76174-146">Kód</span><span class="sxs-lookup"><span data-stu-id="76174-146">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="76174-147">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="76174-147">Configuration</span></span>

<span data-ttu-id="76174-148">Následující konfiguraci lze použít místo kódu k nastavení služby.</span><span class="sxs-lookup"><span data-stu-id="76174-148">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="76174-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="76174-149">See also</span></span>

- [<span data-ttu-id="76174-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76174-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="76174-151">Zabezpečení přenosu WS</span><span class="sxs-lookup"><span data-stu-id="76174-151">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="76174-152">Přehled zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="76174-152">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="76174-153">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="76174-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
