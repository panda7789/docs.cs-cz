---
title: Zabezpečení přenosu pomocí anonymního klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: c3e44c87dfa70ac3a7acc5a83ac596efc22b6155
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344761"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="de8aa-102">Zabezpečení přenosu pomocí anonymního klienta</span><span class="sxs-lookup"><span data-stu-id="de8aa-102">Transport security with an anonymous client</span></span>

<span data-ttu-id="de8aa-103">Tento scénář Windows Communication Foundation (WCF) používá k zajištění důvěrnosti a integrity zabezpečení přenosu (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="de8aa-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="de8aa-104">Server musí být ověřený s certifikátem SSL (Secure Sockets Layer) (SSL) a klienti musí důvěřovat certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="de8aa-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="de8aa-105">Klient není ověřen žádným mechanismem a proto je anonymní.</span><span class="sxs-lookup"><span data-stu-id="de8aa-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="de8aa-106">Ukázkovou aplikaci najdete v tématu [zabezpečení přenosu v protokolu WS](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="de8aa-106">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="de8aa-107">Další informace o zabezpečení přenosu najdete v tématu [Přehled zabezpečení přenosu](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="de8aa-107">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="de8aa-108">Další informace o používání certifikátu se službou najdete v tématu [práce s certifikáty](working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="de8aa-108">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Použití zabezpečení přenosu u anonymního klienta](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="de8aa-110">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="de8aa-110">Characteristic</span></span>|<span data-ttu-id="de8aa-111">Popis</span><span class="sxs-lookup"><span data-stu-id="de8aa-111">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="de8aa-112">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="de8aa-112">Security Mode</span></span>|<span data-ttu-id="de8aa-113">Doprava</span><span class="sxs-lookup"><span data-stu-id="de8aa-113">Transport</span></span>|
|<span data-ttu-id="de8aa-114">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="de8aa-114">Interoperability</span></span>|<span data-ttu-id="de8aa-115">Se stávajícími webovými službami a klienty</span><span class="sxs-lookup"><span data-stu-id="de8aa-115">With existing Web services and clients</span></span>|
|<span data-ttu-id="de8aa-116">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="de8aa-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="de8aa-117">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="de8aa-117">Authentication (Client)</span></span>|<span data-ttu-id="de8aa-118">Ano</span><span class="sxs-lookup"><span data-stu-id="de8aa-118">Yes</span></span><br /><br /> <span data-ttu-id="de8aa-119">Úroveň aplikace (žádná podpora WCF)</span><span class="sxs-lookup"><span data-stu-id="de8aa-119">Application level (no WCF support)</span></span>|
|<span data-ttu-id="de8aa-120">Integrita</span><span class="sxs-lookup"><span data-stu-id="de8aa-120">Integrity</span></span>|<span data-ttu-id="de8aa-121">Ano</span><span class="sxs-lookup"><span data-stu-id="de8aa-121">Yes</span></span>|
|<span data-ttu-id="de8aa-122">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="de8aa-122">Confidentiality</span></span>|<span data-ttu-id="de8aa-123">Ano</span><span class="sxs-lookup"><span data-stu-id="de8aa-123">Yes</span></span>|
|<span data-ttu-id="de8aa-124">Doprava</span><span class="sxs-lookup"><span data-stu-id="de8aa-124">Transport</span></span>|<span data-ttu-id="de8aa-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="de8aa-125">HTTPS</span></span>|
|<span data-ttu-id="de8aa-126">Vazba</span><span class="sxs-lookup"><span data-stu-id="de8aa-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="de8aa-127">Service</span><span class="sxs-lookup"><span data-stu-id="de8aa-127">Service</span></span>

<span data-ttu-id="de8aa-128">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="de8aa-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="de8aa-129">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="de8aa-129">Do one of the following:</span></span>

- <span data-ttu-id="de8aa-130">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="de8aa-130">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="de8aa-131">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="de8aa-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="de8aa-132">Kód</span><span class="sxs-lookup"><span data-stu-id="de8aa-132">Code</span></span>

<span data-ttu-id="de8aa-133">Následující kód ukazuje, jak vytvořit koncový bod pomocí zabezpečení přenosu:</span><span class="sxs-lookup"><span data-stu-id="de8aa-133">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="de8aa-134">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="de8aa-134">Configuration</span></span>

<span data-ttu-id="de8aa-135">Následující kód nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="de8aa-135">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="de8aa-136">Klient není ověřen žádným mechanismem a proto je anonymní.</span><span class="sxs-lookup"><span data-stu-id="de8aa-136">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

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

## <a name="client"></a><span data-ttu-id="de8aa-137">Klient</span><span class="sxs-lookup"><span data-stu-id="de8aa-137">Client</span></span>

<span data-ttu-id="de8aa-138">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="de8aa-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="de8aa-139">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="de8aa-139">Do one of the following:</span></span>

- <span data-ttu-id="de8aa-140">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="de8aa-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="de8aa-141">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="de8aa-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="de8aa-142">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="de8aa-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="de8aa-143">Příklad:</span><span class="sxs-lookup"><span data-stu-id="de8aa-143">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="de8aa-144">Kód</span><span class="sxs-lookup"><span data-stu-id="de8aa-144">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="de8aa-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="de8aa-145">Configuration</span></span>

<span data-ttu-id="de8aa-146">Následující konfiguraci lze použít místo kódu k nastavení služby.</span><span class="sxs-lookup"><span data-stu-id="de8aa-146">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="de8aa-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de8aa-147">See also</span></span>

- [<span data-ttu-id="de8aa-148">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="de8aa-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="de8aa-149">Zabezpečení přenosu WS</span><span class="sxs-lookup"><span data-stu-id="de8aa-149">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="de8aa-150">Přehled zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="de8aa-150">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="de8aa-151">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="de8aa-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
