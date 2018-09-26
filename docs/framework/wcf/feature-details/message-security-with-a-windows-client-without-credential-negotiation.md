---
title: Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
author: BrucePerlerMS
ms.openlocfilehash: 8ca3a3e44386c1576610fe3d42f8697c66bee9ab
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171254"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="4a48a-102">Zabezpečení zpráv u klienta Windows bez vyjednávání pověření</span><span class="sxs-lookup"><span data-stu-id="4a48a-102">Message Security with a Windows Client without Credential Negotiation</span></span>
<span data-ttu-id="4a48a-103">Následující scénář ukazuje klienta Windows Communication Foundation (WCF) a služby zabezpečené pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="4a48a-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="4a48a-104">Službu a klienta jsou ve stejné doméně nebo důvěryhodné domény.</span><span class="sxs-lookup"><span data-stu-id="4a48a-104">Both the service and the client are in the same domain or trusted domains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a48a-105">Rozdíl mezi tento scénář a [zabezpečení zpráv pomocí klienta Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) je, že tento scénář není vyjednávání přihlašovacích údajů pro služby ve službě před odesláním zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="4a48a-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="4a48a-106">Navíc vzhledem k tomu, že to vyžaduje protokol Kerberos, tento scénář vyžaduje prostředí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="4a48a-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>  
  
 <span data-ttu-id="4a48a-107">![Zabezpečení bez vyjednávání přihlašovacích údajů zpráv](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="4a48a-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>  
  
|<span data-ttu-id="4a48a-108">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="4a48a-108">Characteristic</span></span>|<span data-ttu-id="4a48a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4a48a-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4a48a-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4a48a-110">Security Mode</span></span>|<span data-ttu-id="4a48a-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="4a48a-111">Message</span></span>|  
|<span data-ttu-id="4a48a-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="4a48a-112">Interoperability</span></span>|<span data-ttu-id="4a48a-113">Ano, WS-Security s klienty kompatibilní profilu token protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="4a48a-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|  
|<span data-ttu-id="4a48a-114">Ověření (Server)</span><span class="sxs-lookup"><span data-stu-id="4a48a-114">Authentication (Server)</span></span>|<span data-ttu-id="4a48a-115">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="4a48a-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="4a48a-116">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="4a48a-116">Authentication (Client)</span></span>|<span data-ttu-id="4a48a-117">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="4a48a-117">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="4a48a-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="4a48a-118">Integrity</span></span>|<span data-ttu-id="4a48a-119">Ano</span><span class="sxs-lookup"><span data-stu-id="4a48a-119">Yes</span></span>|  
|<span data-ttu-id="4a48a-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="4a48a-120">Confidentiality</span></span>|<span data-ttu-id="4a48a-121">Ano</span><span class="sxs-lookup"><span data-stu-id="4a48a-121">Yes</span></span>|  
|<span data-ttu-id="4a48a-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="4a48a-122">Transport</span></span>|<span data-ttu-id="4a48a-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="4a48a-123">HTTP</span></span>|  
|<span data-ttu-id="4a48a-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="4a48a-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="4a48a-125">Služba</span><span class="sxs-lookup"><span data-stu-id="4a48a-125">Service</span></span>  
 <span data-ttu-id="4a48a-126">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="4a48a-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4a48a-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="4a48a-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="4a48a-128">Vytvoření samostatné služby pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4a48a-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="4a48a-129">Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="4a48a-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4a48a-130">Kód</span><span class="sxs-lookup"><span data-stu-id="4a48a-130">Code</span></span>  
 <span data-ttu-id="4a48a-131">Následující kód vytvoří koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="4a48a-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="4a48a-132">Kód zakáže vyjednávání přihlašovacích údajů služby a zřízení token kontextu zabezpečení (SCT).</span><span class="sxs-lookup"><span data-stu-id="4a48a-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a48a-133">Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, služby uživatelský účet musí mít přístup k hlavní název služby (SPN), který je zaregistrován s doménou služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="4a48a-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="4a48a-134">Můžete to provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="4a48a-134">You can do this in two ways:</span></span>  
  
1.  <span data-ttu-id="4a48a-135">Použití `NetworkService` nebo `LocalSystem` účet ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="4a48a-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="4a48a-136">Vzhledem k tomu, že tyto účty mají přístup k počítači hlavní název služby, který je vytvořen, když je počítač připojen k doméně služby Active Directory, WCF automaticky generuje elementu řádné SPN uvnitř koncového bodu služby v metadatech služby (Web Services Description Jazyk, nebo WSDL).</span><span class="sxs-lookup"><span data-stu-id="4a48a-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>  
  
2.  <span data-ttu-id="4a48a-137">Použijte libovolný účet domény služby Active Directory ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="4a48a-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="4a48a-138">V takovém případě potřebujete vytvořit název SPN pro příslušný účet domény.</span><span class="sxs-lookup"><span data-stu-id="4a48a-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="4a48a-139">Jeden způsob, jak to je použití nástroje nástroje Setspn.exe.</span><span class="sxs-lookup"><span data-stu-id="4a48a-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="4a48a-140">Po vytvoření názvu SPN pro účet služby konfigurace WCF k publikování této hlavní název služby klientům služby prostřednictvím jeho metadat (WSDL).</span><span class="sxs-lookup"><span data-stu-id="4a48a-140">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="4a48a-141">To se provádí nastavením identitě koncového bodu vystavené koncového bodu, buď když k konfigurační soubor aplikace nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="4a48a-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="4a48a-142">Následující příklad publikuje identitu prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="4a48a-142">The following example publishes the identity programmatically.</span></span>  
  
 <span data-ttu-id="4a48a-143">Další informace o SPN, protokol Kerberos a Active Directory, naleznete v tématu [Kerberos technické Supplement pro Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="4a48a-143">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span></span> <span data-ttu-id="4a48a-144">Další informace o identitách koncový bod, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="4a48a-144">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a><span data-ttu-id="4a48a-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="4a48a-145">Configuration</span></span>  
 <span data-ttu-id="4a48a-146">Následující konfigurace je možné použít místo kódu.</span><span class="sxs-lookup"><span data-stu-id="4a48a-146">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="4a48a-147">Klient</span><span class="sxs-lookup"><span data-stu-id="4a48a-147">Client</span></span>  
 <span data-ttu-id="4a48a-148">Následující kód a konfigurace mají běžet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="4a48a-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4a48a-149">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="4a48a-149">Do one of the following:</span></span>  
  
-   <span data-ttu-id="4a48a-150">Vytvoření samostatného klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="4a48a-150">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="4a48a-151">Vytvoření klienta, která nedefinuje žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4a48a-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="4a48a-152">Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4a48a-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="4a48a-153">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4a48a-153">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="4a48a-154">Kód</span><span class="sxs-lookup"><span data-stu-id="4a48a-154">Code</span></span>  
 <span data-ttu-id="4a48a-155">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="4a48a-155">The following code configures the client.</span></span> <span data-ttu-id="4a48a-156">Režim zabezpečení je nastavena na zprávu, a typ pověření klienta je nastaven na Windows.</span><span class="sxs-lookup"><span data-stu-id="4a48a-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="4a48a-157">Všimněte si, <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnosti jsou nastaveny na `false`.</span><span class="sxs-lookup"><span data-stu-id="4a48a-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a48a-158">Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, musí klient nakonfigurovaný s účtem služby SPN před zahájením komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="4a48a-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="4a48a-159">Klient použije hlavní název služby se získat token protokolu Kerberos k ověření a zabezpečení komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="4a48a-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="4a48a-160">Následující příklad ukazuje, jak nakonfigurovat klienta služby SPN.</span><span class="sxs-lookup"><span data-stu-id="4a48a-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="4a48a-161">Pokud používáte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Pokud chcete vygenerovat klienta, název služby SPN se automaticky rozšíří do klienta z metadat služby (WSDL), pokud obsahuje metadata služby Tyto informace.</span><span class="sxs-lookup"><span data-stu-id="4a48a-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="4a48a-162">Další informace o tom, jak nakonfigurovat službu zahrnout jeho hlavního názvu služby metadata služby najdete v části "Služba" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4a48a-162">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>  
>   
>  <span data-ttu-id="4a48a-163">Další informace o hlavní názvy služby protokolu Kerberos a Active Directory najdete v tématu [Kerberos technické Supplement pro Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="4a48a-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span></span> <span data-ttu-id="4a48a-164">Další informace o identitách koncový bod, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="4a48a-164">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a><span data-ttu-id="4a48a-165">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="4a48a-165">Configuration</span></span>  
 <span data-ttu-id="4a48a-166">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="4a48a-166">The following code configures the client.</span></span> <span data-ttu-id="4a48a-167">Všimněte si, [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elementu musí být nastavena tak, aby odpovídaly služby SPN, protože registrovaný pro účet služby v doméně služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="4a48a-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a48a-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a48a-168">See Also</span></span>  
 [<span data-ttu-id="4a48a-169">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4a48a-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="4a48a-170">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="4a48a-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="4a48a-171">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="4a48a-171">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
