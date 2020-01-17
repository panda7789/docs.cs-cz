---
title: Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: d3b05a1786131a119d516edeba0d6e8e24289f87
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212032"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="22b18-102">Zabezpečení zpráv u klienta Windows bez vyjednávání pověření</span><span class="sxs-lookup"><span data-stu-id="22b18-102">Message Security with a Windows Client without Credential Negotiation</span></span>

<span data-ttu-id="22b18-103">V následujícím scénáři vidíte klienta služby a službu Windows Communication Foundation (WCF) zabezpečený protokolem Kerberos.</span><span class="sxs-lookup"><span data-stu-id="22b18-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>

<span data-ttu-id="22b18-104">Služba i klient jsou ve stejné doméně nebo důvěryhodných doménách.</span><span class="sxs-lookup"><span data-stu-id="22b18-104">Both the service and the client are in the same domain or trusted domains.</span></span>

> [!NOTE]
> <span data-ttu-id="22b18-105">Rozdíl mezi tímto scénářem a [zabezpečením zprávy pomocí klienta Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) je v tom, že tento scénář nevyjednává pověření služby se službou před odesláním zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="22b18-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="22b18-106">Navíc vzhledem k tomu, že tento scénář vyžaduje protokol Kerberos, vyžaduje prostředí domény systému Windows.</span><span class="sxs-lookup"><span data-stu-id="22b18-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>

<span data-ttu-id="22b18-107">![Zabezpečení zpráv bez vyjednávání přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="22b18-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>

|<span data-ttu-id="22b18-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="22b18-108">Characteristic</span></span>|<span data-ttu-id="22b18-109">Popis</span><span class="sxs-lookup"><span data-stu-id="22b18-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="22b18-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="22b18-110">Security Mode</span></span>|<span data-ttu-id="22b18-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="22b18-111">Message</span></span>|
|<span data-ttu-id="22b18-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="22b18-112">Interoperability</span></span>|<span data-ttu-id="22b18-113">Ano, WS-Security s kompatibilními klienty profilování Kerberos</span><span class="sxs-lookup"><span data-stu-id="22b18-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|
|<span data-ttu-id="22b18-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="22b18-114">Authentication (Server)</span></span>|<span data-ttu-id="22b18-115">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="22b18-115">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="22b18-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="22b18-116">Authentication (Client)</span></span>|<span data-ttu-id="22b18-117">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="22b18-117">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="22b18-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="22b18-118">Integrity</span></span>|<span data-ttu-id="22b18-119">Ano</span><span class="sxs-lookup"><span data-stu-id="22b18-119">Yes</span></span>|
|<span data-ttu-id="22b18-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="22b18-120">Confidentiality</span></span>|<span data-ttu-id="22b18-121">Ano</span><span class="sxs-lookup"><span data-stu-id="22b18-121">Yes</span></span>|
|<span data-ttu-id="22b18-122">Doprava</span><span class="sxs-lookup"><span data-stu-id="22b18-122">Transport</span></span>|<span data-ttu-id="22b18-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="22b18-123">HTTP</span></span>|
|<span data-ttu-id="22b18-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="22b18-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="22b18-125">Service</span><span class="sxs-lookup"><span data-stu-id="22b18-125">Service</span></span>

<span data-ttu-id="22b18-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="22b18-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="22b18-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="22b18-127">Do one of the following:</span></span>

- <span data-ttu-id="22b18-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="22b18-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="22b18-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="22b18-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="22b18-130">Kód</span><span class="sxs-lookup"><span data-stu-id="22b18-130">Code</span></span>

<span data-ttu-id="22b18-131">Následující kód vytvoří koncový bod služby, který používá zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="22b18-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="22b18-132">Kód zakazuje vyjednávání pověření služby a nakládání s tokenem kontextu zabezpečení (SCT).</span><span class="sxs-lookup"><span data-stu-id="22b18-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>

> [!NOTE]
> <span data-ttu-id="22b18-133">Chcete-li použít typ přihlašovacích údajů systému Windows bez vyjednávání, musí mít uživatelský účet služby přístup k hlavnímu názvu služby (SPN), který je zaregistrován v doméně služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="22b18-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="22b18-134">To můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="22b18-134">You can do this in two ways:</span></span>

1. <span data-ttu-id="22b18-135">Ke spuštění služby použijte účet `NetworkService` nebo `LocalSystem`.</span><span class="sxs-lookup"><span data-stu-id="22b18-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="22b18-136">Vzhledem k tomu, že tyto účty mají přístup k hlavnímu názvu služby počítače, který se vytvoří, když se počítač připojí k doméně služby Active Directory, WCF automaticky vygeneruje správný element SPN v rámci koncového bodu služby v metadatech služby (popis webových služeb Jazyk nebo WSDL).</span><span class="sxs-lookup"><span data-stu-id="22b18-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>

2. <span data-ttu-id="22b18-137">Ke spuštění služby použijte libovolný účet domény služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="22b18-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="22b18-138">V takovém případě musíte pro tento doménový účet vytvořit hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="22b18-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="22b18-139">Jedním ze způsobů, jak to provést, je použít nástroj Setspn. exe Utility.</span><span class="sxs-lookup"><span data-stu-id="22b18-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="22b18-140">Po vytvoření hlavního názvu služby (SPN) pro účet služby nakonfigurujte WCF pro publikování tohoto hlavního názvu služby do klientů služby prostřednictvím metadat (WSDL).</span><span class="sxs-lookup"><span data-stu-id="22b18-140">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="22b18-141">To se provádí nastavením identity koncového bodu pro vystavený koncový bod, a to buď pomocí konfiguračního souboru aplikace, nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="22b18-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="22b18-142">Následující příklad publikuje identitu programově.</span><span class="sxs-lookup"><span data-stu-id="22b18-142">The following example publishes the identity programmatically.</span></span>

<span data-ttu-id="22b18-143">Další informace o SPN, protokolu Kerberos a službě Active Directory najdete v tématu [Kerberos Technical dodatk pro Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="22b18-143">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="22b18-144">Další informace o identitách koncových bodů najdete v tématu [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="22b18-144">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a><span data-ttu-id="22b18-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="22b18-145">Configuration</span></span>

<span data-ttu-id="22b18-146">Místo kódu lze použít následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="22b18-146">The following configuration can be used instead of the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors />
    <services>
      <service behaviorConfiguration="" name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="KerberosBinding"
                  name="WSHttpBinding_ICalculator"
                  contract="ServiceModel.ICalculator"
                  listenUri="net.tcp://localhost/metadata" >
         <identity>
            <servicePrincipalName value="service_spn_name" />
         </identity>
        </endpoint>
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="KerberosBinding">
          <security>
            <message negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="22b18-147">Klient</span><span class="sxs-lookup"><span data-stu-id="22b18-147">Client</span></span>

<span data-ttu-id="22b18-148">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="22b18-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="22b18-149">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="22b18-149">Do one of the following:</span></span>

- <span data-ttu-id="22b18-150">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="22b18-150">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="22b18-151">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="22b18-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="22b18-152">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="22b18-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="22b18-153">Příklad:</span><span class="sxs-lookup"><span data-stu-id="22b18-153">For example:</span></span>

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="22b18-154">Kód</span><span class="sxs-lookup"><span data-stu-id="22b18-154">Code</span></span>

<span data-ttu-id="22b18-155">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="22b18-155">The following code configures the client.</span></span> <span data-ttu-id="22b18-156">Režim zabezpečení je nastaven na hodnotu zpráva a typ přihlašovacích údajů klienta je nastaven na hodnotu Windows.</span><span class="sxs-lookup"><span data-stu-id="22b18-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="22b18-157">Všimněte si, že vlastnosti <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> jsou nastaveny na `false`.</span><span class="sxs-lookup"><span data-stu-id="22b18-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="22b18-158">Chcete-li použít typ přihlašovacích údajů systému Windows bez vyjednávání, musí být klient nakonfigurován pomocí SPN účtu služby před zahájením komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="22b18-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="22b18-159">Klient používá hlavní název služby (SPN) k získání tokenu protokolu Kerberos k ověření a zabezpečení komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="22b18-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="22b18-160">Následující příklad ukazuje, jak nakonfigurovat klienta nástroje pomocí hlavního názvu služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="22b18-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="22b18-161">Pokud k vygenerování klienta používáte [Nástroj pro metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , hlavní název služby (SPN) se automaticky rozšíří na klienta z metadat služby (WSDL), pokud metadata služby obsahují tyto informace.</span><span class="sxs-lookup"><span data-stu-id="22b18-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="22b18-162">Další informace o tom, jak nakonfigurovat službu tak, aby obsahovala hlavní název služby (SPN) v metadatech služby, najdete v části služba dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="22b18-162">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>
>
> <span data-ttu-id="22b18-163">Další informace o hlavních názvových názvech, protokolech Kerberos a službě Active Directory najdete v tématu [Kerberos Technical dodatk pro Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="22b18-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="22b18-164">Další informace o identitách koncových bodů najdete v tématu [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) .</span><span class="sxs-lookup"><span data-stu-id="22b18-164">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a><span data-ttu-id="22b18-165">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="22b18-165">Configuration</span></span>

<span data-ttu-id="22b18-166">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="22b18-166">The following code configures the client.</span></span> <span data-ttu-id="22b18-167">Všimněte si, že [\<element servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) musí být nastaven tak, aby odpovídal názvu SPN služby, jak je zaregistrován pro účet služby v doméně služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="22b18-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://localhost/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator">
        <identity>
          <servicePrincipalName value="service_spn_name" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="22b18-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22b18-168">See also</span></span>

- [<span data-ttu-id="22b18-169">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="22b18-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="22b18-170">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="22b18-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- <span data-ttu-id="22b18-171">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="22b18-171">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
