---
title: Zabezpečení přenosu se základním ověřováním
description: Projděte si tento scénář WCF, který ukazuje základní ověřování pro službu a klienta WCF. Služba potřebuje platný certifikát, který důvěřuje klientovi.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: f15a19feaed631a76948efd24ee225acf789cb2d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244852"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="8be0e-104">Zabezpečení přenosu se základním ověřováním</span><span class="sxs-lookup"><span data-stu-id="8be0e-104">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="8be0e-105">Následující ilustrace znázorňuje službu Windows Communication Foundation (WCF) a klienta.</span><span class="sxs-lookup"><span data-stu-id="8be0e-105">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="8be0e-106">Server potřebuje platný certifikát X. 509, který se dá použít pro SSL (Secure Sockets Layer) (SSL), a klienti musí důvěřovat certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="8be0e-106">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="8be0e-107">Kromě toho webová služba už používá implementaci SSL, kterou je možné použít.</span><span class="sxs-lookup"><span data-stu-id="8be0e-107">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="8be0e-108">Další informace o povolení základního ověřování na Internetová informační služba (IIS) najdete v tématu <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> .</span><span class="sxs-lookup"><span data-stu-id="8be0e-108">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje zabezpečení přenosu pomocí základního ověřování.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="8be0e-110">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="8be0e-110">Characteristic</span></span>|<span data-ttu-id="8be0e-111">Description</span><span class="sxs-lookup"><span data-stu-id="8be0e-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8be0e-112">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8be0e-112">Security Mode</span></span>|<span data-ttu-id="8be0e-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="8be0e-113">Transport</span></span>|  
|<span data-ttu-id="8be0e-114">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="8be0e-114">Interoperability</span></span>|<span data-ttu-id="8be0e-115">S existujícími klienty a službami webové služby</span><span class="sxs-lookup"><span data-stu-id="8be0e-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="8be0e-116">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="8be0e-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="8be0e-117">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="8be0e-117">Authentication (Client)</span></span>|<span data-ttu-id="8be0e-118">Ano (pomocí HTTPS)</span><span class="sxs-lookup"><span data-stu-id="8be0e-118">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="8be0e-119">Ano (pomocí uživatelského jména a hesla)</span><span class="sxs-lookup"><span data-stu-id="8be0e-119">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="8be0e-120">Integrita</span><span class="sxs-lookup"><span data-stu-id="8be0e-120">Integrity</span></span>|<span data-ttu-id="8be0e-121">Ano</span><span class="sxs-lookup"><span data-stu-id="8be0e-121">Yes</span></span>|  
|<span data-ttu-id="8be0e-122">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="8be0e-122">Confidentiality</span></span>|<span data-ttu-id="8be0e-123">Ano</span><span class="sxs-lookup"><span data-stu-id="8be0e-123">Yes</span></span>|  
|<span data-ttu-id="8be0e-124">Přenos</span><span class="sxs-lookup"><span data-stu-id="8be0e-124">Transport</span></span>|<span data-ttu-id="8be0e-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="8be0e-125">HTTPS</span></span>|  
|<span data-ttu-id="8be0e-126">Vazba</span><span class="sxs-lookup"><span data-stu-id="8be0e-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="8be0e-127">Služba</span><span class="sxs-lookup"><span data-stu-id="8be0e-127">Service</span></span>  
 <span data-ttu-id="8be0e-128">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="8be0e-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8be0e-129">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="8be0e-129">Do one of the following:</span></span>  
  
- <span data-ttu-id="8be0e-130">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8be0e-130">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="8be0e-131">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="8be0e-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8be0e-132">Kód</span><span class="sxs-lookup"><span data-stu-id="8be0e-132">Code</span></span>  
 <span data-ttu-id="8be0e-133">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá uživatelské jméno a heslo domény systému Windows pro přenos zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8be0e-133">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="8be0e-134">Všimněte si, že služba vyžaduje pro ověření klienta certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="8be0e-134">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="8be0e-135">Další informace najdete v tématu [práce s certifikáty](working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8be0e-135">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="8be0e-136">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8be0e-136">Configuration</span></span>  
 <span data-ttu-id="8be0e-137">Následující nakonfiguruje službu tak, aby používala základní ověřování s zabezpečením na úrovni přenosu:</span><span class="sxs-lookup"><span data-stu-id="8be0e-137">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="8be0e-138">Klient</span><span class="sxs-lookup"><span data-stu-id="8be0e-138">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="8be0e-139">Kód</span><span class="sxs-lookup"><span data-stu-id="8be0e-139">Code</span></span>  
 <span data-ttu-id="8be0e-140">Následující kód ukazuje kód klienta, který obsahuje uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="8be0e-140">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="8be0e-141">Všimněte si, že uživatel musí zadat platné uživatelské jméno a heslo systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8be0e-141">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="8be0e-142">Zde není zobrazen kód pro vrácení uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="8be0e-142">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="8be0e-143">Použijte dialogové okno nebo jiné rozhraní k dotazování uživatele na informace.</span><span class="sxs-lookup"><span data-stu-id="8be0e-143">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8be0e-144">Uživatelské jméno a heslo lze nastavit pouze pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="8be0e-144">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="8be0e-145">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8be0e-145">Configuration</span></span>  
 <span data-ttu-id="8be0e-146">Následující kód ukazuje konfiguraci klienta.</span><span class="sxs-lookup"><span data-stu-id="8be0e-146">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8be0e-147">Konfiguraci nelze použít k nastavení uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="8be0e-147">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="8be0e-148">Zde uvedená konfigurace musí být rozšířena pomocí kódu pro nastavení uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="8be0e-148">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8be0e-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="8be0e-149">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="8be0e-150">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="8be0e-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="8be0e-151">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="8be0e-151">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="8be0e-152">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8be0e-152">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="8be0e-153">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8be0e-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
