---
title: Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 7845bc45d0baecb07e4c03531f21d900c4e23bf7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595242"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="bb794-102">Zabezpečení zpráv u klienta Windows bez vyjednávání pověření</span><span class="sxs-lookup"><span data-stu-id="bb794-102">Message Security with a Windows Client without Credential Negotiation</span></span>

<span data-ttu-id="bb794-103">V následujícím scénáři vidíte klienta služby a službu Windows Communication Foundation (WCF) zabezpečený protokolem Kerberos.</span><span class="sxs-lookup"><span data-stu-id="bb794-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>

<span data-ttu-id="bb794-104">Služba i klient jsou ve stejné doméně nebo důvěryhodných doménách.</span><span class="sxs-lookup"><span data-stu-id="bb794-104">Both the service and the client are in the same domain or trusted domains.</span></span>

> [!NOTE]
> <span data-ttu-id="bb794-105">Rozdíl mezi tímto scénářem a [zabezpečením zprávy pomocí klienta Windows](message-security-with-a-windows-client.md) je v tom, že tento scénář nevyjednává pověření služby se službou před odesláním zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="bb794-105">The difference between this scenario and [Message Security with a Windows Client](message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="bb794-106">Navíc vzhledem k tomu, že tento scénář vyžaduje protokol Kerberos, vyžaduje prostředí domény systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bb794-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>

<span data-ttu-id="bb794-107">![Zabezpečení zpráv bez vyjednávání přihlašovacích údajů](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="bb794-107">![Message security without credential negotiation](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>

|<span data-ttu-id="bb794-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="bb794-108">Characteristic</span></span>|<span data-ttu-id="bb794-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bb794-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="bb794-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bb794-110">Security Mode</span></span>|<span data-ttu-id="bb794-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bb794-111">Message</span></span>|
|<span data-ttu-id="bb794-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="bb794-112">Interoperability</span></span>|<span data-ttu-id="bb794-113">Ano, WS-Security s kompatibilními klienty profilování Kerberos</span><span class="sxs-lookup"><span data-stu-id="bb794-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|
|<span data-ttu-id="bb794-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="bb794-114">Authentication (Server)</span></span>|<span data-ttu-id="bb794-115">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="bb794-115">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="bb794-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="bb794-116">Authentication (Client)</span></span>|<span data-ttu-id="bb794-117">Vzájemné ověřování serveru a klienta</span><span class="sxs-lookup"><span data-stu-id="bb794-117">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="bb794-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="bb794-118">Integrity</span></span>|<span data-ttu-id="bb794-119">Yes</span><span class="sxs-lookup"><span data-stu-id="bb794-119">Yes</span></span>|
|<span data-ttu-id="bb794-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="bb794-120">Confidentiality</span></span>|<span data-ttu-id="bb794-121">Yes</span><span class="sxs-lookup"><span data-stu-id="bb794-121">Yes</span></span>|
|<span data-ttu-id="bb794-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="bb794-122">Transport</span></span>|<span data-ttu-id="bb794-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="bb794-123">HTTP</span></span>|
|<span data-ttu-id="bb794-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="bb794-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="bb794-125">Služba</span><span class="sxs-lookup"><span data-stu-id="bb794-125">Service</span></span>

<span data-ttu-id="bb794-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="bb794-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="bb794-127">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="bb794-127">Do one of the following:</span></span>

- <span data-ttu-id="bb794-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="bb794-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="bb794-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="bb794-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="bb794-130">Kód</span><span class="sxs-lookup"><span data-stu-id="bb794-130">Code</span></span>

<span data-ttu-id="bb794-131">Následující kód vytvoří koncový bod služby, který používá zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="bb794-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="bb794-132">Kód zakazuje vyjednávání pověření služby a nakládání s tokenem kontextu zabezpečení (SCT).</span><span class="sxs-lookup"><span data-stu-id="bb794-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>

> [!NOTE]
> <span data-ttu-id="bb794-133">Chcete-li použít typ přihlašovacích údajů systému Windows bez vyjednávání, musí mít uživatelský účet služby přístup k hlavnímu názvu služby (SPN), který je zaregistrován v doméně služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="bb794-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="bb794-134">To můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="bb794-134">You can do this in two ways:</span></span>

1. <span data-ttu-id="bb794-135">Použijte `NetworkService` účet nebo `LocalSystem` ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="bb794-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="bb794-136">Vzhledem k tomu, že tyto účty mají přístup k hlavnímu názvu služby počítače, který je vytvořen při připojení počítače k doméně služby Active Directory, služba WCF automaticky vygeneruje správný element SPN uvnitř koncového bodu služby v metadatech služby (Web Services Description Language nebo WSDL).</span><span class="sxs-lookup"><span data-stu-id="bb794-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>

2. <span data-ttu-id="bb794-137">Ke spuštění služby použijte libovolný účet domény služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="bb794-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="bb794-138">V takovém případě musíte pro tento doménový účet vytvořit hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="bb794-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="bb794-139">Jedním ze způsobů, jak to provést, je použít nástroj Setspn. exe Utility.</span><span class="sxs-lookup"><span data-stu-id="bb794-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="bb794-140">Po vytvoření hlavního názvu služby (SPN) pro účet služby nakonfigurujte WCF pro publikování tohoto hlavního názvu služby do klientů služby prostřednictvím metadat (WSDL).</span><span class="sxs-lookup"><span data-stu-id="bb794-140">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="bb794-141">To se provádí nastavením identity koncového bodu pro vystavený koncový bod, a to buď pomocí konfiguračního souboru aplikace, nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="bb794-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="bb794-142">Následující příklad publikuje identitu programově.</span><span class="sxs-lookup"><span data-stu-id="bb794-142">The following example publishes the identity programmatically.</span></span>

<span data-ttu-id="bb794-143">Další informace o SPN, protokolu Kerberos a službě Active Directory najdete v tématu [Kerberos Technical dodatk pro Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="bb794-143">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="bb794-144">Další informace o identitách koncových bodů najdete v tématu [režimy ověřování SecurityBindingElement](securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="bb794-144">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a><span data-ttu-id="bb794-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="bb794-145">Configuration</span></span>

<span data-ttu-id="bb794-146">Místo kódu lze použít následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="bb794-146">The following configuration can be used instead of the code.</span></span>

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

## <a name="client"></a><span data-ttu-id="bb794-147">Klient</span><span class="sxs-lookup"><span data-stu-id="bb794-147">Client</span></span>

<span data-ttu-id="bb794-148">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="bb794-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="bb794-149">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="bb794-149">Do one of the following:</span></span>

- <span data-ttu-id="bb794-150">Vytvořte samostatného klienta pomocí kódu (a kódu klienta).</span><span class="sxs-lookup"><span data-stu-id="bb794-150">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="bb794-151">Vytvořte klienta, který nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="bb794-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="bb794-152">Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument.</span><span class="sxs-lookup"><span data-stu-id="bb794-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="bb794-153">Například:</span><span class="sxs-lookup"><span data-stu-id="bb794-153">For example:</span></span>

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="bb794-154">Kód</span><span class="sxs-lookup"><span data-stu-id="bb794-154">Code</span></span>

<span data-ttu-id="bb794-155">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="bb794-155">The following code configures the client.</span></span> <span data-ttu-id="bb794-156">Režim zabezpečení je nastaven na hodnotu zpráva a typ přihlašovacích údajů klienta je nastaven na hodnotu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb794-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="bb794-157">Všimněte si, <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> že <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnosti a jsou nastaveny na `false` .</span><span class="sxs-lookup"><span data-stu-id="bb794-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="bb794-158">Chcete-li použít typ přihlašovacích údajů systému Windows bez vyjednávání, musí být klient nakonfigurován pomocí SPN účtu služby před zahájením komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="bb794-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="bb794-159">Klient používá hlavní název služby (SPN) k získání tokenu protokolu Kerberos k ověření a zabezpečení komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="bb794-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="bb794-160">Následující příklad ukazuje, jak nakonfigurovat klienta nástroje pomocí hlavního názvu služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="bb794-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="bb794-161">Pokud k vygenerování klienta používáte [Nástroj pro metadata ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , hlavní název služby (SPN) se automaticky rozšíří na klienta z metadat služby (WSDL), pokud metadata služby obsahují tyto informace.</span><span class="sxs-lookup"><span data-stu-id="bb794-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="bb794-162">Další informace o tom, jak nakonfigurovat službu tak, aby obsahovala hlavní název služby (SPN) v metadatech služby, najdete v části služba dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="bb794-162">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>
>
> <span data-ttu-id="bb794-163">Další informace o hlavních názvových názvech, protokolech Kerberos a službě Active Directory najdete v tématu [Kerberos Technical dodatk pro Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="bb794-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="bb794-164">Další informace o identitách koncových bodů najdete v tématu [režimy ověřování SecurityBindingElement](securitybindingelement-authentication-modes.md) .</span><span class="sxs-lookup"><span data-stu-id="bb794-164">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md) topic.</span></span>

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a><span data-ttu-id="bb794-165">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="bb794-165">Configuration</span></span>

<span data-ttu-id="bb794-166">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="bb794-166">The following code configures the client.</span></span> <span data-ttu-id="bb794-167">Všimněte si, že [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) element musí být nastaven tak, aby odpovídal názvu SPN služby, jak je zaregistrován pro účet služby v doméně služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="bb794-167">Note that the [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bb794-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb794-168">See also</span></span>

- [<span data-ttu-id="bb794-169">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bb794-169">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="bb794-170">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="bb794-170">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="bb794-171">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bb794-171">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
