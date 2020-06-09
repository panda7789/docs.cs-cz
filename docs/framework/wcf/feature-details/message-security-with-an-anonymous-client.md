---
title: Zabezpečení zpráv s anonymním klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 058163c96bba036c3183695bf986b4d0424271ac
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595216"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="48d3e-102">Zabezpečení zpráv s anonymním klientem</span><span class="sxs-lookup"><span data-stu-id="48d3e-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="48d3e-103">V následujícím scénáři vidíte klient a službu zabezpečený službou Windows Communication Foundation (WCF) zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="48d3e-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="48d3e-104">Cílem návrhu je použít zabezpečení zpráv místo zabezpečení přenosu, aby v budoucnu bylo možné podporovat bohatší model založený na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="48d3e-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="48d3e-105">Další informace o používání bohatých deklarací pro autorizaci najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="48d3e-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="48d3e-106">Ukázkovou aplikaci najdete v tématu [zabezpečení zpráv anonymně](../samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="48d3e-106">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="48d3e-107">![Zabezpečení zpráv pomocí anonymního klienta](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="48d3e-107">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="48d3e-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="48d3e-108">Characteristic</span></span>|<span data-ttu-id="48d3e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="48d3e-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="48d3e-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="48d3e-110">Security Mode</span></span>|<span data-ttu-id="48d3e-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="48d3e-111">Message</span></span>|
|<span data-ttu-id="48d3e-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="48d3e-112">Interoperability</span></span>|<span data-ttu-id="48d3e-113">Pouze WCF</span><span class="sxs-lookup"><span data-stu-id="48d3e-113">WCF only</span></span>|
|<span data-ttu-id="48d3e-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="48d3e-114">Authentication (Server)</span></span>|<span data-ttu-id="48d3e-115">Počáteční vyjednávání vyžaduje ověření serveru, ale ne ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="48d3e-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="48d3e-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="48d3e-116">Authentication (Client)</span></span>|<span data-ttu-id="48d3e-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="48d3e-117">None</span></span>|
|<span data-ttu-id="48d3e-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="48d3e-118">Integrity</span></span>|<span data-ttu-id="48d3e-119">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="48d3e-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="48d3e-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="48d3e-120">Confidentiality</span></span>|<span data-ttu-id="48d3e-121">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="48d3e-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="48d3e-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="48d3e-122">Transport</span></span>|<span data-ttu-id="48d3e-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="48d3e-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="48d3e-124">Služba</span><span class="sxs-lookup"><span data-stu-id="48d3e-124">Service</span></span>

<span data-ttu-id="48d3e-125">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="48d3e-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="48d3e-126">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="48d3e-126">Do one of the following:</span></span>

- <span data-ttu-id="48d3e-127">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="48d3e-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="48d3e-128">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="48d3e-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="48d3e-129">Kód</span><span class="sxs-lookup"><span data-stu-id="48d3e-129">Code</span></span>

<span data-ttu-id="48d3e-130">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="48d3e-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="48d3e-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="48d3e-131">Configuration</span></span>

<span data-ttu-id="48d3e-132">Místo kódu lze použít následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="48d3e-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="48d3e-133">Element chování služby se používá k určení certifikátu, který se používá k ověření služby klientovi.</span><span class="sxs-lookup"><span data-stu-id="48d3e-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="48d3e-134">Element Service musí určovat chování pomocí `behaviorConfiguration` atributu.</span><span class="sxs-lookup"><span data-stu-id="48d3e-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="48d3e-135">Element Binding určuje, že typ přihlašovacích údajů klienta je `None` , což umožňuje anonymním klientům používat službu.</span><span class="sxs-lookup"><span data-stu-id="48d3e-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="48d3e-136">Klient</span><span class="sxs-lookup"><span data-stu-id="48d3e-136">Client</span></span>

<span data-ttu-id="48d3e-137">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="48d3e-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="48d3e-138">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="48d3e-138">Do one of the following:</span></span>

- <span data-ttu-id="48d3e-139">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="48d3e-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="48d3e-140">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="48d3e-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="48d3e-141">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="48d3e-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="48d3e-142">Například:</span><span class="sxs-lookup"><span data-stu-id="48d3e-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="48d3e-143">Kód</span><span class="sxs-lookup"><span data-stu-id="48d3e-143">Code</span></span>

<span data-ttu-id="48d3e-144">Následující kód vytvoří instanci klienta.</span><span class="sxs-lookup"><span data-stu-id="48d3e-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="48d3e-145">Vazba používá zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na hodnotu None.</span><span class="sxs-lookup"><span data-stu-id="48d3e-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="48d3e-146">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="48d3e-146">Configuration</span></span>

<span data-ttu-id="48d3e-147">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="48d3e-147">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="48d3e-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="48d3e-148">See also</span></span>

- [<span data-ttu-id="48d3e-149">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="48d3e-149">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="48d3e-150">Zabezpečení distribuované aplikace</span><span class="sxs-lookup"><span data-stu-id="48d3e-150">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="48d3e-151">Zabezpečení zpráv s anonymní metodou</span><span class="sxs-lookup"><span data-stu-id="48d3e-151">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="48d3e-152">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="48d3e-152">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="48d3e-153">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="48d3e-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
