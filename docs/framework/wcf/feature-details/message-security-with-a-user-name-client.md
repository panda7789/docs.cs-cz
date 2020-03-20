---
title: Zabezpečení zpráv s klientem uživatelského jména
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 3dd21268d4ea7dc59c74889ac94dc86678e91865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184641"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="ff079-102">Zabezpečení zpráv s klientem uživatelského jména</span><span class="sxs-lookup"><span data-stu-id="ff079-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="ff079-103">Následující obrázek znázorňuje službu WCF (Windows Communication Foundation) a klienta zabezpečeného pomocí zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="ff079-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="ff079-104">Služba je ověřena certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="ff079-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="ff079-105">Klient se ověřuje pomocí uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="ff079-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="ff079-106">Ukázková aplikace naleznete v tématu [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="ff079-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="ff079-107">![Zabezpečení zpráv pomocí ověřování pomocí uživatelského jména](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="ff079-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="ff079-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="ff079-108">Characteristic</span></span>|<span data-ttu-id="ff079-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ff079-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ff079-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ff079-110">Security Mode</span></span>|<span data-ttu-id="ff079-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ff079-111">Message</span></span>|  
|<span data-ttu-id="ff079-112">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="ff079-112">Interoperability</span></span>|<span data-ttu-id="ff079-113">Pouze nadace Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="ff079-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="ff079-114">Ověřování (server)</span><span class="sxs-lookup"><span data-stu-id="ff079-114">Authentication (Server)</span></span>|<span data-ttu-id="ff079-115">Počáteční vyjednávání vyžaduje ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="ff079-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="ff079-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="ff079-116">Authentication (Client)</span></span>|<span data-ttu-id="ff079-117">Uživatelské jméno/heslo</span><span class="sxs-lookup"><span data-stu-id="ff079-117">User name/password</span></span>|  
|<span data-ttu-id="ff079-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="ff079-118">Integrity</span></span>|<span data-ttu-id="ff079-119">Ano, použití kontextu sdíleného zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ff079-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="ff079-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="ff079-120">Confidentiality</span></span>|<span data-ttu-id="ff079-121">Ano, použití kontextu sdíleného zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ff079-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="ff079-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="ff079-122">Transport</span></span>|<span data-ttu-id="ff079-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="ff079-123">HTTP</span></span>|  
|<span data-ttu-id="ff079-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="ff079-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="ff079-125">Služba</span><span class="sxs-lookup"><span data-stu-id="ff079-125">Service</span></span>  
 <span data-ttu-id="ff079-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="ff079-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ff079-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="ff079-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="ff079-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ff079-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="ff079-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="ff079-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ff079-130">kód</span><span class="sxs-lookup"><span data-stu-id="ff079-130">Code</span></span>  
 <span data-ttu-id="ff079-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="ff079-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="ff079-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ff079-132">Configuration</span></span>  
 <span data-ttu-id="ff079-133">Místo kódu lze použít následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="ff079-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="ff079-134">Klient</span><span class="sxs-lookup"><span data-stu-id="ff079-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="ff079-135">kód</span><span class="sxs-lookup"><span data-stu-id="ff079-135">Code</span></span>  
 <span data-ttu-id="ff079-136">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="ff079-136">The following code creates the client.</span></span> <span data-ttu-id="ff079-137">Vazba je zabezpečení režimu zprávy a typ `UserName`pověření klienta je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="ff079-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="ff079-138">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (nelze jej konfigurovat).</span><span class="sxs-lookup"><span data-stu-id="ff079-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="ff079-139">Kód pro vrácení uživatelského jména a hesla zde není zobrazen, protože musí být provedeno na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff079-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="ff079-140">Dialogové okno Formuláře systému Windows můžete například použít k dotazování uživatele na data.</span><span class="sxs-lookup"><span data-stu-id="ff079-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="ff079-141">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ff079-141">Configuration</span></span>  
 <span data-ttu-id="ff079-142">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="ff079-142">The following code configures the client.</span></span> <span data-ttu-id="ff079-143">Vazba je zabezpečení režimu zprávy a typ `UserName`pověření klienta je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="ff079-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="ff079-144">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (nelze jej konfigurovat).</span><span class="sxs-lookup"><span data-stu-id="ff079-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
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
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff079-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff079-145">See also</span></span>

- [<span data-ttu-id="ff079-146">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ff079-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="ff079-147">Zabezpečení zpráv s uživatelským jménem</span><span class="sxs-lookup"><span data-stu-id="ff079-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [<span data-ttu-id="ff079-148">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="ff079-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ff079-149">\<>identity</span><span class="sxs-lookup"><span data-stu-id="ff079-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="ff079-150">[Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ff079-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
