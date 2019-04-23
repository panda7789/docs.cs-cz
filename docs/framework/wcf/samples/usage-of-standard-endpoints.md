---
title: Používání standardních koncových bodů
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 4ef0714acad12db1414e34fbb476b4ae7d1d9fb2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977077"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="3e1f3-102">Používání standardních koncových bodů</span><span class="sxs-lookup"><span data-stu-id="3e1f3-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="3e1f3-103">Tato ukázka demonstruje použití standardních koncových bodů v konfiguračních souborech služby.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="3e1f3-104">Standardní koncový bod umožňuje uživatelům zjednodušit definic koncových bodů s použitím jedné vlastnosti k popisu adresa, vazba a kontrakt kombinaci s další vlastnosti přidružené k němu.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="3e1f3-105">Tato ukázka předvádí, jak definovat a implementovat vlastní standardní koncový bod a tom, jak definovat konkrétní vlastnosti v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="3e1f3-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3e1f3-106">Sample Details</span></span>

<span data-ttu-id="3e1f3-107">Koncové body služby je možné zadat tak poskytuje tři parametry: adresa, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="3e1f3-108">Další parametry, které může být zadán zahrnují konfiguraci chování, záhlaví, identifikátor URI příposlechu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="3e1f3-109">V některých případech, některé nebo všechny adresy vazby a kontrakty mají hodnoty, které nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="3e1f3-110">Z tohoto důvodu je možné použít standardní koncové body.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="3e1f3-111">Mezi příklady těchto koncových bodů patří koncové body metadat systému exchange a zjišťování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="3e1f3-112">Standardní koncové body také zlepšit použitelnost tím, že konfigurace koncových bodů služby bez nutnosti poskytnout informace, které pevné nebo vytvořte svoje vlastní standardní koncové body, například použitelnosti zadáním přiměřené sadu výchozí hodnoty a snížit tak množství podrobností konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="3e1f3-113">Tento příklad se skládá ze dvou projektů: služba, která definuje dva standardní koncové body a klienta, který komunikuje se službou.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="3e1f3-114">Způsob, jakým jsou definovány standardních koncových bodů služby v konfiguračním souboru se zobrazuje v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

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

<span data-ttu-id="3e1f3-115">První koncový bod definovaný pro službu je druhu `customEndpoint`, jejichž definice si můžete prohlédnout ve `<standardEndpoints>` oddílu, ve kterém vlastnost `property` přiřazena hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="3e1f3-116">To platí koncový bod přizpůsobit pomocí nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="3e1f3-117">Druhý koncový bod odpovídá koncový bod metadat, ve kterém jsou pevné hodnoty adresa, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="3e1f3-118">K definování elementu koncový bod standard, která je odvozena z třídy `StandardEndpointElement` musí být vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="3e1f3-119">V případě této ukázce `CustomEndpointElement` třída je definována, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

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

<span data-ttu-id="3e1f3-120">V `CreateServiceEndpoint` funkce, `CustomEndpoint` je vytvořen objekt.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="3e1f3-121">Jeho definice můžete vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3e1f3-121">Its definition is shown in the following example:</span></span>

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

 <span data-ttu-id="3e1f3-122">K provedení komunikace mezi klienta a služby, se vytvoří odkaz na službu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="3e1f3-123">Při ukázku je sestavení a spuštění, spustí služba a klient komunikuje s ním.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="3e1f3-124">Všimněte si, že by měl pokaždé, když se některé změny ve službě aktualizovat odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="3e1f3-125">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="3e1f3-125">To use this sample</span></span>

1. <span data-ttu-id="3e1f3-126">Pomocí sady Visual Studio 2012, otevřete soubor StandardEndpoints.sln.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="3e1f3-127">Povolte více projektů se spustí.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-127">Enable multiple projects to start up.</span></span>

    1.  <span data-ttu-id="3e1f3-128">V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení standardních koncových bodů a potom vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2.  <span data-ttu-id="3e1f3-129">V **společné vlastnosti**vyberte **spouštěný projekt**a potom klikněte na tlačítko **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3.  <span data-ttu-id="3e1f3-130">Přesunout projekt služby na začátku seznamu, s **akce** nastavena na **Start**.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4.  <span data-ttu-id="3e1f3-131">Přesunout projektu klienta po projekt služby také s **akce** nastavena na **Start**.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="3e1f3-132">Toto nastavení určuje, že klientský projekt je proveden po projekt služby.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-132">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="3e1f3-133">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="3e1f3-134">Pokud tyto kroky nefungují, ujistěte se, že vaše prostředí je správně nastavený, pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="3e1f3-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="3e1f3-135">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e1f3-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="3e1f3-136">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e1f3-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="3e1f3-137">Spusťte ukázku v jedné nebo více konfigurací počítače, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e1f3-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e1f3-138">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3e1f3-139">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3e1f3-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3e1f3-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3e1f3-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3e1f3-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
