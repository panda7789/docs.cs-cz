---
title: Konfigurace služeb WCF v kódu
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 8a1eeff76b02315143fb7b50ccc41aa18bb9eb0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225700"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="caa07-102">Konfigurace služeb WCF v kódu</span><span class="sxs-lookup"><span data-stu-id="caa07-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="caa07-103">Windows Communication Foundation (WCF) umožňuje vývojářům konfigurovat služeb pomocí konfiguračních souborů nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="caa07-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="caa07-104">Konfigurační soubory jsou užitečné, pokud je potřeba nakonfigurovat po nasazení služby.</span><span class="sxs-lookup"><span data-stu-id="caa07-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="caa07-105">Při použití konfiguračních souborů, odborníci na IT jenom je potřeba aktualizovat konfigurační soubor, žádné rekompilace je povinný.</span><span class="sxs-lookup"><span data-stu-id="caa07-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="caa07-106">Konfigurační soubory, ale lze komplexní a obtížné na správu.</span><span class="sxs-lookup"><span data-stu-id="caa07-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="caa07-107">Neexistuje žádná podpora pro ladění konfigurační soubory a konfigurační prvky, které je odkazováno dle názvy, které umožňuje vytváření konfigurační soubory obtížné a náchylné k chybě.</span><span class="sxs-lookup"><span data-stu-id="caa07-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="caa07-108">WCF můžete také nakonfigurovat v kódu.</span><span class="sxs-lookup"><span data-stu-id="caa07-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="caa07-109">V dřívějších verzích konfigurace služby WCF (4.0 a starší) v kódu bylo snadné v místním prostředí scénáře <xref:System.ServiceModel.ServiceHost> třída je možné nakonfigurovat koncové body a chování před voláním ServiceHost.Open povolená.</span><span class="sxs-lookup"><span data-stu-id="caa07-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="caa07-110">Ve scénářích hostovaná na webu, ale nemáte přímý přístup k <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="caa07-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="caa07-111">Konfigurace webového hostovaná služba byla potřeba k vytvoření `System.ServiceModel.ServiceHostFactory` vytvořený <xref:System.ServiceModel.Activation.ServiceHostFactory> a provedení všech potřebných konfigurace.</span><span class="sxs-lookup"><span data-stu-id="caa07-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="caa07-112">Počínaje .NET 4.5 WCF poskytuje snadný způsob, jak nakonfigurovat i v místním prostředí a web hostované služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="caa07-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="caa07-113">Metoda Configure</span><span class="sxs-lookup"><span data-stu-id="caa07-113">The Configure method</span></span>  
 <span data-ttu-id="caa07-114">Jednoduše definovat veřejné statické metody volá `Configure` s následující signaturou ve své třídě implementace služby:</span><span class="sxs-lookup"><span data-stu-id="caa07-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="caa07-115">Konfigurovat metoda přijímá <xref:System.ServiceModel.ServiceConfiguration> instanci, která umožňuje vývojářům přidat koncové body a chování.</span><span class="sxs-lookup"><span data-stu-id="caa07-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="caa07-116">Tato metoda je volána službou WCF před otevřením hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="caa07-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="caa07-117">Při definování, ignorují se jakékoli nastavení konfigurace služby zadaný v souboru app.config nebo web.config.</span><span class="sxs-lookup"><span data-stu-id="caa07-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="caa07-118">Následující fragment kódu ukazuje, jak definovat `Configure` metoda a přidat koncový bod služby, chování koncového bodu a chování služby:</span><span class="sxs-lookup"><span data-stu-id="caa07-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
  
 <span data-ttu-id="caa07-119">Pokud chcete povolit protokol, jako je například https pro službu, můžete buď explicitně přidat koncový bod, který používá protokol nebo můžete automaticky přidat koncové body voláním ServiceConfiguration.EnableProtocol(Binding), který přidá koncový bod pro každou základní adresu kompatibilní s protokolem a každá služba kontrakt definovaný.</span><span class="sxs-lookup"><span data-stu-id="caa07-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="caa07-120">Následující kód ukazuje, jak použít metodu ServiceConfiguration.EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="caa07-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="caa07-121">Nastavení <`protocolMappings`> části se použijí pouze, pokud žádné koncové body aplikace se přidají do <xref:System.ServiceModel.ServiceConfiguration> prostřednictvím kódu programu. Volitelně můžete načíst konfiguraci služby z konfiguračního souboru aplikace výchozí voláním <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a pak změňte nastavení.</span><span class="sxs-lookup"><span data-stu-id="caa07-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="caa07-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Tříd také umožňuje načtení konfigurace z centralizovaného konfigurace.</span><span class="sxs-lookup"><span data-stu-id="caa07-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="caa07-123">Následující kód ukazuje, jak implementovat toto:</span><span class="sxs-lookup"><span data-stu-id="caa07-123">The following code illustrates how to implement this:</span></span>  
  
```  
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
>  <span data-ttu-id="caa07-124">Všimněte si, že <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Nastavení v rámci <`service`> značky <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="caa07-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="caa07-125">Koncepčně <`host`> je o konfiguraci hostitele, není konfigurace služby a it získá načtené před provedením metody konfigurace.</span><span class="sxs-lookup"><span data-stu-id="caa07-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa07-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caa07-126">See also</span></span>

- [<span data-ttu-id="caa07-127">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="caa07-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [<span data-ttu-id="caa07-128">Konfigurace chování klientů</span><span class="sxs-lookup"><span data-stu-id="caa07-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="caa07-129">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="caa07-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="caa07-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="caa07-130">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)
- [<span data-ttu-id="caa07-131">Aktivace založená na konfiguraci v IIS a WAS</span><span class="sxs-lookup"><span data-stu-id="caa07-131">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="caa07-132">Konfigurace a podpora metadat</span><span class="sxs-lookup"><span data-stu-id="caa07-132">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="caa07-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="caa07-133">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="caa07-134">Postupy: Určení vazby služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="caa07-134">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="caa07-135">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="caa07-135">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="caa07-136">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="caa07-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="caa07-137">Postupy: Určení klientské vazby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="caa07-137">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
