---
title: "Zabezpečení zpráv u klienta Windows bez vyjednávání pověření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f069ff100a2fba1f6bace1d9a81ed69314261eae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="d90e0-102">Zabezpečení zpráv u klienta Windows bez vyjednávání pověření</span><span class="sxs-lookup"><span data-stu-id="d90e0-102">Message Security with a Windows Client without Credential Negotiation</span></span>
<span data-ttu-id="d90e0-103">Následující scénář ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby zabezpečené pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="d90e0-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured by the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="d90e0-104">Službu a klienta jsou ve stejné doméně nebo důvěryhodné domény.</span><span class="sxs-lookup"><span data-stu-id="d90e0-104">Both the service and the client are in the same domain or trusted domains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d90e0-105">Rozdíl mezi tento scénář a [zabezpečení zpráv s klientem Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) je, že tento scénář není vyjednávání přihlašovací údaje služby ve službě před odesláním zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="d90e0-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="d90e0-106">Navíc vzhledem k tomu, že to vyžaduje protokol Kerberos, tento scénář vyžaduje prostředí domény systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d90e0-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>  
  
 <span data-ttu-id="d90e0-107">![Zpráva zabezpečení bez vyjednávání pověření](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="d90e0-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>  
  
|<span data-ttu-id="d90e0-108">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d90e0-108">Characteristic</span></span>|<span data-ttu-id="d90e0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d90e0-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d90e0-110">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d90e0-110">Security Mode</span></span>|<span data-ttu-id="d90e0-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d90e0-111">Message</span></span>|  
|<span data-ttu-id="d90e0-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="d90e0-112">Interoperability</span></span>|<span data-ttu-id="d90e0-113">Ano, WS-zabezpečení s klienty kompatibilní profil token protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="d90e0-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|  
|<span data-ttu-id="d90e0-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="d90e0-114">Authentication (Server)</span></span>|<span data-ttu-id="d90e0-115">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="d90e0-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="d90e0-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="d90e0-116">Authentication (Client)</span></span>|<span data-ttu-id="d90e0-117">Vzájemné ověřování klienta a serveru</span><span class="sxs-lookup"><span data-stu-id="d90e0-117">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="d90e0-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="d90e0-118">Integrity</span></span>|<span data-ttu-id="d90e0-119">Ano</span><span class="sxs-lookup"><span data-stu-id="d90e0-119">Yes</span></span>|  
|<span data-ttu-id="d90e0-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="d90e0-120">Confidentiality</span></span>|<span data-ttu-id="d90e0-121">Ano</span><span class="sxs-lookup"><span data-stu-id="d90e0-121">Yes</span></span>|  
|<span data-ttu-id="d90e0-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="d90e0-122">Transport</span></span>|<span data-ttu-id="d90e0-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="d90e0-123">HTTP</span></span>|  
|<span data-ttu-id="d90e0-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="d90e0-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d90e0-125">Služba</span><span class="sxs-lookup"><span data-stu-id="d90e0-125">Service</span></span>  
 <span data-ttu-id="d90e0-126">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="d90e0-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d90e0-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="d90e0-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="d90e0-128">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d90e0-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="d90e0-129">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="d90e0-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d90e0-130">Kód</span><span class="sxs-lookup"><span data-stu-id="d90e0-130">Code</span></span>  
 <span data-ttu-id="d90e0-131">Následující kód vytvoří koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="d90e0-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="d90e0-132">Kód zakáže vyjednávání pověření služby a zřízení tokenu kontextu zabezpečení (SCT).</span><span class="sxs-lookup"><span data-stu-id="d90e0-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d90e0-133">Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, uživatelský účet služby musí mít přístup k hlavní název služby (SPN) registrované domény služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d90e0-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="d90e0-134">Můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="d90e0-134">You can do this in two ways:</span></span>  
  
1.  <span data-ttu-id="d90e0-135">Použití `NetworkService` nebo `LocalSystem` účet ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="d90e0-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="d90e0-136">Protože tyto účty mít přístup k počítači hlavní název služby, který je vytvořen, když je počítač připojen k doméně služby Active Directory [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automaticky vygeneruje správné element SPN uvnitř koncový bod služby v metadatech služby (webové služby Popis jazyk nebo WSDL).</span><span class="sxs-lookup"><span data-stu-id="d90e0-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>  
  
2.  <span data-ttu-id="d90e0-137">Použijte libovolný účet domény služby Active Directory ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="d90e0-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="d90e0-138">V takovém případě musíte vytvořit název SPN pro příslušný účet domény.</span><span class="sxs-lookup"><span data-stu-id="d90e0-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="d90e0-139">Jeden způsob, jak to provést, je pomocí nástroje Setspn.exe nástroj.</span><span class="sxs-lookup"><span data-stu-id="d90e0-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="d90e0-140">Po vytvoření názvu SPN pro účet služby konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] publikovat tento hlavní název služby klientům služby prostřednictvím jeho metadata (WSDL).</span><span class="sxs-lookup"><span data-stu-id="d90e0-140">Once the SPN is created for the service's account, configure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="d90e0-141">To se provádí nastavením identitu koncového bodu pro zveřejněné koncový bod, buď když konfiguračního souboru aplikace nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="d90e0-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="d90e0-142">Následující příklad publikuje identitu prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="d90e0-142">The following example publishes the identity programmatically.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d90e0-143">Hlavní názvy služby SPN, protokol Kerberos a služby Active Directory, najdete v části [Kerberos technické Supplement pro Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="d90e0-143"> SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d90e0-144">koncový bod identity, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="d90e0-144"> endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a><span data-ttu-id="d90e0-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d90e0-145">Configuration</span></span>  
 <span data-ttu-id="d90e0-146">Následující konfigurace můžete použít místo kód.</span><span class="sxs-lookup"><span data-stu-id="d90e0-146">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="d90e0-147">Klient</span><span class="sxs-lookup"><span data-stu-id="d90e0-147">Client</span></span>  
 <span data-ttu-id="d90e0-148">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="d90e0-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d90e0-149">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="d90e0-149">Do one of the following:</span></span>  
  
-   <span data-ttu-id="d90e0-150">Vytvořte samostatnou klienta pomocí kódu (a kód klienta).</span><span class="sxs-lookup"><span data-stu-id="d90e0-150">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="d90e0-151">Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d90e0-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d90e0-152">Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d90e0-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d90e0-153">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d90e0-153">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="d90e0-154">Kód</span><span class="sxs-lookup"><span data-stu-id="d90e0-154">Code</span></span>  
 <span data-ttu-id="d90e0-155">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="d90e0-155">The following code configures the client.</span></span> <span data-ttu-id="d90e0-156">Režim zabezpečení je nastaven na zprávu, a typu pověření klienta je nastaven na hodnotu Windows.</span><span class="sxs-lookup"><span data-stu-id="d90e0-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="d90e0-157">Všimněte si, že <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnosti jsou nastaveny na `false`.</span><span class="sxs-lookup"><span data-stu-id="d90e0-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d90e0-158">Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, musí být klient nakonfigurované účtu služby SPN před zahájením komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="d90e0-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="d90e0-159">Klient použije SPN se získat token protokolu Kerberos k ověřování a k zabezpečení komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="d90e0-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="d90e0-160">Následující příklad ukazuje, jak nakonfigurovat klienta služby SPN.</span><span class="sxs-lookup"><span data-stu-id="d90e0-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="d90e0-161">Pokud používáte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienta, názvu služby SPN se automaticky rozšíří do klienta z metadat služby (WSDL), pokud obsahuje metadata služby Tyto informace.</span><span class="sxs-lookup"><span data-stu-id="d90e0-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d90e0-162">Postup konfigurace služby, které chcete zahrnout jeho SPN služby metadata, najdete v části "Služba" dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d90e0-162"> how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>  
>   
>  <span data-ttu-id="d90e0-163">Další informace o SPN, protokolu Kerberos a služby Active Directory najdete v tématu [Kerberos technické Supplement pro Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="d90e0-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d90e0-164">koncový bod identity, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="d90e0-164"> endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a><span data-ttu-id="d90e0-165">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d90e0-165">Configuration</span></span>  
 <span data-ttu-id="d90e0-166">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="d90e0-166">The following code configures the client.</span></span> <span data-ttu-id="d90e0-167">Všimněte si, že [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element musí být nastaven tak, aby odpovídaly SPN služby as registrované pro účet služby v doméně služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d90e0-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d90e0-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="d90e0-168">See Also</span></span>  
 [<span data-ttu-id="d90e0-169">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d90e0-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d90e0-170">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d90e0-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d90e0-171">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="d90e0-171">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
