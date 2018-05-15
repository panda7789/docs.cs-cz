---
title: '&lt;message&gt; – &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: f58fadbc3ac3f193232ad075c4973f6ac2f2d1f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a><span data-ttu-id="1213b-102">&lt;message&gt; – &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="1213b-102">&lt;message&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="1213b-103">Definuje nastavení pro zprávy úroveň zabezpečení [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1213b-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="1213b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1213b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1213b-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="1213b-105">\<bindings></span></span>  
<span data-ttu-id="1213b-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="1213b-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="1213b-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="1213b-107">\<binding></span></span>  
<span data-ttu-id="1213b-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="1213b-108">\<security></span></span>  
<span data-ttu-id="1213b-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="1213b-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1213b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1213b-110">Syntax</span></span>  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1213b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1213b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1213b-112">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1213b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1213b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1213b-113">Attributes</span></span>  
  
|<span data-ttu-id="1213b-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1213b-114">Attribute</span></span>|<span data-ttu-id="1213b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1213b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1213b-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="1213b-116">algorithmSuite</span></span>|<span data-ttu-id="1213b-117">Nastaví zprávu algoritmy šifrování a klíč wrap.</span><span class="sxs-lookup"><span data-stu-id="1213b-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="1213b-118">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, která určuje algoritmy a velikosti klíče.</span><span class="sxs-lookup"><span data-stu-id="1213b-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="1213b-119">Tyto algoritmy mapovat platformám zadaným v specifikace jazyka zásady zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="1213b-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="1213b-120">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="1213b-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="1213b-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="1213b-121">clientCredentialType</span></span>|<span data-ttu-id="1213b-122">Určuje typ pověření, který se má použít při ověřování klienta pomocí zabezpečení na základě zpráv.</span><span class="sxs-lookup"><span data-stu-id="1213b-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="1213b-123">Výchozí hodnota je `UserName`.</span><span class="sxs-lookup"><span data-stu-id="1213b-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="1213b-124">clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="1213b-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1213b-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1213b-125">Value</span></span>|<span data-ttu-id="1213b-126">Popis</span><span class="sxs-lookup"><span data-stu-id="1213b-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1213b-127">UserName</span><span class="sxs-lookup"><span data-stu-id="1213b-127">UserName</span></span>|<span data-ttu-id="1213b-128">-Vyžaduje ověření klienta k serveru pomocí pověření uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="1213b-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="1213b-129">Toto pověření musí být zadán pomocí [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1213b-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="1213b-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nepodporuje odesílání hodnotu hash hesla nebo odvozování klíče pomocí hesla a použití tyto klíče pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="1213b-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="1213b-131">Proto [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] vynucuje, aby přenos být zabezpečeny při použití pověření uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="1213b-131">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="1213b-132">Pro `basicHttpBinding`, to vyžaduje nastavení připojení SSL.</span><span class="sxs-lookup"><span data-stu-id="1213b-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="1213b-133">certifikát</span><span class="sxs-lookup"><span data-stu-id="1213b-133">Certificate</span></span>|<span data-ttu-id="1213b-134">Vyžaduje, aby na server používá certifikát ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="1213b-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="1213b-135">V takovém případě musí být zadán pomocí pověření klienta [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) a [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1213b-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="1213b-136">Kromě toho pokud používáte režim zabezpečení zprávy, klient musí být opatřena certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="1213b-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="1213b-137">Přihlašovací údaje služby v takovém případě musí být zadán pomocí <xref:System.ServiceModel.Description.ClientCredentials> třídy nebo `ClientCredentials` element chování a zadání službu certifikát, pomocí [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1213b-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1213b-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1213b-138">Child Elements</span></span>  
 <span data-ttu-id="1213b-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="1213b-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1213b-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1213b-140">Parent Elements</span></span>  
  
|<span data-ttu-id="1213b-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="1213b-141">Element</span></span>|<span data-ttu-id="1213b-142">Popis</span><span class="sxs-lookup"><span data-stu-id="1213b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1213b-143">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="1213b-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="1213b-144">Definuje možnosti zabezpečení pro [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1213b-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1213b-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="1213b-145">Example</span></span>  
 <span data-ttu-id="1213b-146">Tento příklad znázorňuje implementaci aplikace, která používá zabezpečení basicHttpBinding a zprávu.</span><span class="sxs-lookup"><span data-stu-id="1213b-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="1213b-147">V následujícím příkladu konfigurace pro službu definici koncového bodu určuje basicHttpBinding a odkazuje na vazbu konfigurace s názvem `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="1213b-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="1213b-148">Certifikát, který služba používá k vlastnímu ověření klienta je nastavena v `behaviors` oddíl konfiguračního souboru pod `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="1213b-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="1213b-149">Režim ověřování, který se vztahuje na certifikát, který klient použije k vlastnímu ověření služby je také nastavit `behaviors` oddílu pod `clientCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="1213b-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="1213b-150">Stejné podrobnosti vazby a zabezpečení jsou zadané v konfiguračním souboru klienta.</span><span class="sxs-lookup"><span data-stu-id="1213b-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1213b-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="1213b-151">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>  
 [<span data-ttu-id="1213b-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1213b-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1213b-153">Vazby</span><span class="sxs-lookup"><span data-stu-id="1213b-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1213b-154">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="1213b-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1213b-155">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="1213b-155">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1213b-156">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="1213b-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
