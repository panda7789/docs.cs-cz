---
title: '&lt;message&gt; – &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 08307d1120904fc703e7b76616aacce7e153929a
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842590"
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a><span data-ttu-id="3b4f5-102">&lt;message&gt; – &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3b4f5-102">&lt;message&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="3b4f5-103">Definuje nastavení pro zabezpečení na úrovni zprávy z [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3b4f5-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="3b4f5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3b4f5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3b4f5-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3b4f5-105">\<bindings></span></span>  
<span data-ttu-id="3b4f5-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3b4f5-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="3b4f5-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3b4f5-107">\<binding></span></span>  
<span data-ttu-id="3b4f5-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3b4f5-108">\<security></span></span>  
<span data-ttu-id="3b4f5-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="3b4f5-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4f5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b4f5-110">Syntax</span></span>  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b4f5-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b4f5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3b4f5-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b4f5-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b4f5-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b4f5-113">Attributes</span></span>  
  
|<span data-ttu-id="3b4f5-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3b4f5-114">Attribute</span></span>|<span data-ttu-id="3b4f5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3b4f5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b4f5-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="3b4f5-116">algorithmSuite</span></span>|<span data-ttu-id="3b4f5-117">Nastaví zprávu algoritmy šifrování a klíč zalamování řádků.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="3b4f5-118">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, která určuje algoritmy a velikosti klíče.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="3b4f5-119">Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="3b4f5-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="3b4f5-120">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="3b4f5-121">Typ clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="3b4f5-121">clientCredentialType</span></span>|<span data-ttu-id="3b4f5-122">Určuje typ přihlašovacích údajů pro použití při ověřování klientů pomocí zabezpečení na základě zpráv.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="3b4f5-123">Výchozí hodnota je `UserName`.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3b4f5-124">Typ clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="3b4f5-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3b4f5-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3b4f5-125">Value</span></span>|<span data-ttu-id="3b4f5-126">Popis</span><span class="sxs-lookup"><span data-stu-id="3b4f5-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3b4f5-127">UserName</span><span class="sxs-lookup"><span data-stu-id="3b4f5-127">UserName</span></span>|<span data-ttu-id="3b4f5-128">-Vyžaduje ověření klienta k serveru pomocí přihlašovacích údajů uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="3b4f5-129">Tyto přihlašovací údaje musí být zadaná pomocí [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="3b4f5-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="3b4f5-130">-WCF nepodporuje odesílání hodnotou hash hesla nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="3b4f5-131">Proto WCF vynutí, že přenos zabezpečit při použití pověření uživatelských jmen.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="3b4f5-132">Pro `basicHttpBinding`, to vyžaduje nastavení kanálu SSL.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="3b4f5-133">Certifikát</span><span class="sxs-lookup"><span data-stu-id="3b4f5-133">Certificate</span></span>|<span data-ttu-id="3b4f5-134">Vyžaduje se k serveru, používá certifikát ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="3b4f5-135">Pověření klienta nejsou v tomto případě musí být zadaná pomocí [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) a [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="3b4f5-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="3b4f5-136">Kromě toho-když používají režim zabezpečených zpráv, klient musí být zřízená s certifikátem služby.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="3b4f5-137">Přihlašovací údaje služby v tomto případě musí být zadaná pomocí <xref:System.ServiceModel.Description.ClientCredentials> třídy nebo `ClientCredentials` prvek chování a zadáním služby certifikátu pomocí [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="3b4f5-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b4f5-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3b4f5-138">Child Elements</span></span>  
 <span data-ttu-id="3b4f5-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="3b4f5-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b4f5-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b4f5-140">Parent Elements</span></span>  
  
|<span data-ttu-id="3b4f5-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b4f5-141">Element</span></span>|<span data-ttu-id="3b4f5-142">Popis</span><span class="sxs-lookup"><span data-stu-id="3b4f5-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b4f5-143">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3b4f5-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="3b4f5-144">Definuje možnosti zabezpečení pro [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3b4f5-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3b4f5-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b4f5-145">Example</span></span>  
 <span data-ttu-id="3b4f5-146">Tento příklad ukazuje, jak implementovat aplikaci, která používá zabezpečení tříd basicHttpBinding a zprávy.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="3b4f5-147">V následujícím příkladu konfigurace pro službu, definice koncového bodu, určuje, basicHttpBinding a odkazuje na konfiguraci vazby s názvem `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="3b4f5-148">Nastavení certifikátu, který službu používá ke svému ověření ke klientovi `behaviors` souboru konfigurace v rámci `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="3b4f5-149">Režim ověřování, který se vztahuje na certifikát, který klient použije ke svému ověření ke službě je také nastavena `behaviors` části `clientCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="3b4f5-150">Stejné informace pro vazby a zabezpečení jsou uvedeny v souboru konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="3b4f5-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
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
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b4f5-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b4f5-151">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>  
 [<span data-ttu-id="3b4f5-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3b4f5-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3b4f5-153">Vazby</span><span class="sxs-lookup"><span data-stu-id="3b4f5-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3b4f5-154">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3b4f5-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3b4f5-155">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3b4f5-155">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="3b4f5-156">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3b4f5-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
