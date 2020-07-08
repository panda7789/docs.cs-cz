---
title: Vlastní hostitel služby
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 8302c3c829883da954d200526ca641eb4c169f98
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052023"
---
# <a name="custom-service-host"></a><span data-ttu-id="a8334-102">Vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="a8334-102">Custom Service Host</span></span>
<span data-ttu-id="a8334-103">Tato ukázka předvádí, jak použít vlastní derivát <xref:System.ServiceModel.ServiceHost> třídy pro změnu chování služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="a8334-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="a8334-104">Tento přístup poskytuje opakovaně použitelnou alternativu ke konfiguraci velkého počtu služeb běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a8334-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="a8334-105">Ukázka také ukazuje, jak použít <xref:System.ServiceModel.Activation.ServiceHostFactory> třídu pro použití vlastní třídy ServiceHost ve službě Internetová informační služba (IIS) nebo v hostitelském prostředí služby WAS (Windows Process Activation Service).</span><span class="sxs-lookup"><span data-stu-id="a8334-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8334-106">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="a8334-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8334-107">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a8334-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a8334-108">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="a8334-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8334-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a8334-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="a8334-110">O scénáři</span><span class="sxs-lookup"><span data-stu-id="a8334-110">About the scenario</span></span>
 <span data-ttu-id="a8334-111">Aby nedocházelo k neúmyslnému zveřejnění potenciálně citlivých metadat služby, služba výchozí konfigurace služby Windows Communication Foundation (WCF) zakáže publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="a8334-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="a8334-112">Ve výchozím nastavení je toto chování zabezpečené, ale také znamená, že nemůžete použít nástroj pro import metadat (například Svcutil.exe) k vygenerování kódu klienta, který je vyžadován pro volání služby, pokud není chování publikování metadat služby explicitně povoleno v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a8334-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service's metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="a8334-113">Povolení publikování metadat pro velký počet služeb zahrnuje přidání stejných konfiguračních prvků do každé jednotlivé služby, což má za následek velké množství informací o konfiguraci, které jsou v podstatě stejné.</span><span class="sxs-lookup"><span data-stu-id="a8334-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="a8334-114">Jako alternativu ke konfiguraci jednotlivých služeb je možné napsat imperativní kód, který umožňuje publikování metadat jednou a potom tento kód znovu použít napříč několika různými službami.</span><span class="sxs-lookup"><span data-stu-id="a8334-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="a8334-115">To je dosaženo vytvořením nové třídy, která je odvozena z <xref:System.ServiceModel.ServiceHost> a Přepisuje `ApplyConfiguration` metodu () pro imperativní přidání chování publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="a8334-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8334-116">Pro přehlednost Tato ukázka ukazuje, jak vytvořit nezabezpečený koncový bod publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="a8334-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="a8334-117">Tyto koncové body jsou možná dostupné anonymním neověřeným příjemcům a před nasazením těchto koncových bodů je nutné zajistit, aby bylo zajištěno, že bude jejich veřejněné zveřejnění metadat služby vhodné.</span><span class="sxs-lookup"><span data-stu-id="a8334-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service's metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="a8334-118">Implementace vlastní třídy ServiceHost</span><span class="sxs-lookup"><span data-stu-id="a8334-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="a8334-119"><xref:System.ServiceModel.ServiceHost>Třída zveřejňuje několik užitečných virtuálních metod, které mohou dědit pro změnu chování služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="a8334-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="a8334-120">Například `ApplyConfiguration` metoda () čte informace o konfiguraci služby z úložiště konfigurace a mění hostitele <xref:System.ServiceModel.Description.ServiceDescription> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="a8334-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="a8334-121">Výchozí implementace čte konfiguraci z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8334-121">The default implementation reads configuration from the application's configuration file.</span></span> <span data-ttu-id="a8334-122">Vlastní implementace mohou přepsat `ApplyConfiguration` () pro další změnu <xref:System.ServiceModel.Description.ServiceDescription> pomocí imperativního kódu nebo dokonce nahradit výchozí úložiště konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a8334-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="a8334-123">Například pro čtení konfigurace koncového bodu služby z databáze místo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8334-123">For example, to read a service's endpoint configuration from a database instead of the application's configuration file.</span></span>  
  
 <span data-ttu-id="a8334-124">V této ukázce chceme vytvořit vlastní třídu ServiceHost, která přidá rozhraní ServiceMetadataBehavior (umožňující publikování metadat) i v případě, že toto chování není explicitně přidáno do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="a8334-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior (which enables metadata publishing) even if this behavior is not explicitly added in the service's configuration file.</span></span> <span data-ttu-id="a8334-125">K tomu je potřeba vytvořit novou třídu, která dědí z <xref:System.ServiceModel.ServiceHost> a Overrides `ApplyConfiguration` ().</span><span class="sxs-lookup"><span data-stu-id="a8334-125">To accomplish this, create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
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
  
 <span data-ttu-id="a8334-126">Vzhledem k tomu, že nechcete ignorovat žádnou konfiguraci, která byla k dispozici v konfiguračním souboru aplikace, první věc `ApplyConfiguration` () je volání základní implementace.</span><span class="sxs-lookup"><span data-stu-id="a8334-126">Because we do not want to ignore any configuration that has been provided in the application's configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="a8334-127">Po dokončení této metody můžeme imperativně přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> k popisu pomocí následujícího imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a8334-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
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
  
 <span data-ttu-id="a8334-128">Poslední věc, kterou je `ApplyConfiguration` třeba přepsat, je nutné přidat výchozí koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="a8334-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="a8334-129">Podle konvence je pro každý identifikátor URI v kolekci adres BaseAddresses hostitele služby vytvořen jeden koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="a8334-129">By convention, one metadata endpoint is created for each URI in the service host's BaseAddresses collection.</span></span>  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="a8334-130">Použití vlastní ServiceHost v samoobslužném hostování</span><span class="sxs-lookup"><span data-stu-id="a8334-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="a8334-131">Teď, když jsme dokončili naši vlastní implementaci ServiceHost, ji můžeme použít k přidání chování publikování metadat do jakékoli služby hostováním této služby uvnitř instance našeho `SelfDescribingServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="a8334-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="a8334-132">Následující kód ukazuje, jak ho použít ve scénáři samostatného hostitele.</span><span class="sxs-lookup"><span data-stu-id="a8334-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="a8334-133">Náš vlastní hostitel pořád čte konfiguraci koncového bodu služby z konfiguračního souboru aplikace, jako kdyby jsme používali výchozí <xref:System.ServiceModel.ServiceHost> třídu pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="a8334-133">Our custom host still reads the service's endpoint configuration from the application's configuration file, as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="a8334-134">Vzhledem k tomu, že jsme přidali logiku pro povolení publikování metadat v rámci našeho vlastního hostitele, už nemusíte explicitně povolit chování publikování metadat v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a8334-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="a8334-135">Tento přístup má odlišnou výhodu při vytváření aplikace, která obsahuje několik služeb a chcete povolit publikování metadat na každém z nich, aniž byste museli psát stejné konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="a8334-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="a8334-136">Použití vlastního hostitele ServiceHost ve službě IIS nebo WAS</span><span class="sxs-lookup"><span data-stu-id="a8334-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="a8334-137">Použití vlastního hostitele služby ve scénářích pro vlastní hostitele je jednoduché, protože se jedná o kód vaší aplikace, který je nakonec zodpovědný za vytvoření a otevření instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="a8334-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="a8334-138">Ve službě IIS nebo se hostující prostředí ale infrastruktura WCF dynamicky vytvoří instanci hostitele vaší služby v reakci na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a8334-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service's host in response to incoming messages.</span></span> <span data-ttu-id="a8334-139">Vlastní hostitelé služby můžete také použít v tomto hostitelském prostředí, ale vyžadují nějaký další kód ve formě ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="a8334-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="a8334-140">Následující kód ukazuje derivaci <xref:System.ServiceModel.Activation.ServiceHostFactory> , který vrací instance našeho vlastního `SelfDescribingServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="a8334-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
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
  
 <span data-ttu-id="a8334-141">Jak vidíte, implementace vlastního ServiceHostFactory je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="a8334-141">As you can see, implementing a custom ServiceHostFactory is straightforward.</span></span> <span data-ttu-id="a8334-142">Všechny vlastní logiky se nacházejí v implementaci ServiceHost. objekt pro vytváření vrací instanci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="a8334-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="a8334-143">Aby bylo možné používat vlastní továrnu s implementací služby, je nutné do souboru. svc služby přidat další metadata.</span><span class="sxs-lookup"><span data-stu-id="a8334-143">To use a custom factory with a service implementation, we must add some additional metadata to the service's .svc file.</span></span>  
  
```aspx-csharp
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="a8334-144">Do direktivy jsme přidali dodatečný `Factory` atribut `@ServiceHost` a jako hodnotu atributu jste předali název typu CLR naší vlastní továrny.</span><span class="sxs-lookup"><span data-stu-id="a8334-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute's value.</span></span> <span data-ttu-id="a8334-145">Když služba IIS nebo obdržela zprávu pro tuto službu, hostitelská infrastruktura WCF nejprve vytvoří instanci třídy ServiceHostFactory a potom sama inicializuje hostitele služby voláním `ServiceHostFactory.CreateServiceHost()` .</span><span class="sxs-lookup"><span data-stu-id="a8334-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiates the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="a8334-146">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a8334-146">Running the sample</span></span>  
 <span data-ttu-id="a8334-147">I když tato ukázka poskytuje plně funkční implementaci klienta a služby, bod ukázky je Ukázat, jak změnit chování služby za běhu pomocí vlastního hostitele. proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="a8334-147">Although this sample does provide a fully functional client and service implementation, the point of the sample is to illustrate how to alter a service's run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="a8334-148">Sledování účinku vlastního hostitele</span><span class="sxs-lookup"><span data-stu-id="a8334-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="a8334-149">Otevřete soubor Web.config služby a sledujte, že není k dispozici žádná konfigurace, která by explicitně povolila metadata služby.</span><span class="sxs-lookup"><span data-stu-id="a8334-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="a8334-150">Otevřete soubor služby. svc a sledujte, že jeho @ServiceHost Direktiva obsahuje atribut Factory, který určuje název vlastní ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="a8334-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="a8334-151">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a8334-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="a8334-152">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8334-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a8334-153">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8334-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="a8334-154">Po vytvoření řešení spusťte Setup.bat a nastavte aplikaci ServiceModelSamples ve službě IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a8334-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="a8334-155">Adresář ServiceModelSamples by se teď měl zobrazit jako aplikace IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a8334-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="a8334-156">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8334-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="a8334-157">Pokud chcete odebrat aplikaci IIS 7,0, spusťte *Cleanup.bat*.</span><span class="sxs-lookup"><span data-stu-id="a8334-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8334-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8334-158">See also</span></span>

- [<span data-ttu-id="a8334-159">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="a8334-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
