---
title: <message> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 320aca16bde9fc27aa35cad27286d402745e4710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931562"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="94ed2-102">\<> zpráv > \<BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="94ed2-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="94ed2-103">Definuje nastavení pro zabezpečení [ \<BasicHttpBinding >](basichttpbinding.md)na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="94ed2-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="94ed2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="94ed2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="94ed2-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="94ed2-105">\<bindings></span></span>  
<span data-ttu-id="94ed2-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="94ed2-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="94ed2-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="94ed2-107">\<binding></span></span>  
<span data-ttu-id="94ed2-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="94ed2-108">\<security></span></span>  
<span data-ttu-id="94ed2-109">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="94ed2-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ed2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94ed2-110">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94ed2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94ed2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="94ed2-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94ed2-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94ed2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="94ed2-113">Attributes</span></span>  
  
|<span data-ttu-id="94ed2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="94ed2-114">Attribute</span></span>|<span data-ttu-id="94ed2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="94ed2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94ed2-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="94ed2-116">algorithmSuite</span></span>|<span data-ttu-id="94ed2-117">Nastaví šifrování zpráv a algoritmy pro zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="94ed2-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="94ed2-118">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, který určuje algoritmy a velikosti klíčů.</span><span class="sxs-lookup"><span data-stu-id="94ed2-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="94ed2-119">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="94ed2-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="94ed2-120">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="94ed2-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="94ed2-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="94ed2-121">clientCredentialType</span></span>|<span data-ttu-id="94ed2-122">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení založeného na zprávách.</span><span class="sxs-lookup"><span data-stu-id="94ed2-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="94ed2-123">Výchozí hodnota je `UserName`.</span><span class="sxs-lookup"><span data-stu-id="94ed2-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="94ed2-124">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="94ed2-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="94ed2-125">Value</span><span class="sxs-lookup"><span data-stu-id="94ed2-125">Value</span></span>|<span data-ttu-id="94ed2-126">Popis</span><span class="sxs-lookup"><span data-stu-id="94ed2-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94ed2-127">UserName</span><span class="sxs-lookup"><span data-stu-id="94ed2-127">UserName</span></span>|<span data-ttu-id="94ed2-128">– Vyžaduje, aby byl klient ověřený pro server s přihlašovacími údaji uživatele.</span><span class="sxs-lookup"><span data-stu-id="94ed2-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="94ed2-129">Toto pověření je nutné zadat pomocí [ \<> ClientCredentials](clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="94ed2-129">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="94ed2-130">-WCF nepodporuje odeslání výtahu hesla ani odvození klíčů pomocí hesel a použití takových klíčů pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="94ed2-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="94ed2-131">Proto WCF vynutilo zabezpečení přenosu při použití přihlašovacích údajů uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="94ed2-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="94ed2-132">V `basicHttpBinding`případě nástroje to vyžaduje vytvoření kanálu SSL.</span><span class="sxs-lookup"><span data-stu-id="94ed2-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="94ed2-133">Certifikát</span><span class="sxs-lookup"><span data-stu-id="94ed2-133">Certificate</span></span>|<span data-ttu-id="94ed2-134">Vyžaduje, aby byl klient ověřený na serveru pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="94ed2-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="94ed2-135">Pověření klienta v tomto případě musí být zadáno pomocí [ \<](clientcredentials.md) [ \<](clientcertificate-of-servicecredentials.md)> ClientCredentials a > ClientCertificate.</span><span class="sxs-lookup"><span data-stu-id="94ed2-135">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="94ed2-136">Kromě toho je nutné při použití režimu zabezpečení zpráv zřídit klienta s certifikátem služby.</span><span class="sxs-lookup"><span data-stu-id="94ed2-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="94ed2-137">Pověření služby v tomto případě je nutné zadat pomocí <xref:System.ServiceModel.Description.ClientCredentials> elementu Class nebo `ClientCredentials` Behavior a zadáním certifikátu služby pomocí [ \<> serviceCertificate](servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="94ed2-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94ed2-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94ed2-138">Child Elements</span></span>  
 <span data-ttu-id="94ed2-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="94ed2-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94ed2-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94ed2-140">Parent Elements</span></span>  
  
|<span data-ttu-id="94ed2-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="94ed2-141">Element</span></span>|<span data-ttu-id="94ed2-142">Popis</span><span class="sxs-lookup"><span data-stu-id="94ed2-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94ed2-143">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="94ed2-143">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="94ed2-144">Definuje možnosti [ \<zabezpečení BasicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94ed2-144">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="94ed2-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="94ed2-145">Example</span></span>  
 <span data-ttu-id="94ed2-146">Tato ukázka předvádí, jak implementovat aplikaci, která používá zabezpečení basicHttpBinding a Message.</span><span class="sxs-lookup"><span data-stu-id="94ed2-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="94ed2-147">V následujícím příkladu konfigurace služby určuje definice koncového bodu basicHttpBinding a odkazuje na konfiguraci vazby s názvem `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="94ed2-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="94ed2-148">Certifikát, který služba používá ke vzájemnému ověření pro klienta, je nastaven v `behaviors` části konfiguračního souboru `serviceCredentials` pod prvkem.</span><span class="sxs-lookup"><span data-stu-id="94ed2-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="94ed2-149">Režim ověřování, který se vztahuje na certifikát, který klient používá k ověření ve službě, je také nastaven v `behaviors` části `clientCertificate` pod prvkem.</span><span class="sxs-lookup"><span data-stu-id="94ed2-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="94ed2-150">V konfiguračním souboru klienta jsou zadány stejné podrobnosti o vazbě a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="94ed2-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
    <!-- This configuration defines the SecurityMode as Message and
         the clientCredentialType as Certificate. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
               is in the user's Trusted People store, then it will be trusted without performing a
               validation of the certificate's issuer chain. This setting is used here for convenience so that the
               sample can be run without having to have certificates issued by a certification authority (CA).
               This setting is less secure than the default, ChainTrust. The security implications of this
               setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="94ed2-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94ed2-151">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="94ed2-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="94ed2-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="94ed2-153">Vazby</span><span class="sxs-lookup"><span data-stu-id="94ed2-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="94ed2-154">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="94ed2-154">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="94ed2-155">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="94ed2-155">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="94ed2-156">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="94ed2-156">\<binding></span></span>](../../../misc/binding.md)
