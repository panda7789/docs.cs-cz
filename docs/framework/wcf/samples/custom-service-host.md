---
title: Vlastní hostitel služby
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 09a69e489c4b4eb5d3af6e2e74316e678be3d049
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555996"
---
# <a name="custom-service-host"></a><span data-ttu-id="06460-102">Vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="06460-102">Custom Service Host</span></span>
<span data-ttu-id="06460-103">Tato ukázka předvádí, jak používat vlastní odvozený ze <xref:System.ServiceModel.ServiceHost> třídy pro úpravu chování za běhu služby.</span><span class="sxs-lookup"><span data-stu-id="06460-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="06460-104">Tento přístup poskytuje opakovaně použitelné alternativu ke konfiguraci velkým množstvím služeb v běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="06460-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="06460-105">Ukázka také ukazuje, jak používat <xref:System.ServiceModel.Activation.ServiceHostFactory> třídu použít vlastní hostitel služby v prostředí hostování internetové informační služby (IIS) nebo Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="06460-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06460-106">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="06460-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06460-107">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="06460-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06460-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="06460-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06460-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="06460-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="06460-110">O scénář</span><span class="sxs-lookup"><span data-stu-id="06460-110">About the Scenario</span></span>  
 <span data-ttu-id="06460-111">Pokud chcete zabránit neúmyslnému zveřejnění metadat služby potenciálně citlivých, výchozí konfigurace pro služby Windows Communication Foundation (WCF) zakáže publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="06460-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="06460-112">Toto chování je ve výchozím nastavení zabezpečený, ale také znamená, že nemůžete použít metadat importovat nástroj (například Svcutil.exe) ke generování kódu klienta, který je potřeba volat službu, není-li v konfiguraci není explicitně povoleno chování publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="06460-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="06460-113">Publikování metadat pro velký počet služeb zahrnuje přidání stejné prvky konfigurace pro jednotlivé služby, což vede k velké množství informací o konfiguraci, která je v podstatě stejné.</span><span class="sxs-lookup"><span data-stu-id="06460-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="06460-114">Jako alternativu ke konfiguraci jednotlivých služeb samostatně je možné psát imperativního kódu, který umožňuje publikování jednou metadat a pak znovu použít tento kód napříč několika různých služeb.</span><span class="sxs-lookup"><span data-stu-id="06460-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="06460-115">To lze provést tak, že vytvoříte novou třídu, která je odvozena z <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`– metoda () imperativně přidat chování publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="06460-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06460-116">Pro přehlednost Tato ukázka ukazuje, jak vytvořit koncový bod publikování metadat zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="06460-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="06460-117">Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené uživatele a musí tak, aby byl veřejně pocházejí metadata služby odpovídající věnovat pozornost před nasazením tyto koncové body.</span><span class="sxs-lookup"><span data-stu-id="06460-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="06460-118">Implementace vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="06460-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="06460-119"><xref:System.ServiceModel.ServiceHost> Třída zveřejňuje několik užitečné virtuální metody, které můžete přepsat dědice ke změně chování za běhu služby.</span><span class="sxs-lookup"><span data-stu-id="06460-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="06460-120">Například `ApplyConfiguration`– metoda () načte informace o konfiguraci služeb z konfigurace úložiště a mění hostitele <xref:System.ServiceModel.Description.ServiceDescription> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="06460-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="06460-121">Výchozí implementace načte konfiguraci z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="06460-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="06460-122">Můžete přepsat vlastní implementace `ApplyConfiguration`() pro další úpravu <xref:System.ServiceModel.Description.ServiceDescription> pomocí imperativního kódu nebo dokonce i úplně nahradit výchozí konfigurace úložiště.</span><span class="sxs-lookup"><span data-stu-id="06460-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="06460-123">Chcete-li například čtení konfigurace koncového bodu služby z databáze místo souboru konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="06460-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="06460-124">V tomto příkladu chceme vytvořit vlastní hostitel služby, který přidá třídě ServiceMetadataBehavior (který umožňuje publikování metadat), i když toto chování se nepřidá explicitně v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="06460-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="06460-125">K tomu vytvoříme novou třídu, která dědí z <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="06460-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```  
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to   
    //alter the ServiceDescription prior to opening  
    //the service host.   
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();       
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="06460-126">Protože jsme nechcete ignorovat všechny konfigurace, který byl poskytnut v konfiguračním souboru aplikace, první věc, kterou naše přepsání `ApplyConfiguration`nemá () je volání základní implementaci.</span><span class="sxs-lookup"><span data-stu-id="06460-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="06460-127">Po dokončení této metody můžete imperativně přidáme <xref:System.ServiceModel.Description.ServiceMetadataBehavior> popis, pomocí následujících imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="06460-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```  
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,   
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="06460-128">Poslední věcí, kterou naše `ApplyConfiguration`přepsání (), musíte udělat, je přidat výchozí koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="06460-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="06460-129">Podle konvence je vytvořen jeden koncový bod metadat pro každý identifikátor URI v kolekci adres BaseAddresses hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="06460-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```  
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="06460-130">Použití vlastní hostitel služby v hostování na vlastním serveru</span><span class="sxs-lookup"><span data-stu-id="06460-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="06460-131">Teď, když jsme dokončili naše vlastní implementace ServiceHost, jsme slouží k přidání chování publikování metadat k libovolné službě hostováním danou službu v rámci instance naší `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="06460-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="06460-132">Následující kód ukazuje, jak ho použít ve scénáři hostování na vlastním serveru.</span><span class="sxs-lookup"><span data-stu-id="06460-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="06460-133">Naše vlastního hostitele stále načítá konfigurace koncového bodu služby z konfiguračního souboru aplikace, tak, jako kdyby jsme použili výchozí <xref:System.ServiceModel.ServiceHost> třídy pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="06460-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="06460-134">Ale vzhledem k tomu, že jsme přidali logiky povolit publikování v rámci naší vlastního hostitele metadat, jsme již musíte povolit explicitně chování při publikování v konfiguraci metadat.</span><span class="sxs-lookup"><span data-stu-id="06460-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="06460-135">Tento přístup má různé výhody, pokud vytváříte aplikaci, která obsahuje několik služeb a chcete povolit publikování metadat na každém z nich bez psaní stejný konfigurační prvky pořád dokola.</span><span class="sxs-lookup"><span data-stu-id="06460-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="06460-136">Použití vlastní hostitel služby IIS nebo WAS</span><span class="sxs-lookup"><span data-stu-id="06460-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="06460-137">Používání vlastní hostitel služby ve scénářích hostování na vlastním serveru je jasné, protože je kód aplikace, která je nakonec odpovědné za vytváření a otevírání instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="06460-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="06460-138">IIS nebo WAS hostitelské prostředí ale infrastruktura WCF je dynamicky vytvoření instance hostitele vaší služby odpověď na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="06460-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="06460-139">Vlastní Obsluha hostitelů lze také v toto hostitelské prostředí, ale vyžadují další kód ve formuláři ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="06460-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="06460-140">Následující kód ukazuje odvozený ze <xref:System.ServiceModel.Activation.ServiceHostFactory> , který vrátí instance naší vlastní `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="06460-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```  
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,   
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)   
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,     
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="06460-141">Jak je vidět, implementace vlastního ServiceHostFactory je velmi jednoduché.</span><span class="sxs-lookup"><span data-stu-id="06460-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="06460-142">Všechny vlastní logiku se nachází uvnitř implementace ServiceHost; objekt pro vytváření vrátí instanci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="06460-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="06460-143">Určený objekt pro vytváření vlastní implementace služby musí přidáme některá další metadata do souboru .svc služby.</span><span class="sxs-lookup"><span data-stu-id="06460-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="06460-144">Tady jsme přidali další `Factory` atribut `@ServiceHost` směrnice a předané CLR zadejte název objektu pro vytváření naše vlastní jako hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="06460-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="06460-145">Když služba IIS nebo WAS obdrží zprávu pro tuto službu, infrastruktury hostování WCF nejprve vytvoří instanci ServiceHostFactory a potom vytvořte instanci samotného hostitele služby pomocí volání `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="06460-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="06460-146">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="06460-146">Running the Sample</span></span>  
 <span data-ttu-id="06460-147">I když tato ukázka poskytuje plně funkčního klienta a implementaci služby, je bod ukázku si ukážeme, jak chcete změnit chování služby za běhu pomocí vlastního hostitele., proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="06460-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="06460-148">Chcete-li sledovat účinek vlastního hostitele</span><span class="sxs-lookup"><span data-stu-id="06460-148">To observe the effect of the custom host</span></span>  
  
1.  <span data-ttu-id="06460-149">Otevřete soubor Web.config služby a podívejte se, že neexistuje žádná konfigurace explicitně povolení metadat služby.</span><span class="sxs-lookup"><span data-stu-id="06460-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2.  <span data-ttu-id="06460-150">Otevřete soubor SVC služby a zda se zobrazila zpráva jeho @ServiceHost direktiva obsahuje atribut Factory, který určuje název vlastního ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="06460-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06460-151">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="06460-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06460-152">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06460-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="06460-153">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06460-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="06460-154">Po řešení je sestavený Build, spusťte Setup.bat nastavit aplikaci ServiceModelSamples [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06460-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="06460-155">Adresář ServiceModelSamples by se měla objevit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="06460-155">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="06460-156">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06460-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="06460-157">Chcete-li odebrat [!INCLUDE[iisver](../../../../includes/iisver-md.md)] běhu Cleanup.bat aplikace.</span><span class="sxs-lookup"><span data-stu-id="06460-157">To remove the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06460-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06460-158">See also</span></span>
- [<span data-ttu-id="06460-159">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="06460-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
