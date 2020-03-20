---
title: Vlastní zabezpečený koncový bod metadat
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183851"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="4f197-102">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="4f197-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="4f197-103">Tato ukázka ukazuje, jak implementovat službu s koncovým bodem zabezpečené metadata, který používá jednu z vazby exchange non-metadata a jak nakonfigurovat [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klienty pro načtení metadat z takového koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="4f197-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="4f197-104">Pro vystavení koncových bodů metadat jsou k dispozici dvě vazby poskytované systémem: mexHttpBinding a mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="4f197-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="4f197-105">mexHttpBinding se používá k vystavení koncového bodu metadat přes protokol HTTP nezabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="4f197-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="4f197-106">mexHttpsBinding se používá k vystavení koncového bodu metadat přes protokol HTTPS zabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="4f197-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="4f197-107">Tato ukázka ukazuje, jak vystavit koncový bod <xref:System.ServiceModel.WSHttpBinding>zabezpečené metadata pomocí .</span><span class="sxs-lookup"><span data-stu-id="4f197-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="4f197-108">To byste chtěli provést, pokud chcete změnit nastavení zabezpečení ve vazbě, ale nechcete používat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4f197-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="4f197-109">Pokud použijete mexHttpsBinding koncový bod metadat bude zabezpečený, ale neexistuje žádný způsob, jak změnit nastavení vazby.</span><span class="sxs-lookup"><span data-stu-id="4f197-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f197-110">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4f197-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="4f197-111">Služba</span><span class="sxs-lookup"><span data-stu-id="4f197-111">Service</span></span>  
 <span data-ttu-id="4f197-112">Služba v této ukázce má dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="4f197-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="4f197-113">Koncový bod aplikace `ICalculator` slouží smlouvy `WSHttpBinding` `ReliableSession` s `Message` povolenou a zabezpečení pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4f197-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="4f197-114">Koncový bod metadat také `WSHttpBinding`používá , se stejným `ReliableSession`nastavením zabezpečení, ale bez .</span><span class="sxs-lookup"><span data-stu-id="4f197-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="4f197-115">Zde je příslušná konfigurace:</span><span class="sxs-lookup"><span data-stu-id="4f197-115">Here is the relevant configuration:</span></span>  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="4f197-116">V mnoha dalších ukázkách koncový bod metadat `mexHttpBinding`používá výchozí , který není zabezpečený.</span><span class="sxs-lookup"><span data-stu-id="4f197-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="4f197-117">Zde jsou metadata `WSHttpBinding` zabezpečena pomocí `Message` zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4f197-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="4f197-118">Aby klienti metadat načíst tato metadata, musí být nakonfigurován s odpovídající vazby.</span><span class="sxs-lookup"><span data-stu-id="4f197-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="4f197-119">Tato ukázka ukazuje dva takové klienty.</span><span class="sxs-lookup"><span data-stu-id="4f197-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="4f197-120">První klient používá Svcutil.exe k načtení metadat a generování klientského kódu a konfigurace v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4f197-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="4f197-121">Vzhledem k tomu, že služba používá pro metadata nevýchozí vazbu, musí být nástroj Svcutil.exe specificky nakonfigurován tak, aby mohl získat metadata ze služby pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="4f197-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="4f197-122">Druhý klient používá `MetadataResolver` dynamicky načíst metadata pro známé smlouvy a potom vyvolat operace na dynamicky generované klienta.</span><span class="sxs-lookup"><span data-stu-id="4f197-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="4f197-123">Klient Svcutil</span><span class="sxs-lookup"><span data-stu-id="4f197-123">Svcutil client</span></span>  
 <span data-ttu-id="4f197-124">Při použití výchozí vazby `IMetadataExchange` k hostování koncového bodu můžete spustit svcutil.exe s adresou tohoto koncového bodu:</span><span class="sxs-lookup"><span data-stu-id="4f197-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="4f197-125">a funguje to.</span><span class="sxs-lookup"><span data-stu-id="4f197-125">and it works.</span></span> <span data-ttu-id="4f197-126">Ale v této ukázce server používá mimo výchozí koncový bod k hostování metadat.</span><span class="sxs-lookup"><span data-stu-id="4f197-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="4f197-127">Takže Svcutil.exe musí být instruován, aby použil správnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="4f197-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="4f197-128">To lze provést pomocí souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="4f197-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="4f197-129">Soubor Svcutil.exe.config vypadá jako normální konfigurační soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="4f197-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="4f197-130">Jedinými neobvyklými aspekty jsou název koncového bodu klienta a smlouva:</span><span class="sxs-lookup"><span data-stu-id="4f197-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="4f197-131">Název koncového bodu musí být název schématu adresy, kde jsou metadata hostována, a kontrakt koncového bodu musí být `IMetadataExchange`.</span><span class="sxs-lookup"><span data-stu-id="4f197-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="4f197-132">Proto při Svcutil.exe je spuštěn s příkazovým řádkem, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="4f197-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="4f197-133">vyhledá koncový bod s názvem "http" a smlouvy `IMetadataExchange` pro konfiguraci vazby a chování výměny komunikace s koncovým bodem metadat.</span><span class="sxs-lookup"><span data-stu-id="4f197-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="4f197-134">Zbytek souboru Svcutil.exe.config v ukázce určuje pověření konfigurace vazby a chování tak, aby odpovídaly konfiguraci koncového bodu metadat na serveru.</span><span class="sxs-lookup"><span data-stu-id="4f197-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="4f197-135">Aby svcutil.exe vyzvednout konfiguraci v Svcutil.exe.config, Svcutil.exe musí být ve stejném adresáři jako konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="4f197-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="4f197-136">V důsledku toho je nutné zkopírovat soubor Svcutil.exe z jeho umístění instalace do adresáře, který obsahuje soubor Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="4f197-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="4f197-137">Potom z tohoto adresáře spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4f197-137">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="4f197-138">Vedoucí ". \\" zajišťuje spuštění kopie souboru Svcutil.exe v tomto adresáři (ten, který má odpovídající soubor Svcutil.exe.config).</span><span class="sxs-lookup"><span data-stu-id="4f197-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="4f197-139">Klient MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="4f197-139">MetadataResolver client</span></span>  
 <span data-ttu-id="4f197-140">Pokud klient zná smlouvu a jak mluvit s metadaty v době návrhu, klient může dynamicky `MetadataResolver`zjistit vazbu a adresu koncových bodů aplikace pomocí .</span><span class="sxs-lookup"><span data-stu-id="4f197-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="4f197-141">Tento ukázkový klient to ukazuje a ukazuje, jak `MetadataResolver` nakonfigurovat vazbu `MetadataExchangeClient`a pověření používaná vytvořením a konfigurací rozhraní .</span><span class="sxs-lookup"><span data-stu-id="4f197-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="4f197-142">Stejné informace o vazbě a certifikátu, které se objevily v svcutil.exe.config, lze imperativně zadat na `MetadataExchangeClient`:</span><span class="sxs-lookup"><span data-stu-id="4f197-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="4f197-143">S `mexClient` nakonfigurované, můžeme výčet smluv, které `MetadataResolver` nás zajímají, a použít k načtení seznamu koncových bodů s těmito smlouvami:</span><span class="sxs-lookup"><span data-stu-id="4f197-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="4f197-144">Nakonec můžeme použít informace z těchto koncových bodů k inicializaci vazby a adresy `ChannelFactory` slouží k vytvoření kanálů pro komunikaci s koncovými body aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f197-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="4f197-145">Klíčovým bodem tohoto ukázkového klienta je ukázat, `MetadataResolver`že pokud používáte , a je nutné zadat vlastní vazby `MetadataExchangeClient` nebo chování pro komunikaci výměny metadat, můžete použít k určení těchto vlastních nastavení.</span><span class="sxs-lookup"><span data-stu-id="4f197-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="4f197-146">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="4f197-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="4f197-147">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f197-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4f197-148">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f197-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="4f197-149">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="4f197-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="4f197-150">Spusťte soubor Setup.bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="4f197-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="4f197-151">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="4f197-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="4f197-152">Všimněte si, že Setup.bat používá nástroj FindPrivateKey.exe, který je nainstalován spuštěním setupCertTool.bat z [jednorázového postupu instalace pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f197-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4f197-153">Spusťte klientskou aplikaci z \MetadataResolverClient\bin nebo \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="4f197-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="4f197-154">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="4f197-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="4f197-155">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4f197-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="4f197-156">Po dokončení ukázky odeberte certifikáty spuštěním souboru Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="4f197-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="4f197-157">Jiné ukázky zabezpečení používají stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="4f197-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="4f197-158">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="4f197-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="4f197-159">Na serveru spusťte . `setup.bat service`</span><span class="sxs-lookup"><span data-stu-id="4f197-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="4f197-160">Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="4f197-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="4f197-161">Na serveru upravte web.config tak, aby odrážel nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="4f197-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="4f197-162">To znamená změnit `findValue` atribut v [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="4f197-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="4f197-163">Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="4f197-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="4f197-164">Na straně klienta spusťte `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="4f197-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="4f197-165">Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem Client.com a exportuje klientský certifikát do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="4f197-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="4f197-166">V souboru App.config `MetadataResolverClient` v klientském počítači změňte hodnotu adresy koncového bodu mex tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="4f197-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="4f197-167">Provést nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="4f197-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="4f197-168">Změňte také výskyt "localhost" v souboru metadataResolverClient.cs na nový název certifikátu služby (plně kvalifikovaný název domény serveru).</span><span class="sxs-lookup"><span data-stu-id="4f197-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="4f197-169">Proveďte totéž pro App.config projektu SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="4f197-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="4f197-170">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="4f197-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="4f197-171">Na straně klienta spusťte `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="4f197-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="4f197-172">Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="4f197-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="4f197-173">Na serveru, `ImportClientCert.bat`spustit , To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="4f197-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="4f197-174">Na servisním počítači vytvořte projekt služby v sadě Visual Studio a vyberte stránku nápovědy ve webovém prohlížeči a ověřte, zda je spuštěný.</span><span class="sxs-lookup"><span data-stu-id="4f197-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="4f197-175">V klientském počítači spusťte metadataResolverClient nebo SvcutilClient z VS.</span><span class="sxs-lookup"><span data-stu-id="4f197-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="4f197-176">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4f197-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4f197-177">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="4f197-177">To clean up after the sample</span></span>  
  
- <span data-ttu-id="4f197-178">Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.</span><span class="sxs-lookup"><span data-stu-id="4f197-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f197-179">Tento skript neodebere certifikáty služeb na straně klienta při spuštění této ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="4f197-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="4f197-180">Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="4f197-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="4f197-181">Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`použijte následující příkaz: .</span><span class="sxs-lookup"><span data-stu-id="4f197-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="4f197-182">Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4f197-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4f197-183">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4f197-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f197-184">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4f197-184">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4f197-185">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4f197-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f197-186">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4f197-186">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
