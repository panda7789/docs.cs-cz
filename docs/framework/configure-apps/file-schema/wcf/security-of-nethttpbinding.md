---
title: '&lt;security&gt; – &lt;netHttpBinding'
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 6357593be17c2d008204598d51610fa3dbf77c27
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527463"
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="967e8-102">&lt;security&gt; – &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="967e8-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="967e8-103">Definuje možnosti zabezpečení [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="967e8-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="967e8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="967e8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="967e8-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="967e8-105">\<bindings></span></span>  
<span data-ttu-id="967e8-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="967e8-106">\<netHttpBinding></span></span>  
<span data-ttu-id="967e8-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="967e8-107">\<binding></span></span>  
<span data-ttu-id="967e8-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="967e8-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="967e8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="967e8-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="967e8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="967e8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="967e8-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="967e8-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="967e8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="967e8-112">Attributes</span></span>  
  
|<span data-ttu-id="967e8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="967e8-113">Attribute</span></span>|<span data-ttu-id="967e8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="967e8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="967e8-115">režim</span><span class="sxs-lookup"><span data-stu-id="967e8-115">mode</span></span>|<span data-ttu-id="967e8-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="967e8-116">Optional.</span></span> <span data-ttu-id="967e8-117">Určuje typ zabezpečení, který se používá.</span><span class="sxs-lookup"><span data-stu-id="967e8-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="967e8-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="967e8-118">The default is `None`.</span></span> <span data-ttu-id="967e8-119">Tento atribut je typu <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="967e8-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="967e8-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="967e8-120">mode Attribute</span></span>  
  
|<span data-ttu-id="967e8-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="967e8-121">Value</span></span>|<span data-ttu-id="967e8-122">Popis</span><span class="sxs-lookup"><span data-stu-id="967e8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="967e8-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="967e8-123">None</span></span>|<span data-ttu-id="967e8-124">-Zprávy nejsou zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="967e8-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="967e8-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="967e8-125">Transport</span></span>|<span data-ttu-id="967e8-126">Zabezpečení je prováděno pomocí přenos protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="967e8-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="967e8-127">Zprávy protokolu SOAP jsou zabezpečené pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="967e8-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="967e8-128">Služba je ověřen u klienta pomocí certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="967e8-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="967e8-129">Klient je ověřený pomocí nebyl typ ClientCredentialType zadán.</span><span class="sxs-lookup"><span data-stu-id="967e8-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="967e8-130">Zpráva</span><span class="sxs-lookup"><span data-stu-id="967e8-130">Message</span></span>|<span data-ttu-id="967e8-131">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="967e8-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="967e8-132">Ve výchozím nastavení je tělo zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="967e8-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="967e8-133">Pro tuto vazbu systému vyžaduje, aby certifikát serveru poskytnuta klientovi mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="967e8-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="967e8-134">Jediné platné `ClientCredentialType` pro tuto vazbu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="967e8-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="967e8-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="967e8-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="967e8-136">Zabezpečení přenosu zajišťují integritu a důvěrnost serveru ověřování.</span><span class="sxs-lookup"><span data-stu-id="967e8-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="967e8-137">Ověření klienta je k dispozici prostřednictvím zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="967e8-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="967e8-138">Tento režim je důležité, když se uživatel ověřuje pomocí uživatelského jména a hesla a nějaké existující nasazení HTTP pro přenos zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="967e8-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="967e8-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="967e8-139">TransportCredentialOnly</span></span>|<span data-ttu-id="967e8-140">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="967e8-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="967e8-141">Poskytuje ověření klienta založené na protokolu http.</span><span class="sxs-lookup"><span data-stu-id="967e8-141">It provides http-based client authentication.</span></span> <span data-ttu-id="967e8-142">Tento režim je třeba používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="967e8-142">This mode should be used with caution.</span></span> <span data-ttu-id="967e8-143">Byste měli použít ve prostředích, kde zabezpečení přenosu se neposkytujeme jiným způsobem (jako je protokol IPSec) a infrastruktura WCF se poskytuje pouze ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="967e8-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="967e8-144">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="967e8-144">Child Elements</span></span>  
  
|<span data-ttu-id="967e8-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="967e8-145">Element</span></span>|<span data-ttu-id="967e8-146">Popis</span><span class="sxs-lookup"><span data-stu-id="967e8-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="967e8-147">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="967e8-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="967e8-148">Definuje nastavení zabezpečení přenosu pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="967e8-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="967e8-149">Tento element odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="967e8-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="967e8-150">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="967e8-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="967e8-151">Definuje nastavení zabezpečení zpráv pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="967e8-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="967e8-152">Tento element odpovídá <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="967e8-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="967e8-153">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="967e8-153">Parent Elements</span></span>  
  
|<span data-ttu-id="967e8-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="967e8-154">Element</span></span>|<span data-ttu-id="967e8-155">Popis</span><span class="sxs-lookup"><span data-stu-id="967e8-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="967e8-156">vazba</span><span class="sxs-lookup"><span data-stu-id="967e8-156">binding</span></span>|<span data-ttu-id="967e8-157">Prvek vazby [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="967e8-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="967e8-158">Poznámky</span><span class="sxs-lookup"><span data-stu-id="967e8-158">Remarks</span></span>  
 <span data-ttu-id="967e8-159">Ve výchozím nastavení není zabezpečen zprávu protokolu SOAP a klient není ověřený.</span><span class="sxs-lookup"><span data-stu-id="967e8-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="967e8-160">Tento prvek umožňuje konfigurovat nastavení dalšího ověření zabezpečení pro `netHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="967e8-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967e8-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="967e8-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>    
 [<span data-ttu-id="967e8-162">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="967e8-162">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="967e8-163">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="967e8-163">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="967e8-164">Vazby</span><span class="sxs-lookup"><span data-stu-id="967e8-164">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="967e8-165">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="967e8-165">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="967e8-166">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="967e8-166">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="967e8-167">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="967e8-167">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
