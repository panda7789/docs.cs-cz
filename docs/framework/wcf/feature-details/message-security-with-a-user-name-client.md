---
title: Zabezpečení zpráv s klientem uživatelského jména
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 9447487012cae370d35880e5b780465f9434051b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602619"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="2daef-102">Zabezpečení zpráv s klientem uživatelského jména</span><span class="sxs-lookup"><span data-stu-id="2daef-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="2daef-103">Následující ilustrace znázorňuje službu Windows Communication Foundation (WCF) a klienta zabezpečenou pomocí zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="2daef-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="2daef-104">Služba se ověřuje pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="2daef-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="2daef-105">Klient se ověřuje pomocí uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="2daef-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="2daef-106">Ukázkovou aplikaci najdete v tématu [zabezpečení zpráv – uživatelské jméno](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="2daef-106">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="2daef-107">![Zabezpečení zpráv pomocí ověřování uživatelského jména](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="2daef-107">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="2daef-108">Charakteristika</span><span class="sxs-lookup"><span data-stu-id="2daef-108">Characteristic</span></span>|<span data-ttu-id="2daef-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2daef-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2daef-110">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2daef-110">Security Mode</span></span>|<span data-ttu-id="2daef-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2daef-111">Message</span></span>|  
|<span data-ttu-id="2daef-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="2daef-112">Interoperability</span></span>|<span data-ttu-id="2daef-113">Pouze Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="2daef-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="2daef-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="2daef-114">Authentication (Server)</span></span>|<span data-ttu-id="2daef-115">Počáteční vyjednávání vyžaduje ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="2daef-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="2daef-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="2daef-116">Authentication (Client)</span></span>|<span data-ttu-id="2daef-117">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="2daef-117">User name/password</span></span>|  
|<span data-ttu-id="2daef-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="2daef-118">Integrity</span></span>|<span data-ttu-id="2daef-119">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2daef-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="2daef-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="2daef-120">Confidentiality</span></span>|<span data-ttu-id="2daef-121">Ano, použití sdíleného kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2daef-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="2daef-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="2daef-122">Transport</span></span>|<span data-ttu-id="2daef-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="2daef-123">HTTP</span></span>|  
|<span data-ttu-id="2daef-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="2daef-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="2daef-125">Služba</span><span class="sxs-lookup"><span data-stu-id="2daef-125">Service</span></span>  
 <span data-ttu-id="2daef-126">Následující kód a konfigurace jsou určeny ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="2daef-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2daef-127">Proveďte některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="2daef-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="2daef-128">Vytvořte samostatnou službu pomocí kódu bez konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2daef-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="2daef-129">Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="2daef-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2daef-130">Kód</span><span class="sxs-lookup"><span data-stu-id="2daef-130">Code</span></span>  
 <span data-ttu-id="2daef-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="2daef-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="2daef-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2daef-132">Configuration</span></span>  
 <span data-ttu-id="2daef-133">Místo kódu lze použít následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="2daef-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="2daef-134">Klient</span><span class="sxs-lookup"><span data-stu-id="2daef-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="2daef-135">Kód</span><span class="sxs-lookup"><span data-stu-id="2daef-135">Code</span></span>  
 <span data-ttu-id="2daef-136">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="2daef-136">The following code creates the client.</span></span> <span data-ttu-id="2daef-137">Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na hodnotu `UserName` .</span><span class="sxs-lookup"><span data-stu-id="2daef-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="2daef-138">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není možné je konfigurovat).</span><span class="sxs-lookup"><span data-stu-id="2daef-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="2daef-139">Kód pro vrácení uživatelského jména a hesla zde není zobrazen, protože musí být proveden na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="2daef-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="2daef-140">Můžete například použít dialogové okno model Windows Forms k dotazování uživatele na data.</span><span class="sxs-lookup"><span data-stu-id="2daef-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="2daef-141">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2daef-141">Configuration</span></span>  
 <span data-ttu-id="2daef-142">Následující kód nakonfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="2daef-142">The following code configures the client.</span></span> <span data-ttu-id="2daef-143">Vazba je zabezpečení režimu zprávy a typ přihlašovacích údajů klienta je nastaven na hodnotu `UserName` .</span><span class="sxs-lookup"><span data-stu-id="2daef-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="2daef-144">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není možné je konfigurovat).</span><span class="sxs-lookup"><span data-stu-id="2daef-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2daef-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="2daef-145">See also</span></span>

- [<span data-ttu-id="2daef-146">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2daef-146">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="2daef-147">Zabezpečení zpráv s uživatelským jménem</span><span class="sxs-lookup"><span data-stu-id="2daef-147">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="2daef-148">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="2daef-148">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="2daef-149">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2daef-149">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
