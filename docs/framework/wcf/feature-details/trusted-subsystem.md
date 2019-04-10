---
title: Důvěryhodný subsystém
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 681312f4fcc76b275697024a45503f5c4cf89a4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208537"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="557f0-102">Důvěryhodný subsystém</span><span class="sxs-lookup"><span data-stu-id="557f0-102">Trusted Subsystem</span></span>
<span data-ttu-id="557f0-103">Klient přistupuje k jedné nebo více webových služeb, které jsou distribuovány napříč sítí.</span><span class="sxs-lookup"><span data-stu-id="557f0-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="557f0-104">Webové služby jsou navržené tak, aby tento přístup k dalším prostředkům (například databáze nebo jiné webové služby), je zapouzdřena v obchodní logice webové služby.</span><span class="sxs-lookup"><span data-stu-id="557f0-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="557f0-105">Tyto prostředky musí být chráněný před neoprávněným přístupem.</span><span class="sxs-lookup"><span data-stu-id="557f0-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="557f0-106">Následující obrázek znázorňuje proces důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="557f0-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="557f0-107">![Důvěryhodný subsystém](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="557f0-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="557f0-108">Následující kroky popisují proces důvěryhodný subsystém, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="557f0-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1.  <span data-ttu-id="557f0-109">Klient odešle požadavek na důvěryhodný subsystém spolu s přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="557f0-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2.  <span data-ttu-id="557f0-110">Důvěryhodný subsystém ověřuje a autorizuje uživatele.</span><span class="sxs-lookup"><span data-stu-id="557f0-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3.  <span data-ttu-id="557f0-111">Důvěryhodný subsystém odešle zprávu požadavku vzdáleného prostředku.</span><span class="sxs-lookup"><span data-stu-id="557f0-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="557f0-112">Této žádosti je přiložený přihlašovací údaje pro důvěryhodného subsystém (nebo účet služby, pod kterým je prováděný procesem důvěryhodný subsystém).</span><span class="sxs-lookup"><span data-stu-id="557f0-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4.  <span data-ttu-id="557f0-113">Prostředek back-end se ověřuje a autorizuje důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="557f0-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="557f0-114">Poté zpracuje požadavek a vydá odpověď na důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="557f0-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5.  <span data-ttu-id="557f0-115">Důvěryhodný subsystém zpracuje odpověď a problémy s vlastním odpověď klientovi.</span><span class="sxs-lookup"><span data-stu-id="557f0-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="557f0-116">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="557f0-116">Characteristic</span></span>|<span data-ttu-id="557f0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="557f0-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="557f0-118">Režim zabezpečení</span><span class="sxs-lookup"><span data-stu-id="557f0-118">Security Mode</span></span>|<span data-ttu-id="557f0-119">Zpráva</span><span class="sxs-lookup"><span data-stu-id="557f0-119">Message</span></span>|  
|<span data-ttu-id="557f0-120">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="557f0-120">Interoperability</span></span>|<span data-ttu-id="557f0-121">Windows Communication Foundation (WCF) pouze.</span><span class="sxs-lookup"><span data-stu-id="557f0-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="557f0-122">Ověřování (služba)</span><span class="sxs-lookup"><span data-stu-id="557f0-122">Authentication (service)</span></span>|<span data-ttu-id="557f0-123">Služba tokenů zabezpečení ověřuje a autorizuje klientů.</span><span class="sxs-lookup"><span data-stu-id="557f0-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="557f0-124">Ověření (klient)</span><span class="sxs-lookup"><span data-stu-id="557f0-124">Authentication (client)</span></span>|<span data-ttu-id="557f0-125">Důvěryhodný subsystém ověřuje klienta a prostředku ověřuje službě důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="557f0-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="557f0-126">Integrita</span><span class="sxs-lookup"><span data-stu-id="557f0-126">Integrity</span></span>|<span data-ttu-id="557f0-127">Ano</span><span class="sxs-lookup"><span data-stu-id="557f0-127">Yes</span></span>|  
|<span data-ttu-id="557f0-128">Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="557f0-128">Confidentiality</span></span>|<span data-ttu-id="557f0-129">Ano</span><span class="sxs-lookup"><span data-stu-id="557f0-129">Yes</span></span>|  
|<span data-ttu-id="557f0-130">Přenos</span><span class="sxs-lookup"><span data-stu-id="557f0-130">Transport</span></span>|<span data-ttu-id="557f0-131">HTTP mezi klientem a službou důvěryhodný subsystém.</span><span class="sxs-lookup"><span data-stu-id="557f0-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="557f0-132">SÍŤ. TCP mezi důvěryhodný subsystém služeb a prostředků (služba back-end).</span><span class="sxs-lookup"><span data-stu-id="557f0-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="557f0-133">Vazba</span><span class="sxs-lookup"><span data-stu-id="557f0-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding> <span data-ttu-id="557f0-134">and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="557f0-134">and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="557f0-135">Prostředků (služba Back-End)</span><span class="sxs-lookup"><span data-stu-id="557f0-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="557f0-136">Kód</span><span class="sxs-lookup"><span data-stu-id="557f0-136">Code</span></span>  
 <span data-ttu-id="557f0-137">Následující kód ukazuje, jak vytvořit koncový bod služby pro prostředek, který používá zabezpečení přenosu přenosový protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="557f0-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="557f0-138">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="557f0-138">Configuration</span></span>  
 <span data-ttu-id="557f0-139">Následující konfigurace nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="557f0-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="trusted-subsystem"></a><span data-ttu-id="557f0-140">Důvěryhodný subsystém</span><span class="sxs-lookup"><span data-stu-id="557f0-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="557f0-141">Kód</span><span class="sxs-lookup"><span data-stu-id="557f0-141">Code</span></span>  
 <span data-ttu-id="557f0-142">Následující kód ukazuje, jak vytvořit koncový bod služby pro důvěryhodného podsystému, který používá zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="557f0-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="557f0-143">Následující kód ukazuje služby v důvěryhodný subsystém, který komunikuje s back-end služby pomocí zabezpečení přenosu přenosový protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="557f0-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="557f0-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="557f0-144">Configuration</span></span>  
 <span data-ttu-id="557f0-145">Následující konfigurace nastaví stejný koncový bod pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="557f0-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="557f0-146">Všimněte si dvě vazby: Jeden zabezpečuje službu hostovanou v důvěryhodný subsystém a druhý zajišťuje komunikaci mezi důvěryhodný subsystém a back-end služby.</span><span class="sxs-lookup"><span data-stu-id="557f0-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="557f0-147">Klient</span><span class="sxs-lookup"><span data-stu-id="557f0-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="557f0-148">Kód</span><span class="sxs-lookup"><span data-stu-id="557f0-148">Code</span></span>  
 <span data-ttu-id="557f0-149">Následující kód ukazuje, jak vytvořit klienta, který komunikuje s důvěryhodný subsystém pomocí zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověření.</span><span class="sxs-lookup"><span data-stu-id="557f0-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="557f0-150">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="557f0-150">Configuration</span></span>  
 <span data-ttu-id="557f0-151">Následující kód konfiguruje klienta pro ověřování pomocí zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="557f0-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="557f0-152">Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není konfigurovatelné).</span><span class="sxs-lookup"><span data-stu-id="557f0-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="557f0-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="557f0-153">See also</span></span>

- [<span data-ttu-id="557f0-154">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="557f0-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="557f0-155">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="557f0-155">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
