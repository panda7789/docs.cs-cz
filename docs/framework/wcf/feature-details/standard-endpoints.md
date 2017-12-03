---
title: "Standardní koncové body"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 869861ce1e2ba4456c8e8fbd06f9ff590fb3576a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="standard-endpoints"></a><span data-ttu-id="02a58-102">Standardní koncové body</span><span class="sxs-lookup"><span data-stu-id="02a58-102">Standard Endpoints</span></span>
<span data-ttu-id="02a58-103">Koncové body jsou definovány zadáním adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="02a58-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="02a58-104">Další parametry, které může být nastaven na koncový bod patří konfigurace chování, záhlaví a naslouchání identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="02a58-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="02a58-105">Pro určité typy koncových bodů tyto hodnoty se nezmění.</span><span class="sxs-lookup"><span data-stu-id="02a58-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="02a58-106">Například vždy použít koncové body metadat systému exchange <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt.</span><span class="sxs-lookup"><span data-stu-id="02a58-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="02a58-107">Další koncové body, jako například <xref:System.ServiceModel.Description.WebHttpEndpoint> vždy vyžadují chování zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02a58-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="02a58-108">Tak, že jsou koncové body pomocí výchozí hodnoty pro vlastnosti běžně používané koncového bodu je možné zlepšit použitelnost koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02a58-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="02a58-109">Standardní koncové body umožňují vývojáři definovat koncový bod, který má výchozí hodnoty nebo kde vlastnosti jeden nebo více koncového bodu se nemění.</span><span class="sxs-lookup"><span data-stu-id="02a58-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="02a58-110">Tyto koncové body umožňují používat takové koncového bodu bez nutnosti zadávat informace, které statické.</span><span class="sxs-lookup"><span data-stu-id="02a58-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="02a58-111">Standardní koncové body lze použít pro infrastrukturu a aplikaci koncové body.</span><span class="sxs-lookup"><span data-stu-id="02a58-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="02a58-112">Koncové body infrastruktury</span><span class="sxs-lookup"><span data-stu-id="02a58-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="02a58-113">Služba může vystavit koncové body se některé vlastnosti nejsou explicitně implementované vytváření služby.</span><span class="sxs-lookup"><span data-stu-id="02a58-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="02a58-114">Například zpřístupní koncový bod metadat systému exchange <xref:System.ServiceModel.Description.IMetadataExchange> smlouvy, ale jako službu, můžete vytvářet neimplementuje rozhraní, je implementováno modulem WCF.</span><span class="sxs-lookup"><span data-stu-id="02a58-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="02a58-115">Tyto infrastruktury koncové body mají výchozí hodnoty pro jednu nebo více vlastností koncový bod, některé z nich může být změnit.</span><span class="sxs-lookup"><span data-stu-id="02a58-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="02a58-116"><xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Musí být vlastnost koncovým bodem metadat exchange <xref:System.ServiceModel.Description.IMetadataExchange>, zatímco vývojáře můžete zadat další vlastnosti, například vazby.</span><span class="sxs-lookup"><span data-stu-id="02a58-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="02a58-117">Koncové body infrastruktury se identifikují podle nastavení <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="02a58-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="02a58-118">Aplikace koncové body</span><span class="sxs-lookup"><span data-stu-id="02a58-118">Application Endpoints</span></span>  
 <span data-ttu-id="02a58-119">Vývojáři aplikací můžete definovat svoje vlastní standardní koncové body, které určují výchozí hodnoty pro adresy, vazby nebo kontrakt.</span><span class="sxs-lookup"><span data-stu-id="02a58-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="02a58-120">Můžete definovat koncový bod standardní odvozením třídy od <xref:System.ServiceModel.Description.ServiceEndpoint> a nastavení vlastností příslušný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02a58-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="02a58-121">Můžete zadat výchozí hodnoty pro vlastnosti, které mohou být změněny.</span><span class="sxs-lookup"><span data-stu-id="02a58-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="02a58-122">Některé další vlastnosti budou mít statické hodnoty, které nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="02a58-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="02a58-123">Následující příklad ukazuje, jak implementovat standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02a58-123">The following example shows how to implement a standard endpoint.</span></span>  
  
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
  
 <span data-ttu-id="02a58-124">Chcete-li použít vlastní koncový bod uživatelem definované v konfiguračním souboru musí odvození třídy z <xref:System.ServiceModel.Configuration.StandardEndpointElement>, odvození třídy z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>a zaregistrujte nový standardní koncový bod v části rozšíření v souboru machine.config nebo v souboru app.config.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Poskytuje podporu konfigurace pro standardní koncový bod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="02a58-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="02a58-125"><xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Poskytuje základní typ pro kolekci, která se zobrazí pod <`standardEndpoints`> část v konfiguraci pro standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="02a58-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="02a58-126">Následující příklad ukazuje, jak implementovat tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="02a58-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="02a58-127">Následující příklad ukazuje, jak zaregistrovat koncový bod standardní na části rozšíření.</span><span class="sxs-lookup"><span data-stu-id="02a58-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="02a58-128">Koncový bod standardní konfigurace</span><span class="sxs-lookup"><span data-stu-id="02a58-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="02a58-129">Standardní koncové body mohou být přidány do kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="02a58-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="02a58-130">K přidání standardní koncového bodu v kódu jednoduše vytvořit instanci typu příslušné standardní koncový bod a přidejte ji do hostitele služby, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="02a58-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="02a58-131">K přidání standardní koncového bodu v konfiguraci, přidejte <`endpoint`> elementu, který chcete <`service`> elementu a všechny potřebné nastavení konfigurace v <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="02a58-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="02a58-132">Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jednu standardní koncové body, které se dodává s [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02a58-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
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
  
 <span data-ttu-id="02a58-133">Typ standardní koncového bodu je určen pomocí typu atributu v <`endpoint`> elementu.</span><span class="sxs-lookup"><span data-stu-id="02a58-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="02a58-134">Koncový bod je nakonfigurované v rámci <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="02a58-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="02a58-135">V příkladu nahoře <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod a je nakonfigurovaný.</span><span class="sxs-lookup"><span data-stu-id="02a58-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="02a58-136"><`udpDiscoveryEndpoint`> Obsahuje element <`standardEndpoint`>, který nastavuje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> vlastnost <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="02a58-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="02a58-137">Standardní koncové body, které jsou součástí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="02a58-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="02a58-138">Následující tabulka uvádí standardní koncové body, které jsou součástí [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02a58-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="02a58-139">Standardní koncový bod, který se používá ke zveřejnění metadata služby.</span><span class="sxs-lookup"><span data-stu-id="02a58-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="02a58-140">Standardní koncový bod, který je používán služby zasílání oznámení.</span><span class="sxs-lookup"><span data-stu-id="02a58-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="02a58-141">Standardní koncový bod, který se používá služby k odesílání zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="02a58-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="02a58-142">Vytvoření vazby standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes UDP, vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="02a58-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="02a58-143">Standardní koncový bod, který je používán služby pro odeslání zpráv oznámení vazbu UDP.</span><span class="sxs-lookup"><span data-stu-id="02a58-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="02a58-144">Standardní koncový bod, který používá protokol WS-Discovery k vyhledání adresa koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="02a58-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="02a58-145">Standardní koncový bod pro metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="02a58-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="02a58-146">Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby, který automaticky přidá <xref:System.ServiceModel.Description.WebHttpBehavior> chování</span><span class="sxs-lookup"><span data-stu-id="02a58-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="02a58-147">Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby, který automaticky přidá <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> chování.</span><span class="sxs-lookup"><span data-stu-id="02a58-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="02a58-148">Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="02a58-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="02a58-149">Standardní koncový bod, který umožňuje volat operace ovládacího prvku na instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="02a58-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="02a58-150">Standardní koncový bod, který podporuje vytváření a záložku obnovení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="02a58-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
