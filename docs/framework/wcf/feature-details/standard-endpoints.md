---
title: Standardní koncové body
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 880601664d7602e279c5d022fa37c44914a58772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184408"
---
# <a name="standard-endpoints"></a><span data-ttu-id="e41d2-102">Standardní koncové body</span><span class="sxs-lookup"><span data-stu-id="e41d2-102">Standard Endpoints</span></span>
<span data-ttu-id="e41d2-103">Koncové body jsou definovány zadáním adresy, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="e41d2-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="e41d2-104">Mezi další parametry, které mohou být nastaveny v koncovém bodě, patří konfigurace chování, záhlaví a naslouchání identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="e41d2-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="e41d2-105">U určitých typů koncových bodů se tyto hodnoty nemění.</span><span class="sxs-lookup"><span data-stu-id="e41d2-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="e41d2-106">Například koncové body výměny metadat <xref:System.ServiceModel.Description.IMetadataExchange> vždy používají smlouvy.</span><span class="sxs-lookup"><span data-stu-id="e41d2-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="e41d2-107">Jiné koncové body, <xref:System.ServiceModel.Description.WebHttpEndpoint> například vždy vyžadují zadané chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="e41d2-108">Použitelnost koncového bodu lze zlepšit tím, že koncové body s výchozí hodnoty pro běžně používané vlastnosti koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="e41d2-109">Standardní koncové body umožňují vývojáři definovat koncový bod, který má výchozí hodnoty nebo kde se nemění vlastnosti jednoho nebo více koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e41d2-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="e41d2-110">Tyto koncové body umožňují použít takový koncový bod bez nutnosti zadat informace statické povahy.</span><span class="sxs-lookup"><span data-stu-id="e41d2-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="e41d2-111">Standardní koncové body lze použít pro koncové body infrastruktury a aplikace.</span><span class="sxs-lookup"><span data-stu-id="e41d2-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="e41d2-112">Koncové body infrastruktury</span><span class="sxs-lookup"><span data-stu-id="e41d2-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="e41d2-113">Služba může vystavit koncové body s některými vlastnostmi, které nejsou explicitně implementovány autorem služby.</span><span class="sxs-lookup"><span data-stu-id="e41d2-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="e41d2-114">Například koncový bod výměny metadat <xref:System.ServiceModel.Description.IMetadataExchange> zveřejňuje smlouvy, ale jako autor služby neimplementujete toto rozhraní, je implementována WCF.</span><span class="sxs-lookup"><span data-stu-id="e41d2-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="e41d2-115">Tyto koncové body infrastruktury mají výchozí hodnoty pro jednu nebo více vlastností koncového bodu, z nichž některé mohou být neměnné.</span><span class="sxs-lookup"><span data-stu-id="e41d2-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="e41d2-116">Vlastnost <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> koncového bodu výměny metadat <xref:System.ServiceModel.Description.IMetadataExchange>musí být , zatímco jiné vlastnosti, jako je vazba může být poskytnuta vývojář.</span><span class="sxs-lookup"><span data-stu-id="e41d2-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="e41d2-117">Koncové body infrastruktury jsou <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> identifikovány nastavením vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="e41d2-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="e41d2-118">Koncové body aplikace</span><span class="sxs-lookup"><span data-stu-id="e41d2-118">Application Endpoints</span></span>  
 <span data-ttu-id="e41d2-119">Vývojáři aplikací můžete definovat své vlastní standardní koncové body, které určují výchozí hodnoty pro adresu, vazbu nebo smlouvu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="e41d2-120">Standardní koncový bod definujete odvozením třídy z <xref:System.ServiceModel.Description.ServiceEndpoint> a nastavením příslušných vlastností koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="e41d2-121">Můžete zadat výchozí hodnoty pro vlastnosti, které lze změnit.</span><span class="sxs-lookup"><span data-stu-id="e41d2-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="e41d2-122">Některé další vlastnosti budou mít statické hodnoty, které se nemohou změnit.</span><span class="sxs-lookup"><span data-stu-id="e41d2-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="e41d2-123">Následující příklad ukazuje, jak implementovat standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e41d2-123">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  

    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="e41d2-124">Chcete-li použít vlastní koncový bod definovaný uživatelem v <xref:System.ServiceModel.Configuration.StandardEndpointElement>konfiguračním <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>souboru, musíte odvodit třídu z , odvodit třídu z aplikace a zaregistrovat nový standardní koncový bod v části rozšíření v souboru app.config nebo machine.config.  Poskytuje <xref:System.ServiceModel.Configuration.StandardEndpointElement> podporu konfigurace pro standardní koncový bod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="e41d2-125">Poskytuje <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> typ zálohování pro kolekci, která `standardEndpoints` se zobrazí pod <> části v konfiguraci pro standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e41d2-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="e41d2-126">Následující příklad ukazuje, jak implementovat tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="e41d2-127">Následující příklad ukazuje, jak zaregistrovat standardní koncový bod v části rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e41d2-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="e41d2-128">Konfigurace standardního koncového bodu</span><span class="sxs-lookup"><span data-stu-id="e41d2-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="e41d2-129">Standardní koncové body lze přidat v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e41d2-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="e41d2-130">Chcete-li přidat standardní koncový bod v kódu, jednoduše vytvořte instanci příslušného standardního typu koncového bodu a přidejte jej do hostitele služby, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e41d2-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="e41d2-131">Chcete-li přidat standardní koncový bod `endpoint` v konfiguraci, `service` přidejte <> prvek `standardEndpoints` do <> elementu a všechna potřebná nastavení konfigurace v elementu <>.</span><span class="sxs-lookup"><span data-stu-id="e41d2-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="e41d2-132">Následující příklad <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>ukazuje, jak přidat jeden ze standardních [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]koncových bodů, které jsou dodávány s .</span><span class="sxs-lookup"><span data-stu-id="e41d2-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="e41d2-133">Typ standardního koncového bodu je určen pomocí `endpoint` atributu kind v elementu <>.</span><span class="sxs-lookup"><span data-stu-id="e41d2-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="e41d2-134">Koncový bod je konfigurován `standardEndpoints` v rámci <> elementu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="e41d2-135">Ve výše uvedeném <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> příkladu je přidán a nakonfigurován koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e41d2-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="e41d2-136">Prvek `udpDiscoveryEndpoint` <> obsahuje `standardEndpoint` <>, která nastaví <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> vlastnost <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="e41d2-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="e41d2-137">Standardní koncové body dodávané s rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e41d2-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="e41d2-138">V následující tabulce jsou uvedeny [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]standardní koncové body dodávané s .</span><span class="sxs-lookup"><span data-stu-id="e41d2-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="e41d2-139">Standardní koncový bod, který se používá k odhalení metadat služby.</span><span class="sxs-lookup"><span data-stu-id="e41d2-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="e41d2-140">Standardní koncový bod, který používá služby k odesílání zpráv oznámení.</span><span class="sxs-lookup"><span data-stu-id="e41d2-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="e41d2-141">Standardní koncový bod, který používá služby k odesílání zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e41d2-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="e41d2-142">Standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes vazbu vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="e41d2-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="e41d2-143">Standardní koncový bod, který používá služby k odesílání zpráv oznámení prostřednictvím vazby UDP.</span><span class="sxs-lookup"><span data-stu-id="e41d2-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="e41d2-144">Standardní koncový bod, který používá WS-Discovery dynamicky najít adresu koncového bodu za běhu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="e41d2-145">Standardní koncový bod pro výměnu metadat.</span><span class="sxs-lookup"><span data-stu-id="e41d2-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="e41d2-146">Standardní koncový bod <xref:System.ServiceModel.WebHttpBinding> s vazbou, <xref:System.ServiceModel.Description.WebHttpBehavior> která automaticky přidá chování</span><span class="sxs-lookup"><span data-stu-id="e41d2-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="e41d2-147">Standardní koncový bod <xref:System.ServiceModel.WebHttpBinding> s vazbou, <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> která automaticky přidá chování.</span><span class="sxs-lookup"><span data-stu-id="e41d2-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="e41d2-148">Standardní koncový bod <xref:System.ServiceModel.WebHttpBinding> s vazbou.</span><span class="sxs-lookup"><span data-stu-id="e41d2-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="e41d2-149">Standardní koncový bod, který umožňuje volat operace řízení na instancích pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e41d2-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="e41d2-150">Standardní koncový bod, který podporuje vytváření pracovních postupů a obnovení záložek.</span><span class="sxs-lookup"><span data-stu-id="e41d2-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
