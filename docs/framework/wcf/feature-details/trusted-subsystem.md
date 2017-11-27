---
title: "Důvěryhodný subsystém"
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
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 229efd7fed9b8aeb1effff7bd4358930ab8c44ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="trusted-subsystem"></a><span data-ttu-id="e904c-102">Důvěryhodný subsystém</span><span class="sxs-lookup"><span data-stu-id="e904c-102">Trusted Subsystem</span></span>
<span data-ttu-id="e904c-103">Klient přistupuje k jedné nebo více webových služeb, které jsou rozmístěny v síti.</span><span class="sxs-lookup"><span data-stu-id="e904c-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="e904c-104">Webové služby jsou navržené tak, aby přístup k další prostředky (například databáze nebo jiných webových služeb) je zapouzdřené v obchodní logice webovou službu.</span><span class="sxs-lookup"><span data-stu-id="e904c-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="e904c-105">Tyto prostředky musí být chráněny před neoprávněným přístupem.</span><span class="sxs-lookup"><span data-stu-id="e904c-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="e904c-106">Následující obrázek znázorňuje proces důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="e904c-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="e904c-107">![Důvěryhodný subsystém](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="e904c-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="e904c-108">Následující kroky popisují proces důvěryhodný subsystém, jak ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="e904c-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1.  <span data-ttu-id="e904c-109">Klient odešle požadavek na důvěryhodný subsystém spolu s přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="e904c-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2.  <span data-ttu-id="e904c-110">Důvěryhodný subsystém ověří a autorizuje uživatele.</span><span class="sxs-lookup"><span data-stu-id="e904c-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3.  <span data-ttu-id="e904c-111">Důvěryhodný subsystém odešle zprávu požadavku vzdálený prostředek.</span><span class="sxs-lookup"><span data-stu-id="e904c-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="e904c-112">Tento požadavek je přiložena přihlašovací údaje pro důvěryhodný subsystém (nebo účtu služby, pod kterým se spouští proces důvěryhodný subsystém).</span><span class="sxs-lookup"><span data-stu-id="e904c-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4.  <span data-ttu-id="e904c-113">Prostředek back-end ověří a autorizuje důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="e904c-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="e904c-114">Pak zpracuje požadavek a odpověď důvěryhodný subsystém problémy.</span><span class="sxs-lookup"><span data-stu-id="e904c-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5.  <span data-ttu-id="e904c-115">Důvěryhodný subsystém zpracuje odpověď a vydá vlastní odpověď klientovi.</span><span class="sxs-lookup"><span data-stu-id="e904c-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="e904c-116">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e904c-116">Characteristic</span></span>|<span data-ttu-id="e904c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e904c-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e904c-118">Režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e904c-118">Security Mode</span></span>|<span data-ttu-id="e904c-119">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e904c-119">Message</span></span>|  
|<span data-ttu-id="e904c-120">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="e904c-120">Interoperability</span></span>|[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e904c-121">pouze.</span><span class="sxs-lookup"><span data-stu-id="e904c-121"> only.</span></span>|  
|<span data-ttu-id="e904c-122">Ověřování (služba)</span><span class="sxs-lookup"><span data-stu-id="e904c-122">Authentication (service)</span></span>|<span data-ttu-id="e904c-123">Služby tokenů zabezpečení ověřování a autorizaci klientů.</span><span class="sxs-lookup"><span data-stu-id="e904c-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="e904c-124">Ověřování (klient)</span><span class="sxs-lookup"><span data-stu-id="e904c-124">Authentication (client)</span></span>|<span data-ttu-id="e904c-125">Důvěryhodný subsystém ověřuje klienta a prostředek ověřuje důvěryhodný subsystém služby.</span><span class="sxs-lookup"><span data-stu-id="e904c-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="e904c-126">Integrita</span><span class="sxs-lookup"><span data-stu-id="e904c-126">Integrity</span></span>|<span data-ttu-id="e904c-127">Ano</span><span class="sxs-lookup"><span data-stu-id="e904c-127">Yes</span></span>|  
|<span data-ttu-id="e904c-128">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="e904c-128">Confidentiality</span></span>|<span data-ttu-id="e904c-129">Ano</span><span class="sxs-lookup"><span data-stu-id="e904c-129">Yes</span></span>|  
|<span data-ttu-id="e904c-130">Přenos</span><span class="sxs-lookup"><span data-stu-id="e904c-130">Transport</span></span>|<span data-ttu-id="e904c-131">HTTP mezi klientem a službou důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="e904c-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="e904c-132">NET. TCP mezi službou důvěryhodný subsystém a prostředků (služba back-end).</span><span class="sxs-lookup"><span data-stu-id="e904c-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="e904c-133">Vazba</span><span class="sxs-lookup"><span data-stu-id="e904c-133">Binding</span></span>|<span data-ttu-id="e904c-134"><xref:System.ServiceModel.WSHttpBinding>a <xref:System.ServiceModel.NetTcpBinding> [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e904c-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="e904c-135">Prostředek (služba Back-End)</span><span class="sxs-lookup"><span data-stu-id="e904c-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="e904c-136">Kód</span><span class="sxs-lookup"><span data-stu-id="e904c-136">Code</span></span>  
 <span data-ttu-id="e904c-137">Následující kód ukazuje, jak vytvořit koncový bod služby pro prostředek, který používá zabezpečení přenosu zajišťuje přenosový protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="e904c-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="e904c-138">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e904c-138">Configuration</span></span>  
 <span data-ttu-id="e904c-139">Následující konfigurace nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e904c-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="e904c-140">Důvěryhodný subsystém</span><span class="sxs-lookup"><span data-stu-id="e904c-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="e904c-141">Kód</span><span class="sxs-lookup"><span data-stu-id="e904c-141">Code</span></span>  
 <span data-ttu-id="e904c-142">Následující kód ukazuje, jak vytvořit koncový bod služby pro důvěryhodný subsystém, který používá zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="e904c-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="e904c-143">Následující kód ukazuje služby v důvěryhodný subsystém, který komunikuje s back endové služby pomocí zabezpečení přenosu zajišťuje přenosový protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="e904c-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="e904c-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e904c-144">Configuration</span></span>  
 <span data-ttu-id="e904c-145">Následující konfigurace nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e904c-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="e904c-146">Všimněte si dvě vazby: jednu zabezpečuje služby hostované v důvěryhodný subsystém a dalších komunikuje mezi důvěryhodný subsystém a back endové službě.</span><span class="sxs-lookup"><span data-stu-id="e904c-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""   
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="e904c-147">Klient</span><span class="sxs-lookup"><span data-stu-id="e904c-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="e904c-148">Kód</span><span class="sxs-lookup"><span data-stu-id="e904c-148">Code</span></span>  
 <span data-ttu-id="e904c-149">Následující kód ukazuje, jak vytvořit klienta, který komunikuje s důvěryhodný subsystém pomocí zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="e904c-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="e904c-150">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e904c-150">Configuration</span></span>  
 <span data-ttu-id="e904c-151">Následující kód konfiguruje klienta na používání zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="e904c-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="e904c-152">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není konfigurovatelné).</span><span class="sxs-lookup"><span data-stu-id="e904c-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""   
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e904c-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="e904c-153">See Also</span></span>  
 [<span data-ttu-id="e904c-154">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e904c-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e904c-155">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="e904c-155">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
