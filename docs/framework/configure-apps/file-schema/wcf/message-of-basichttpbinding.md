---
title: <message> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 748a734af8cf6767ce47cfffce9aec3ef627cb44
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736738"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="abd62-102">\<message> z \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="abd62-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="abd62-103">Definuje nastavení pro zabezpečení na úrovni zprávy [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="abd62-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="abd62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abd62-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abd62-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="abd62-105">Attributes and Elements</span></span>  
 <span data-ttu-id="abd62-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="abd62-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abd62-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="abd62-107">Attributes</span></span>  
  
|<span data-ttu-id="abd62-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="abd62-108">Attribute</span></span>|<span data-ttu-id="abd62-109">Popis</span><span class="sxs-lookup"><span data-stu-id="abd62-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abd62-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="abd62-110">algorithmSuite</span></span>|<span data-ttu-id="abd62-111">Nastaví šifrování zpráv a algoritmy pro zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="abd62-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="abd62-112">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> , který určuje algoritmy a velikosti klíčů.</span><span class="sxs-lookup"><span data-stu-id="abd62-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="abd62-113">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="abd62-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="abd62-114">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="abd62-114">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="abd62-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="abd62-115">clientCredentialType</span></span>|<span data-ttu-id="abd62-116">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení založeného na zprávách.</span><span class="sxs-lookup"><span data-stu-id="abd62-116">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="abd62-117">Výchozí formát je `UserName`.</span><span class="sxs-lookup"><span data-stu-id="abd62-117">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="abd62-118">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="abd62-118">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="abd62-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="abd62-119">Value</span></span>|<span data-ttu-id="abd62-120">Description</span><span class="sxs-lookup"><span data-stu-id="abd62-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="abd62-121">UserName</span><span class="sxs-lookup"><span data-stu-id="abd62-121">UserName</span></span>|<span data-ttu-id="abd62-122">– Vyžaduje, aby byl klient ověřený pro server s přihlašovacími údaji uživatele.</span><span class="sxs-lookup"><span data-stu-id="abd62-122">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="abd62-123">Toto pověření je nutné zadat pomocí [\<clientCredentials>](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="abd62-123">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="abd62-124">-WCF nepodporuje odeslání výtahu hesla ani odvození klíčů pomocí hesel a použití takových klíčů pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="abd62-124">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="abd62-125">Proto WCF vynutilo zabezpečení přenosu při použití přihlašovacích údajů uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="abd62-125">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="abd62-126">V případě nástroje `basicHttpBinding` to vyžaduje vytvoření kanálu SSL.</span><span class="sxs-lookup"><span data-stu-id="abd62-126">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="abd62-127">Certifikát</span><span class="sxs-lookup"><span data-stu-id="abd62-127">Certificate</span></span>|<span data-ttu-id="abd62-128">Vyžaduje, aby byl klient ověřený na serveru pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="abd62-128">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="abd62-129">Přihlašovací údaje klienta v tomto případě je nutné zadat pomocí [\<clientCredentials>](clientcredentials.md) a [\<clientCertificate>](clientcertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="abd62-129">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="abd62-130">Kromě toho je nutné při použití režimu zabezpečení zpráv zřídit klienta s certifikátem služby.</span><span class="sxs-lookup"><span data-stu-id="abd62-130">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="abd62-131">Pověření služby v tomto případě je nutné zadat pomocí <xref:System.ServiceModel.Description.ClientCredentials> elementu Class nebo `ClientCredentials` Behavior a zadáním certifikátu služby pomocí [\<serviceCertificate>](servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="abd62-131">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abd62-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="abd62-132">Child Elements</span></span>  
 <span data-ttu-id="abd62-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="abd62-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abd62-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="abd62-134">Parent Elements</span></span>  
  
|<span data-ttu-id="abd62-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="abd62-135">Element</span></span>|<span data-ttu-id="abd62-136">Description</span><span class="sxs-lookup"><span data-stu-id="abd62-136">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="abd62-137">Definuje možnosti zabezpečení pro [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="abd62-137">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="abd62-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="abd62-138">Example</span></span>  
 <span data-ttu-id="abd62-139">Tato ukázka předvádí, jak implementovat aplikaci, která používá zabezpečení basicHttpBinding a Message.</span><span class="sxs-lookup"><span data-stu-id="abd62-139">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="abd62-140">V následujícím příkladu konfigurace služby určuje definice koncového bodu basicHttpBinding a odkazuje na konfiguraci vazby s názvem `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="abd62-140">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="abd62-141">Certifikát, který služba používá ke vzájemnému ověření pro klienta, je nastaven v `behaviors` části konfiguračního souboru pod `serviceCredentials` prvkem.</span><span class="sxs-lookup"><span data-stu-id="abd62-141">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="abd62-142">Režim ověřování, který se vztahuje na certifikát, který klient používá k ověření ve službě, je také nastaven v `behaviors` části pod `clientCertificate` prvkem.</span><span class="sxs-lookup"><span data-stu-id="abd62-142">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="abd62-143">V konfiguračním souboru klienta jsou zadány stejné podrobnosti o vazbě a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="abd62-143">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abd62-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="abd62-144">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="abd62-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="abd62-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="abd62-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="abd62-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="abd62-147">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="abd62-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="abd62-148">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="abd62-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
