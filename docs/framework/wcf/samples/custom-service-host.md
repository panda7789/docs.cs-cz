---
title: Vlastní hostitel služby
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 2aed557d1d045c08aed206660aa7b4b75ffe0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145069"
---
# <a name="custom-service-host"></a><span data-ttu-id="d251a-102">Vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="d251a-102">Custom Service Host</span></span>
<span data-ttu-id="d251a-103">Tato ukázka ukazuje, jak použít <xref:System.ServiceModel.ServiceHost> vlastní derivaci třídy ke změně chování za běhu služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="d251a-104">Tento přístup poskytuje opakovaně použitelnou alternativu ke konfiguraci velkého počtu služeb běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d251a-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="d251a-105">Ukázka také ukazuje, jak <xref:System.ServiceModel.Activation.ServiceHostFactory> použít třídu k použití vlastního ServiceHost v internetové informační službě (IIS) nebo službě aktivace procesů systému Windows (WAS) hostingové prostředí.</span><span class="sxs-lookup"><span data-stu-id="d251a-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d251a-106">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d251a-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d251a-107">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d251a-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d251a-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d251a-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d251a-109">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d251a-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="d251a-110">O scénáři</span><span class="sxs-lookup"><span data-stu-id="d251a-110">About the scenario</span></span>
 <span data-ttu-id="d251a-111">Chcete-li zabránit neúmyslnému zveřejnění potenciálně citlivých metadat služby, výchozí konfigurace pro služby WCF (Windows Communication Foundation) zakáže publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="d251a-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="d251a-112">Toto chování je ve výchozím nastavení zabezpečené, ale také znamená, že nelze použít nástroj pro import metadat (například Svcutil.exe) ke generování klientského kódu potřebného k volání služby, pokud není v konfiguraci explicitně povoleno chování publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="d251a-113">Povolení publikování metadat pro velký počet služeb zahrnuje přidání stejných prvků konfigurace do každé jednotlivé služby, což má za následek velké množství informací o konfiguraci, která je v podstatě stejná.</span><span class="sxs-lookup"><span data-stu-id="d251a-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="d251a-114">Jako alternativu ke konfiguraci jednotlivých služeb jednotlivě je možné napsat imperativní kód, který umožňuje publikování metadat jednou a potom znovu použít tento kód v několika různých službách.</span><span class="sxs-lookup"><span data-stu-id="d251a-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="d251a-115">Toho lze dosáhnout vytvořením nové třídy, která je odvozena od <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`() metodu, aby bylo nutné přidat chování publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="d251a-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d251a-116">Pro přehlednost tato ukázka ukazuje, jak vytvořit koncový bod publikování nezabezpečených metadat.</span><span class="sxs-lookup"><span data-stu-id="d251a-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="d251a-117">Tyto koncové body jsou potenciálně k dispozici anonymní matné neověřené spotřebitele a je třeba dbát na to před nasazením těchto koncových bodů, aby bylo zajištěno, že je vhodné veřejně zveřejnit metadata služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="d251a-118">Implementace vlastního ServiceHost</span><span class="sxs-lookup"><span data-stu-id="d251a-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="d251a-119">Třída <xref:System.ServiceModel.ServiceHost> zveřejňuje několik užitečných virtuálních metod, které dědicové mohou přepsat změnit chování za běhu služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="d251a-120">Například `ApplyConfiguration`() metoda čte informace o konfiguraci služby z <xref:System.ServiceModel.Description.ServiceDescription> úložiště konfigurace a odpovídajícím způsobem změní hostitele.</span><span class="sxs-lookup"><span data-stu-id="d251a-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="d251a-121">Výchozí implementace čte konfiguraci z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d251a-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="d251a-122">Vlastní implementace můžete `ApplyConfiguration`přepsat () dále <xref:System.ServiceModel.Description.ServiceDescription> změnit pomocí imperativní kód nebo dokonce nahradit výchozí úložiště konfigurace úplně.</span><span class="sxs-lookup"><span data-stu-id="d251a-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="d251a-123">Chcete-li například číst konfiguraci koncového bodu služby z databáze namísto konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d251a-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="d251a-124">V této ukázce chceme vytvořit vlastní ServiceHost, který přidá ServiceMetadataBehavior (který umožňuje publikování metadat), i v případě, že toto chování není explicitně přidán do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="d251a-125">K dosažení tohoto cíle vytvoříme novou <xref:System.ServiceModel.ServiceHost> třídu, `ApplyConfiguration`která dědí z a přepíše ().</span><span class="sxs-lookup"><span data-stu-id="d251a-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp
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
  
 <span data-ttu-id="d251a-126">Vzhledem k tomu, že nechceme ignorovat žádnou konfiguraci, která byla poskytnuta `ApplyConfiguration`v konfiguračním souboru aplikace, první věc, kterou naše přepsání () dělá, je volání základní implementace.</span><span class="sxs-lookup"><span data-stu-id="d251a-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="d251a-127">Jakmile tato metoda dokončí, můžeme imperativně přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do popisu pomocí následujícího imperativníkód.</span><span class="sxs-lookup"><span data-stu-id="d251a-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="d251a-128">Poslední věc, `ApplyConfiguration`kterou naše () přepsání musí udělat, je přidat výchozí koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="d251a-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="d251a-129">Podle konvence je vytvořen jeden koncový bod metadat pro každý identifikátor URI v kolekci BaseAddresses hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```csharp
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="d251a-130">Použití vlastního ServiceHost v samoobslužném hostiteli</span><span class="sxs-lookup"><span data-stu-id="d251a-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="d251a-131">Nyní, když jsme dokončili naši vlastní implementaci ServiceHost, můžeme ji použít k přidání chování publikování `SelfDescribingServiceHost`metadat do libovolné služby tím, že tuto službu hostujeme uvnitř instance našeho .</span><span class="sxs-lookup"><span data-stu-id="d251a-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="d251a-132">Následující kód ukazuje, jak ji použít ve scénáři vlastního hostitele.</span><span class="sxs-lookup"><span data-stu-id="d251a-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="d251a-133">Náš vlastní hostitel stále čte konfiguraci koncového bodu služby z konfiguračního <xref:System.ServiceModel.ServiceHost> souboru aplikace, stejně jako kdybychom použili výchozí třídu k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="d251a-134">Protože jsme však přidali logiku umožňující publikování metadat uvnitř našeho vlastního hostitele, již nesmíme explicitně povolit chování publikování metadat v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d251a-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="d251a-135">Tento přístup má výraznou výhodu při vytváření aplikace, která obsahuje několik služeb a chcete povolit publikování metadat na každé z nich bez psaní stejné konfigurační prvky znovu a znovu.</span><span class="sxs-lookup"><span data-stu-id="d251a-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="d251a-136">Použití vlastního servicehost ve službě IIS nebo WAS</span><span class="sxs-lookup"><span data-stu-id="d251a-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="d251a-137">Použití vlastního hostitele služby ve scénářích vlastního hostitele je jednoduché, protože je to kód aplikace, který je nakonec zodpovědný za vytvoření a otevření instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="d251a-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="d251a-138">V hostitelském prostředí služby IIS nebo WAS však infrastruktura WCF dynamicky instanci hostitele služby v reakci na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="d251a-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="d251a-139">Vlastní hostitelé služeb lze také použít v tomto hostitelském prostředí, ale vyžadují nějaký další kód ve formě ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="d251a-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="d251a-140">Následující kód ukazuje <xref:System.ServiceModel.Activation.ServiceHostFactory> derivaci, která vrací `SelfDescribingServiceHost`instance našeho vlastního .</span><span class="sxs-lookup"><span data-stu-id="d251a-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="d251a-141">Jak můžete vidět, implementace vlastní ServiceHostFactory je velmi jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="d251a-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="d251a-142">Všechny vlastní logiky se nachází uvnitř implementace ServiceHost; factory vrátí instanci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d251a-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="d251a-143">Chcete-li použít vlastní továrnu s implementací služby, musíme do souboru .svc služby přidat další metadata.</span><span class="sxs-lookup"><span data-stu-id="d251a-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="d251a-144">Zde jsme přidali `Factory` další `@ServiceHost` atribut směrnice a předal název typu CLR naší vlastní továrny jako hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="d251a-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="d251a-145">Když služba IIS nebo WAS obdrží zprávu pro tuto službu, hostitelská infrastruktura WCF nejprve vytvoří instanci ServiceHostFactory a potom vytvoří instanci samotného hostitele služby voláním `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="d251a-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="d251a-146">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d251a-146">Running the sample</span></span>  
 <span data-ttu-id="d251a-147">I když tato ukázka poskytuje plně funkční implementaci klienta a služby, bod ukázky je ilustrovat, jak změnit chování služby za běhu pomocí vlastního hostitele., postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="d251a-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="d251a-148">Sledujte účinek vlastního hostitele</span><span class="sxs-lookup"><span data-stu-id="d251a-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="d251a-149">Otevřete soubor Web.config služby a všimněte si, že neexistuje žádná konfigurace, která by explicitně povoluje metadata pro službu.</span><span class="sxs-lookup"><span data-stu-id="d251a-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="d251a-150">Otevřete soubor .svc služby a @ServiceHost všimněte si, že jeho směrnice obsahuje atribut Factory, který určuje název vlastní ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="d251a-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="d251a-151">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d251a-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="d251a-152">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d251a-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d251a-153">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d251a-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="d251a-154">Po vytvoření řešení spusťte soubor Setup.bat a nastavte aplikaci ServiceModelSamples ve službě IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d251a-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="d251a-155">Adresář ServiceModelSamples by se nyní měl zobrazit jako aplikace služby IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="d251a-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="d251a-156">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d251a-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="d251a-157">Chcete-li odebrat aplikaci služby IIS 7.0, spusťte *soubor Cleanup.bat*.</span><span class="sxs-lookup"><span data-stu-id="d251a-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="d251a-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="d251a-158">See also</span></span>

- [<span data-ttu-id="d251a-159">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="d251a-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
