---
title: Zabezpečení přenosu se základním ověřováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: eace5ce9a84d99cb2526896cca36a9e2a13fd5f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742693"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="05d3e-102">Zabezpečení přenosu se základním ověřováním</span><span class="sxs-lookup"><span data-stu-id="05d3e-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="05d3e-103">Následující ilustrace znázorňuje službu Windows Communication Foundation (WCF) a klienta.</span><span class="sxs-lookup"><span data-stu-id="05d3e-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="05d3e-104">Server potřebuje platný certifikát X. 509, který se dá použít pro SSL (Secure Sockets Layer) (SSL), a klienti musí důvěřovat certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="05d3e-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="05d3e-105">Kromě toho webová služba už používá implementaci SSL, kterou je možné použít.</span><span class="sxs-lookup"><span data-stu-id="05d3e-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="05d3e-106">Další informace o povolení základního ověřování na Internetová informační služba (IIS) najdete v článku <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span><span class="sxs-lookup"><span data-stu-id="05d3e-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje zabezpečení přenosu pomocí základního ověřování.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="05d3e-108">Charakteristiku</span><span class="sxs-lookup"><span data-stu-id="05d3e-108">Characteristic</span></span>|<span data-ttu-id="05d3e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="05d3e-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="05d3e-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="05d3e-110">Security Mode</span></span>|<span data-ttu-id="05d3e-111">Přepravu</span><span class="sxs-lookup"><span data-stu-id="05d3e-111">Transport</span></span>|  
|<span data-ttu-id="05d3e-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="05d3e-112">Interoperability</span></span>|<span data-ttu-id="05d3e-113">S existujícími klienty a službami webové služby</span><span class="sxs-lookup"><span data-stu-id="05d3e-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="05d3e-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="05d3e-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="05d3e-115">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="05d3e-115">Authentication (Client)</span></span>|<span data-ttu-id="05d3e-116">Ano (pomocí HTTPS)</span><span class="sxs-lookup"><span data-stu-id="05d3e-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="05d3e-117">Ano (pomocí uživatelského jména a hesla)</span><span class="sxs-lookup"><span data-stu-id="05d3e-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="05d3e-118">Způsobilost</span><span class="sxs-lookup"><span data-stu-id="05d3e-118">Integrity</span></span>|<span data-ttu-id="05d3e-119">Ano</span><span class="sxs-lookup"><span data-stu-id="05d3e-119">Yes</span></span>|  
|<span data-ttu-id="05d3e-120">Chovávat</span><span class="sxs-lookup"><span data-stu-id="05d3e-120">Confidentiality</span></span>|<span data-ttu-id="05d3e-121">Ano</span><span class="sxs-lookup"><span data-stu-id="05d3e-121">Yes</span></span>|  
|<span data-ttu-id="05d3e-122">Přepravu</span><span class="sxs-lookup"><span data-stu-id="05d3e-122">Transport</span></span>|<span data-ttu-id="05d3e-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="05d3e-123">HTTPS</span></span>|  
|<span data-ttu-id="05d3e-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="05d3e-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="05d3e-125">Service</span><span class="sxs-lookup"><span data-stu-id="05d3e-125">Service</span></span>  
 <span data-ttu-id="05d3e-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="05d3e-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="05d3e-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="05d3e-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="05d3e-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="05d3e-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="05d3e-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="05d3e-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="05d3e-130">Kód</span><span class="sxs-lookup"><span data-stu-id="05d3e-130">Code</span></span>  
 <span data-ttu-id="05d3e-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá uživatelské jméno a heslo domény systému Windows pro přenos zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="05d3e-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="05d3e-132">Všimněte si, že služba vyžaduje pro ověření klienta certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="05d3e-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="05d3e-133">Další informace najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="05d3e-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="05d3e-134">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="05d3e-134">Configuration</span></span>  
 <span data-ttu-id="05d3e-135">Následující nakonfiguruje službu tak, aby používala základní ověřování s zabezpečením na úrovni přenosu:</span><span class="sxs-lookup"><span data-stu-id="05d3e-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="05d3e-136">Klient</span><span class="sxs-lookup"><span data-stu-id="05d3e-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="05d3e-137">Kód</span><span class="sxs-lookup"><span data-stu-id="05d3e-137">Code</span></span>  
 <span data-ttu-id="05d3e-138">Následující kód ukazuje kód klienta, který obsahuje uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="05d3e-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="05d3e-139">Všimněte si, že uživatel musí zadat platné uživatelské jméno a heslo systému Windows.</span><span class="sxs-lookup"><span data-stu-id="05d3e-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="05d3e-140">Zde není zobrazen kód pro vrácení uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="05d3e-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="05d3e-141">Použijte dialogové okno nebo jiné rozhraní k dotazování uživatele na informace.</span><span class="sxs-lookup"><span data-stu-id="05d3e-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05d3e-142">Uživatelské jméno a heslo lze nastavit pouze pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="05d3e-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="05d3e-143">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="05d3e-143">Configuration</span></span>  
 <span data-ttu-id="05d3e-144">Následující kód ukazuje konfiguraci klienta.</span><span class="sxs-lookup"><span data-stu-id="05d3e-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05d3e-145">Konfiguraci nelze použít k nastavení uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="05d3e-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="05d3e-146">Zde uvedená konfigurace musí být rozšířena pomocí kódu pro nastavení uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="05d3e-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05d3e-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05d3e-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="05d3e-148">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="05d3e-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="05d3e-149">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="05d3e-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="05d3e-150">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="05d3e-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="05d3e-151">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="05d3e-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="05d3e-152">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="05d3e-152">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
