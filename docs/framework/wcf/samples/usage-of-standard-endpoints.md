---
title: Používání standardních koncových bodů
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 2b210bfe683669aeebf54a1701f07d492e6abdb4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715349"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="a185b-102">Používání standardních koncových bodů</span><span class="sxs-lookup"><span data-stu-id="a185b-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="a185b-103">Tato ukázka předvádí, jak používat standardní koncové body v konfiguračních souborech služby.</span><span class="sxs-lookup"><span data-stu-id="a185b-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="a185b-104">Standardní koncový bod umožňuje uživateli zjednodušit definice koncových bodů pomocí jedné vlastnosti pro popis kombinace adresy, vazby a kontraktu s dalšími vlastnostmi, které jsou k ní přidružené.</span><span class="sxs-lookup"><span data-stu-id="a185b-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="a185b-105">Tato ukázka předvádí, jak definovat a implementovat vlastní koncový bod Standard a jak definovat konkrétní vlastnosti v koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="a185b-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="a185b-106">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="a185b-106">Sample Details</span></span>

<span data-ttu-id="a185b-107">Koncové body služby je možné zadat zadáním tří parametrů: adresa, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a185b-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="a185b-108">Mezi další parametry, které lze zadat, patří konfigurace chování, hlavičky, identifikátor URI naslouchání atd.</span><span class="sxs-lookup"><span data-stu-id="a185b-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="a185b-109">V některých případech mají některé nebo všechny adresy, vazby a kontrakty hodnoty, které se nedají změnit.</span><span class="sxs-lookup"><span data-stu-id="a185b-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="a185b-110">Z tohoto důvodu je možné použít standardní koncové body.</span><span class="sxs-lookup"><span data-stu-id="a185b-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="a185b-111">Mezi příklady takových koncových bodů patří koncové body výměny metadat a koncové body zjišťování.</span><span class="sxs-lookup"><span data-stu-id="a185b-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="a185b-112">Standardní koncové body také zlepšují použitelnost tím, že umožňují konfiguraci koncových bodů služby bez nutnosti poskytovat informace o pevné povaze nebo vytvářet vlastní standardní koncové body, například pro zlepšení použitelnosti poskytnutím přiměřené sady výchozích hodnoty, čímž se sníží úroveň podrobností konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="a185b-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="a185b-113">Tato ukázka se skládá ze dvou projektů: služby, která definuje dva standardní koncové body a klienta, který komunikuje se službou.</span><span class="sxs-lookup"><span data-stu-id="a185b-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="a185b-114">Způsob definování standardních koncových bodů pro službu v konfiguračním souboru je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a185b-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="a185b-115">Prvním koncovým bodem definovaným pro službu je `customEndpoint`, jehož definici lze zobrazit v části `<standardEndpoints>`, ve které je `property` vlastnosti přiřazena hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="a185b-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="a185b-116">Jedná se o případ přizpůsobený koncovému bodu s novou vlastností.</span><span class="sxs-lookup"><span data-stu-id="a185b-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="a185b-117">Druhý koncový bod odpovídá koncovému bodu metadat, ve kterém jsou opraveny hodnoty adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a185b-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="a185b-118">Pro definování elementu standardního koncového bodu musí být vytvořena třída, která je odvozena od `StandardEndpointElement`.</span><span class="sxs-lookup"><span data-stu-id="a185b-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="a185b-119">V případě této ukázky byla definována třída `CustomEndpointElement`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a185b-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

<span data-ttu-id="a185b-120">Ve funkci `CreateServiceEndpoint` je vytvořen objekt `CustomEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="a185b-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="a185b-121">Jeho definice je uvedena v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a185b-121">Its definition is shown in the following example:</span></span>

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 <span data-ttu-id="a185b-122">K provedení komunikace mezi službou a klientem se v klientovi vytvoří odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="a185b-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="a185b-123">Při sestavení a spuštění ukázky se služba spustí a klient s ním komunikuje.</span><span class="sxs-lookup"><span data-stu-id="a185b-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="a185b-124">Všimněte si, že odkaz na službu by se měl aktualizovat při každé změně ve službě.</span><span class="sxs-lookup"><span data-stu-id="a185b-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="a185b-125">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="a185b-125">To use this sample</span></span>

1. <span data-ttu-id="a185b-126">Pomocí sady Visual Studio 2012 otevřete soubor oddílu StandardEndpoints. sln.</span><span class="sxs-lookup"><span data-stu-id="a185b-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="a185b-127">Povolit spuštění více projektů.</span><span class="sxs-lookup"><span data-stu-id="a185b-127">Enable multiple projects to start up.</span></span>

    1. <span data-ttu-id="a185b-128">V **Průzkumník řešení**klikněte pravým tlačítkem myši na standardní řešení koncových bodů a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a185b-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2. <span data-ttu-id="a185b-129">V nabídce **běžné vlastnosti**vyberte možnost **projekt po spuštění**a pak klikněte na **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="a185b-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3. <span data-ttu-id="a185b-130">Přesuňte projekt služby na začátek seznamu a **akci** nastavte na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="a185b-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4. <span data-ttu-id="a185b-131">Přesuňte klientský projekt po projektu služby a **akci** nastavte na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="a185b-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="a185b-132">To určuje, že projekt klienta je proveden po projektu služby.</span><span class="sxs-lookup"><span data-stu-id="a185b-132">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="a185b-133">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="a185b-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="a185b-134">Pokud tyto kroky nefungují, ujistěte se, že máte správně nastavené prostředí, a to pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="a185b-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="a185b-135">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a185b-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="a185b-136">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a185b-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="a185b-137">Chcete-li spustit ukázku v jedné nebo více konfiguracích počítačů, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a185b-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a185b-138">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="a185b-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a185b-139">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a185b-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a185b-140">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="a185b-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a185b-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a185b-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
