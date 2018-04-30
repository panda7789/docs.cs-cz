---
title: Zabezpečení přenosu se základním ověřováním
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
caps.latest.revision: 18
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 7430767c80515d14ae23e17ae2b94e0acc97ff30
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="6f0a7-102">Zabezpečení přenosu se základním ověřováním</span><span class="sxs-lookup"><span data-stu-id="6f0a7-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="6f0a7-103">Následující obrázek znázorňuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-103">The following illustration shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client.</span></span> <span data-ttu-id="6f0a7-104">Server vyžaduje platný certifikát X.509, který lze použít pro vrstvy SSL (Secure Sockets) a klienti musí důvěřovat certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="6f0a7-105">Navíc webová služba již má implementaci protokolu SSL, který lze použít.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="6f0a7-106">Další informace o povolení základní ověřování v Internetové informační služby (IIS) najdete v tématu [ http://go.microsoft.com/fwlink/?LinkId=83822 ](http://go.microsoft.com/fwlink/?LinkId=83822).</span><span class="sxs-lookup"><span data-stu-id="6f0a7-106">For more information about enabling basic authentication on Internet Information Services (IIS), see [http://go.microsoft.com/fwlink/?LinkId=83822](http://go.microsoft.com/fwlink/?LinkId=83822).</span></span>  
  
 <span data-ttu-id="6f0a7-107">![Přenosu zabezpečení se základním ověřováním](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span><span class="sxs-lookup"><span data-stu-id="6f0a7-107">![Transport security with basic authentication](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span></span>  
  
|<span data-ttu-id="6f0a7-108">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6f0a7-108">Characteristic</span></span>|<span data-ttu-id="6f0a7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6f0a7-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6f0a7-110">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-110">Security Mode</span></span>|<span data-ttu-id="6f0a7-111">Přenos</span><span class="sxs-lookup"><span data-stu-id="6f0a7-111">Transport</span></span>|  
|<span data-ttu-id="6f0a7-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="6f0a7-112">Interoperability</span></span>|<span data-ttu-id="6f0a7-113">S existující klienty webové služby a služby</span><span class="sxs-lookup"><span data-stu-id="6f0a7-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="6f0a7-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="6f0a7-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="6f0a7-115">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="6f0a7-115">Authentication (Client)</span></span>|<span data-ttu-id="6f0a7-116">Ano (pomocí protokolu HTTPS)</span><span class="sxs-lookup"><span data-stu-id="6f0a7-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="6f0a7-117">Ano (prostřednictvím uživatelské jméno a heslo)</span><span class="sxs-lookup"><span data-stu-id="6f0a7-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="6f0a7-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="6f0a7-118">Integrity</span></span>|<span data-ttu-id="6f0a7-119">Ano</span><span class="sxs-lookup"><span data-stu-id="6f0a7-119">Yes</span></span>|  
|<span data-ttu-id="6f0a7-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="6f0a7-120">Confidentiality</span></span>|<span data-ttu-id="6f0a7-121">Ano</span><span class="sxs-lookup"><span data-stu-id="6f0a7-121">Yes</span></span>|  
|<span data-ttu-id="6f0a7-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="6f0a7-122">Transport</span></span>|<span data-ttu-id="6f0a7-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="6f0a7-123">HTTPS</span></span>|  
|<span data-ttu-id="6f0a7-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="6f0a7-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="6f0a7-125">Služba</span><span class="sxs-lookup"><span data-stu-id="6f0a7-125">Service</span></span>  
 <span data-ttu-id="6f0a7-126">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="6f0a7-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="6f0a7-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="6f0a7-128">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="6f0a7-129">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6f0a7-130">Kód</span><span class="sxs-lookup"><span data-stu-id="6f0a7-130">Code</span></span>  
 <span data-ttu-id="6f0a7-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá Windows domény uživatelské jméno a heslo pro zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="6f0a7-132">Všimněte si, že služba vyžaduje, aby certifikátu X.509. certifikát k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="6f0a7-133">Další informace najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="6f0a7-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="6f0a7-134">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6f0a7-134">Configuration</span></span>  
 <span data-ttu-id="6f0a7-135">Následující konfiguruje službu používat základní ověřování s zabezpečení na úrovni přenosu:</span><span class="sxs-lookup"><span data-stu-id="6f0a7-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="6f0a7-136">Klient</span><span class="sxs-lookup"><span data-stu-id="6f0a7-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="6f0a7-137">Kód</span><span class="sxs-lookup"><span data-stu-id="6f0a7-137">Code</span></span>  
 <span data-ttu-id="6f0a7-138">Následující kód ukazuje kód klienta, která obsahuje uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="6f0a7-139">Všimněte si, že uživatel musí poskytnout platné uživatelské jméno systému Windows a heslo.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="6f0a7-140">Kód, který vrátí uživatelské jméno a heslo není zobrazeny zde.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="6f0a7-141">Použijte dialogové okno nebo jiných rozhraní k dotazování uživatelské informace.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f0a7-142">Uživatelské jméno a heslo lze nastavit pouze pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="6f0a7-143">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6f0a7-143">Configuration</span></span>  
 <span data-ttu-id="6f0a7-144">Následující kód ukazuje konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f0a7-145">Konfigurace nelze použít k nastavení uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="6f0a7-146">Konfigurace znázorněné v tomto poli musí rozšířit pomocí kódu nastavit uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="6f0a7-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
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
  
## <a name="see-also"></a><span data-ttu-id="6f0a7-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f0a7-147">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [<span data-ttu-id="6f0a7-148">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="6f0a7-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="6f0a7-149">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="6f0a7-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="6f0a7-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6f0a7-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="6f0a7-151">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="6f0a7-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [<span data-ttu-id="6f0a7-152">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="6f0a7-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
