---
title: "Konfigurace služeb WCF v kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 202214a6c9279eb61db560321a8f36943ce5d635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="6fb7d-102">Konfigurace služeb WCF v kódu</span><span class="sxs-lookup"><span data-stu-id="6fb7d-102">Configuring WCF Services in Code</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="6fb7d-103">umožňuje vývojářům konfigurovat služeb pomocí konfiguračních souborů nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-103"> allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="6fb7d-104">Konfigurační soubory jsou užitečné, když je potřeba nakonfigurovat po nasazení služby.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="6fb7d-105">Při použití konfigurační soubory, odborník v oblasti IT pouze musí aktualizovat konfigurační soubor, není třeba žádné opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="6fb7d-106">Konfigurační soubory, však může být složité a obtížné.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="6fb7d-107">Neexistuje žádná podpora pro ladění konfigurační soubory a konfigurace – elementy odkazují názvy, které umožňuje vytváření konfigurační soubory k chybám a obtížná.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="6fb7d-108">také umožňuje konfigurovat služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-108"> also allows you to configure services in code.</span></span> <span data-ttu-id="6fb7d-109">V dřívějších verzích [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 a starší) konfigurace služby v kódu se snadno ve vlastním hostováním scénářů <xref:System.ServiceModel.ServiceHost> třída povolena, můžete nakonfigurovat koncové body a chování před volání ServiceHost.Open.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-109">In earlier versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="6fb7d-110">Ve scénářích hostovaná na webu, ale nemáte přímý přístup k <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="6fb7d-111">Konfigurace webové hostované služby, bylo potřeba vytvořit `System.ServiceModel.ServiceHostFactory` vytvořené <xref:System.ServiceModel.Activation.ServiceHostFactory> a provést všechny potřebné konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="6fb7d-112">Od verze rozhraní .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] poskytuje snadný způsob, jak nakonfigurovat i samoobslužně hostované a webové hostované služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-112">Starting with .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="6fb7d-113">Metoda konfigurace</span><span class="sxs-lookup"><span data-stu-id="6fb7d-113">The Configure method</span></span>  
 <span data-ttu-id="6fb7d-114">Jednoduše zadejte veřejnou statickou metodu s názvem `Configure` následující podpisem v třídě implementace služby:</span><span class="sxs-lookup"><span data-stu-id="6fb7d-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="6fb7d-115">Provede metodu konfigurace <xref:System.ServiceModel.ServiceConfiguration> instanci, která umožňuje vývojáři přidat koncové body a chování.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="6fb7d-116">Tato metoda je volána [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] před otevřením hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-116">This method is called by [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] before the service host is opened.</span></span> <span data-ttu-id="6fb7d-117">Pokud je definována, nastavení konfigurace služby, který je zadaný v souboru app.config nebo web.config, bude ignorována.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="6fb7d-118">Následující fragment kódu ukazuje, jak definovat `Configure` metoda a přidání koncového bodu služby, chování koncového bodu a chování služby:</span><span class="sxs-lookup"><span data-stu-id="6fb7d-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
            return string.Format("You entered: {0}", value);  
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
  
 <span data-ttu-id="6fb7d-119">Pokud chcete povolit protokol, jako je například https pro službu, můžete buď explicitně přidat koncový bod, který používá protokol nebo můžete automaticky přidat koncové body voláním ServiceConfiguration.EnableProtocol(Binding), který přidá koncový bod pro každou základní adresu kompatibilní s protokolem a každý kontrakt služby definované.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="6fb7d-120">Následující kód ukazuje, jak lze pomocí této metody ServiceConfiguration.EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="6fb7d-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
  
 <span data-ttu-id="6fb7d-121">Nastavení v <`protocolMappings`> části jsou použít jen v případě žádné koncové body aplikace jsou přidány do <xref:System.ServiceModel.ServiceConfiguration> prostřednictvím kódu programu. Volitelně můžete načíst konfiguraci služby z konfiguračního souboru aplikace výchozí voláním <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a poté změňte nastavení.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="6fb7d-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Třída taky umožňuje načíst konfiguraci z centralizované konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="6fb7d-123">Následující kód ukazuje, jak implementovat toto:</span><span class="sxs-lookup"><span data-stu-id="6fb7d-123">The following code illustrates how to implement this:</span></span>  
  
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
>  <span data-ttu-id="6fb7d-124">Všimněte si, že <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Nastavení v rámci <`service`> značky <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="6fb7d-125">Koncepčně <`host`> je o konfigurace hostitele, není konfigurace služby a získá načíst před spuštěním metody konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb7d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fb7d-126">See Also</span></span>  
 [<span data-ttu-id="6fb7d-127">Konfigurace služeb pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="6fb7d-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="6fb7d-128">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="6fb7d-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="6fb7d-129">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="6fb7d-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="6fb7d-130">Aktivace na základě konfigurace</span><span class="sxs-lookup"><span data-stu-id="6fb7d-130">Configuration-Based Activation</span></span>](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [<span data-ttu-id="6fb7d-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6fb7d-131">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [<span data-ttu-id="6fb7d-132">Aktivace založená na konfiguraci v IIS a WAS</span><span class="sxs-lookup"><span data-stu-id="6fb7d-132">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [<span data-ttu-id="6fb7d-133">Konfigurace a podpora metadat</span><span class="sxs-lookup"><span data-stu-id="6fb7d-133">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [<span data-ttu-id="6fb7d-134">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6fb7d-134">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [<span data-ttu-id="6fb7d-135">Postupy: Určení vazby služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="6fb7d-135">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="6fb7d-136">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="6fb7d-136">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="6fb7d-137">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="6fb7d-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="6fb7d-138">Postupy: Určení vazby klienta v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="6fb7d-138">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
