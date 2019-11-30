---
title: Konfigurace služeb WCF v kódu
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 5d05fe5f70f4e2b1490c728cc019430cd94ff925
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569508"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="7279f-102">Konfigurace služeb WCF v kódu</span><span class="sxs-lookup"><span data-stu-id="7279f-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="7279f-103">Windows Communication Foundation (WCF) umožňuje vývojářům nakonfigurovat služby pomocí konfiguračních souborů nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="7279f-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="7279f-104">Konfigurační soubory jsou užitečné, když po nasazení potřebujete nakonfigurovat službu.</span><span class="sxs-lookup"><span data-stu-id="7279f-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="7279f-105">Při použití konfiguračních souborů potřebuje IT specialista aktualizovat pouze konfigurační soubor, není nutné znovu zkompilována.</span><span class="sxs-lookup"><span data-stu-id="7279f-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="7279f-106">Konfigurační soubory ale mohou být složité a obtížné udržovat.</span><span class="sxs-lookup"><span data-stu-id="7279f-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="7279f-107">Neexistuje žádná podpora pro ladění konfiguračních souborů a konfigurační prvky jsou odkazovány pomocí názvů, které usnadňují a obtíže při vytváření konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="7279f-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="7279f-108">WCF také umožňuje nakonfigurovat služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="7279f-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="7279f-109">V dřívějších verzích WCF (4,0 a starší) konfigurace služeb v kódu byla v rámci scénářů s vlastním hostováním velmi snadná, <xref:System.ServiceModel.ServiceHost> třídy vám umožňují nakonfigurovat koncové body a chování před voláním třídy ServiceHost. Open.</span><span class="sxs-lookup"><span data-stu-id="7279f-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="7279f-110">Ve scénářích, kde se nachází web, ale nemáte přímý přístup k třídě <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7279f-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="7279f-111">Pro konfiguraci webové hostované služby jste museli vytvořit `System.ServiceModel.ServiceHostFactory`, která vytvořila <xref:System.ServiceModel.Activation.ServiceHostFactory> a provedla všechny potřebné konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7279f-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="7279f-112">Počínaje verzí .NET 4,5 nabízí WCF snazší způsob, jak v kódu nakonfigurovat služby hostované v místním prostředí i na webu.</span><span class="sxs-lookup"><span data-stu-id="7279f-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="7279f-113">Metoda Configure</span><span class="sxs-lookup"><span data-stu-id="7279f-113">The Configure method</span></span>  
 <span data-ttu-id="7279f-114">Jednoduše definujte veřejnou statickou metodu s názvem `Configure` s následující signaturou ve třídě implementace služby:</span><span class="sxs-lookup"><span data-stu-id="7279f-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="7279f-115">Metoda Configure přebírá <xref:System.ServiceModel.ServiceConfiguration> instanci, která vývojářům umožňuje přidat koncové body a chování.</span><span class="sxs-lookup"><span data-stu-id="7279f-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="7279f-116">Tato metoda je volána službou WCF před otevřením hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="7279f-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="7279f-117">Při definování budou všechna nastavení konfigurace služby zadaná v souboru App. config nebo Web. config ignorována.</span><span class="sxs-lookup"><span data-stu-id="7279f-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="7279f-118">Následující fragment kódu ukazuje, jak definovat metodu `Configure` a přidat koncový bod služby, chování koncového bodu a chování služby:</span><span class="sxs-lookup"><span data-stu-id="7279f-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="7279f-119">Pokud chcete povolit protokol, jako je například https pro službu, můžete buď explicitně přidat koncový bod, který používá protokol, nebo můžete automaticky přidat koncové body voláním ServiceConfiguration. EnableProtocol (Binding), který přidá koncový bod pro každou základní adresu. kompatibilní s protokolem a všemi definovanými kontrakty služby.</span><span class="sxs-lookup"><span data-stu-id="7279f-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="7279f-120">Následující kód ilustruje, jak použít metodu ServiceConfiguration. EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="7279f-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpsBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="7279f-121">Nastavení v části <`protocolMappings`> se použijí jenom v případě, že se do <xref:System.ServiceModel.ServiceConfiguration>ho programově nepřidaly žádné koncové body aplikace. Můžete volitelně načíst konfiguraci služby z výchozího konfiguračního souboru aplikace voláním <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a potom změnit nastavení.</span><span class="sxs-lookup"><span data-stu-id="7279f-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="7279f-122">Třída <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> také umožňuje načíst konfiguraci z centralizované konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7279f-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="7279f-123">Následující kód ilustruje, jak implementovat toto:</span><span class="sxs-lookup"><span data-stu-id="7279f-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="7279f-124">Všimněte si, že <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> nastavení v <`service`> <`system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="7279f-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="7279f-125">Konceptuální <`host`> se týká konfigurace hostitele, nikoli konfigurace služby a načítá se před spuštěním metody konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7279f-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7279f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7279f-126">See also</span></span>

- [<span data-ttu-id="7279f-127">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="7279f-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="7279f-128">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="7279f-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="7279f-129">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="7279f-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="7279f-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7279f-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="7279f-131">Aktivace založená na konfiguraci v IIS a WAS</span><span class="sxs-lookup"><span data-stu-id="7279f-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="7279f-132">Konfigurace a podpora metadat</span><span class="sxs-lookup"><span data-stu-id="7279f-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="7279f-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7279f-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="7279f-134">Postupy: Určení vazby služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7279f-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="7279f-135">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7279f-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="7279f-136">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7279f-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="7279f-137">Postupy: Určení vazby klienta v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7279f-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
