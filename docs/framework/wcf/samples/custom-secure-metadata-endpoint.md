---
title: "Vlastní zabezpečený koncový bod metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cad98ab0df372b19efcf102cce3f80e3f7b0632f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="0432a-102">Vlastní zabezpečený koncový bod metadat</span><span class="sxs-lookup"><span data-stu-id="0432a-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="0432a-103">Tento příklad znázorňuje, jak implementovat služby Zabezpečené metadata koncový bod, který používá jedna z vazeb neobsahující metadata exchange a postup konfigurace [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klientům načíst metadata z těchto metadat koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="0432a-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="0432a-104">Nejsou k dispozici pro vystavení koncové body metadat dvě vazby poskytované systémem: mexHttpBinding a mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="0432a-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="0432a-105">mexHttpBinding se používá ke zveřejnění způsobem nezabezpečené koncový bod metadat prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0432a-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="0432a-106">mexHttpsBinding se používá ke zveřejnění koncový bod metadat prostřednictvím protokolu HTTPS zabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="0432a-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="0432a-107">Tato ukázka znázorňuje, jak vystavit koncový bod metadat zabezpečené pomocí <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0432a-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="0432a-108">Chcete by se to udělat, když chcete změnit nastavení zabezpečení na vazby, ale nechcete používat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0432a-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="0432a-109">Pokud použijete mexHttpsBinding bude váš koncový bod metadat zabezpečené, ale neexistuje žádný způsob, jak upravit nastavení vazby.</span><span class="sxs-lookup"><span data-stu-id="0432a-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0432a-110">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0432a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="0432a-111">Služba</span><span class="sxs-lookup"><span data-stu-id="0432a-111">Service</span></span>  
 <span data-ttu-id="0432a-112">Služba v této ukázce má dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="0432a-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="0432a-113">Koncový bod aplikace slouží `ICalculator` smlouvy na `WSHttpBinding` s `ReliableSession` povolená a `Message` zabezpečení pomocí certifikátů.</span><span class="sxs-lookup"><span data-stu-id="0432a-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="0432a-114">Koncový bod metadat také používá `WSHttpBinding`, stejné nastavení zabezpečení, ale ne `ReliableSession`.</span><span class="sxs-lookup"><span data-stu-id="0432a-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="0432a-115">Tady je relevantní konfigurace:</span><span class="sxs-lookup"><span data-stu-id="0432a-115">Here is the relevant configuration:</span></span>  
  
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
  
 <span data-ttu-id="0432a-116">V mnoha dalších ukázky koncový bod metadat používá výchozí `mexHttpBinding`, která není zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="0432a-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="0432a-117">Zde je metadata zabezpečené pomocí `WSHttpBinding` s `Message` zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0432a-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="0432a-118">Aby klienti metadata k načtení těchto metadat musejí být nakonfigurovány s odpovídající vazby.</span><span class="sxs-lookup"><span data-stu-id="0432a-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="0432a-119">Tento příklad ukazuje dva těchto klientů.</span><span class="sxs-lookup"><span data-stu-id="0432a-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="0432a-120">První klient použije Svcutil.exe pro načtení metadat a generovat kód klienta a konfigurace v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="0432a-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="0432a-121">Protože služba používá jiné než výchozí vazbu pro metadata, nástroje Svcutil.exe je potřeba nakonfigurovat tak, aby ho můžete získat metadata ze služby pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="0432a-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="0432a-122">Druhý klient použije `MetadataResolver` dynamicky načíst metadata pro kontraktu známé a pak vyvolání operací v dynamicky generovaném klientovi.</span><span class="sxs-lookup"><span data-stu-id="0432a-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="0432a-123">Svcutil klienta</span><span class="sxs-lookup"><span data-stu-id="0432a-123">Svcutil client</span></span>  
 <span data-ttu-id="0432a-124">Při použití výchozí vazbu na hostitele vaší `IMetadataExchange` koncový bod, můžete spustit Svcutil.exe s adresou tohoto koncového bodu:</span><span class="sxs-lookup"><span data-stu-id="0432a-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="0432a-125">a metoda funguje.</span><span class="sxs-lookup"><span data-stu-id="0432a-125">and it works.</span></span> <span data-ttu-id="0432a-126">Ale v této ukázce server používá k hostování metadata koncový bod jiné než výchozí.</span><span class="sxs-lookup"><span data-stu-id="0432a-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="0432a-127">Proto musí být Svcutil.exe pokyn k použití správné vazby.</span><span class="sxs-lookup"><span data-stu-id="0432a-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="0432a-128">To lze provést pomocí souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="0432a-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="0432a-129">Soubor Svcutil.exe.config vypadá jako normální klienta konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0432a-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="0432a-130">Pouze neobvyklou aspekty jsou název koncového bodu klienta a kontraktu:</span><span class="sxs-lookup"><span data-stu-id="0432a-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="0432a-131">Název koncového bodu musí být název schématu adresy, na kterém je hostována metadata a koncového bodu kontraktu musí být `IMetadataExchange`.</span><span class="sxs-lookup"><span data-stu-id="0432a-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="0432a-132">Když je proto Svcutil.exe spusťte pomocí příkazového řádku například následující:</span><span class="sxs-lookup"><span data-stu-id="0432a-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="0432a-133">Vypadá to, pro koncový bod s názvem "http" a kontrakt `IMetadataExchange` ke konfiguraci vazby a chování exchange pro komunikaci s koncovým bodem metadat.</span><span class="sxs-lookup"><span data-stu-id="0432a-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="0432a-134">Zbytek souboru Svcutil.exe.config v ukázce určuje Konfigurace vazeb a chování přihlašovacích údajů podle serveru konfigurace koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="0432a-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="0432a-135">Aby Svcutil.exe zachycení konfigurace v Svcutil.exe.config Svcutil.exe musí být ve stejném adresáři jako konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="0432a-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="0432a-136">V důsledku toho je nutné zkopírovat Svcutil.exe z umístění instalace do adresáře, který obsahuje soubor Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="0432a-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="0432a-137">Potom z adresáře, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="0432a-137">Then from that directory, run the following command:</span></span>  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="0432a-138">Úvodního ". \\"zajistí, že je použít kopii Svcutil.exe v tomto adresáři (ten, který má odpovídající Svcutil.exe.config).</span><span class="sxs-lookup"><span data-stu-id="0432a-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="0432a-139">Třídy MetadataResolver klienta</span><span class="sxs-lookup"><span data-stu-id="0432a-139">MetadataResolver client</span></span>  
 <span data-ttu-id="0432a-140">Pokud klient zná kontrakt a postupy, aby komunikoval s metadaty v době návrhu, klienta můžete dynamicky zjistit vazeb a adresy koncových bodů aplikace pomocí `MetadataResolver`.</span><span class="sxs-lookup"><span data-stu-id="0432a-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="0432a-141">Tato ukázka klienta ukazuje to, znázorňující postup konfigurace vazby a pověření používaná `MetadataResolver` pomocí vytvoření a konfigurace `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="0432a-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="0432a-142">Imperativní na lze zadat stejný certifikát a vazeb informace, které zobrazovaly v Svcutil.exe.config `MetadataExchangeClient`:</span><span class="sxs-lookup"><span data-stu-id="0432a-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="0432a-143">S `mexClient` nakonfigurovaná, jsme výčet kontrakty jsme zájem a použijte `MetadataResolver` načíst seznam koncových bodů s tyto smlouvy:</span><span class="sxs-lookup"><span data-stu-id="0432a-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="0432a-144">Nakonec informace z těchto koncových bodů můžete použít k chybě při inicializaci vazby a adresu `ChannelFactory` použít k vytvoření kanálů pro komunikaci s koncovými body aplikace.</span><span class="sxs-lookup"><span data-stu-id="0432a-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="0432a-145">Bodem klíče klienta Tato ukázka je prokázat, že, pokud používáte `MetadataResolver`a je nutné zadat vlastní vazby nebo chování pro komunikaci se exchange metadata, můžete použít `MetadataExchangeClient` k určení tato vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="0432a-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="0432a-146">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="0432a-146">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="0432a-147">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0432a-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0432a-148">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0432a-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="0432a-149">Ke spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="0432a-149">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="0432a-150">Spuštění Setup.bat od vzorku instalační složku.</span><span class="sxs-lookup"><span data-stu-id="0432a-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="0432a-151">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="0432a-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="0432a-152">Všimněte si, že Setup.bat používá nástroj FindPrivateKey.exe, který je nainstalovaná, spuštěním setupCertTool.bat z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0432a-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0432a-153">Spusťte klientskou aplikaci z \MetadataResolverClient\bin nebo \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="0432a-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="0432a-154">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="0432a-154">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="0432a-155">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="0432a-155">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
4.  <span data-ttu-id="0432a-156">Odeberte certifikáty spuštěním Cleanup.bat po dokončení se vzorkem.</span><span class="sxs-lookup"><span data-stu-id="0432a-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="0432a-157">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="0432a-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="0432a-158">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="0432a-158">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="0432a-159">Na serveru, spusťte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="0432a-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="0432a-160">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="0432a-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2.  <span data-ttu-id="0432a-161">Na serveru upravte soubor Web.config tak, aby odrážely novou název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="0432a-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="0432a-162">To znamená, změnit `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="0432a-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3.  <span data-ttu-id="0432a-163">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="0432a-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4.  <span data-ttu-id="0432a-164">Na klientovi, spusťte `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="0432a-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="0432a-165">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem Client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="0432a-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5.  <span data-ttu-id="0432a-166">V souboru App.config `MetadataResolverClient` na klientský počítač, změňte hodnotu adresa koncového bodu mex tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="0432a-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="0432a-167">Provedete to nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="0432a-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="0432a-168">Výskyt řetězce "localhost" v souboru metadataResolverClient.cs také změníte na nový název certifikátu služby (plně kvalifikovaný název domény serveru).</span><span class="sxs-lookup"><span data-stu-id="0432a-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="0432a-169">Stejnou věc udělat pro App.config SvcutilClient projektu.</span><span class="sxs-lookup"><span data-stu-id="0432a-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6.  <span data-ttu-id="0432a-170">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="0432a-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7.  <span data-ttu-id="0432a-171">Na klientovi, spusťte `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="0432a-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="0432a-172">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="0432a-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8.  <span data-ttu-id="0432a-173">Na serveru, spusťte `ImportClientCert.bat`, tento klientský certifikát naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="0432a-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="0432a-174">Na počítači služby sestavení projektu služby v sadě Visual Studio a vyberte stránku nápovědy ve webovém prohlížeči a ověřte, zda je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="0432a-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="0432a-175">V klientském počítači spusťte MetadataResolverClient nebo SvcutilClient ze sady VS.</span><span class="sxs-lookup"><span data-stu-id="0432a-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1.  <span data-ttu-id="0432a-176">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="0432a-176">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0432a-177">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="0432a-177">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="0432a-178">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="0432a-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0432a-179">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="0432a-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="0432a-180">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty mezi počítači, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="0432a-180">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="0432a-181">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="0432a-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="0432a-182">Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="0432a-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0432a-183">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0432a-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0432a-184">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0432a-184">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0432a-185">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0432a-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0432a-186">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0432a-186">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a><span data-ttu-id="0432a-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="0432a-187">See Also</span></span>
