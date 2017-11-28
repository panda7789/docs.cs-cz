---
title: "Zabezpečení zpráv s klientem uživatelského jména"
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
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 429136ab3e01f3f53f662db02bbac6096be48d11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="0808a-102">Zabezpečení zpráv s klientem uživatelského jména</span><span class="sxs-lookup"><span data-stu-id="0808a-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="0808a-103">Následující obrázek znázorňuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpečené pomocí zabezpečení na úrovni zpráv klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="0808a-103">The following illustration shows an [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client secured using message-level security.</span></span> <span data-ttu-id="0808a-104">Služba je ověření pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="0808a-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="0808a-105">Klient se ověří pomocí uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="0808a-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="0808a-106">Ukázkovou aplikaci, najdete v části [uživatelské jméno zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="0808a-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="0808a-107">![Zabezpečení zpráv pomocí uživatelského jména ověřování](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="0808a-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="0808a-108">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0808a-108">Characteristic</span></span>|<span data-ttu-id="0808a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0808a-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0808a-110">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0808a-110">Security Mode</span></span>|<span data-ttu-id="0808a-111">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0808a-111">Message</span></span>|  
|<span data-ttu-id="0808a-112">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="0808a-112">Interoperability</span></span>|[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="0808a-113">pouze</span><span class="sxs-lookup"><span data-stu-id="0808a-113"> only</span></span>|  
|<span data-ttu-id="0808a-114">Ověřování (Server)</span><span class="sxs-lookup"><span data-stu-id="0808a-114">Authentication (Server)</span></span>|<span data-ttu-id="0808a-115">Počáteční vyjednávání vyžaduje ověření serveru</span><span class="sxs-lookup"><span data-stu-id="0808a-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="0808a-116">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="0808a-116">Authentication (Client)</span></span>|<span data-ttu-id="0808a-117">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="0808a-117">User name/password</span></span>|  
|<span data-ttu-id="0808a-118">Integrita</span><span class="sxs-lookup"><span data-stu-id="0808a-118">Integrity</span></span>|<span data-ttu-id="0808a-119">Ano, kontextu sdílené zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0808a-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="0808a-120">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="0808a-120">Confidentiality</span></span>|<span data-ttu-id="0808a-121">Ano, kontextu sdílené zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0808a-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="0808a-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="0808a-122">Transport</span></span>|<span data-ttu-id="0808a-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="0808a-123">HTTP</span></span>|  
|<span data-ttu-id="0808a-124">Vazba</span><span class="sxs-lookup"><span data-stu-id="0808a-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="0808a-125">Služba</span><span class="sxs-lookup"><span data-stu-id="0808a-125">Service</span></span>  
 <span data-ttu-id="0808a-126">Následující kód a konfigurace jsou určená ke spuštění nezávisle.</span><span class="sxs-lookup"><span data-stu-id="0808a-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="0808a-127">Proveďte jednu z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="0808a-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="0808a-128">Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0808a-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="0808a-129">Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="0808a-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0808a-130">Kód</span><span class="sxs-lookup"><span data-stu-id="0808a-130">Code</span></span>  
 <span data-ttu-id="0808a-131">Následující kód ukazuje, jak vytvořit koncový bod služby, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="0808a-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="0808a-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0808a-132">Configuration</span></span>  
 <span data-ttu-id="0808a-133">Místo kód se dají použít následující konfigurace:</span><span class="sxs-lookup"><span data-stu-id="0808a-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="0808a-134">Klient</span><span class="sxs-lookup"><span data-stu-id="0808a-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="0808a-135">Kód</span><span class="sxs-lookup"><span data-stu-id="0808a-135">Code</span></span>  
 <span data-ttu-id="0808a-136">Následující kód vytvoří klienta.</span><span class="sxs-lookup"><span data-stu-id="0808a-136">The following code creates the client.</span></span> <span data-ttu-id="0808a-137">Vazba je režim zabezpečení zpráv a typu pověření klienta nastavena na `UserName`.</span><span class="sxs-lookup"><span data-stu-id="0808a-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="0808a-138">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není konfigurovatelné).</span><span class="sxs-lookup"><span data-stu-id="0808a-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="0808a-139">Kód, který vrátí uživatelské jméno a heslo není tady zobrazit, protože musíte to provést na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="0808a-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="0808a-140">Například pomocí dialogového okna Windows Forms dotazovat uživatele pro data.</span><span class="sxs-lookup"><span data-stu-id="0808a-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="0808a-141">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0808a-141">Configuration</span></span>  
 <span data-ttu-id="0808a-142">Následující kód konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="0808a-142">The following code configures the client.</span></span> <span data-ttu-id="0808a-143">Vazba je režim zabezpečení zpráv a typu pověření klienta nastavena na `UserName`.</span><span class="sxs-lookup"><span data-stu-id="0808a-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="0808a-144">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není konfigurovatelné).</span><span class="sxs-lookup"><span data-stu-id="0808a-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0808a-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="0808a-145">See Also</span></span>  
 [<span data-ttu-id="0808a-146">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0808a-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="0808a-147">Uživatelské jméno zabezpečení zprávy</span><span class="sxs-lookup"><span data-stu-id="0808a-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [<span data-ttu-id="0808a-148">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="0808a-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="0808a-149">\<identity ></span><span class="sxs-lookup"><span data-stu-id="0808a-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [<span data-ttu-id="0808a-150">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="0808a-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
