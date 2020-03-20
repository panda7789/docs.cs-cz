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
# <a name="standard-endpoints"></a>Standardní koncové body
Koncové body jsou definovány zadáním adresy, vazby a smlouvy. Mezi další parametry, které mohou být nastaveny v koncovém bodě, patří konfigurace chování, záhlaví a naslouchání identifikátorů URI.  U určitých typů koncových bodů se tyto hodnoty nemění. Například koncové body výměny metadat <xref:System.ServiceModel.Description.IMetadataExchange> vždy používají smlouvy. Jiné koncové body, <xref:System.ServiceModel.Description.WebHttpEndpoint> například vždy vyžadují zadané chování koncového bodu. Použitelnost koncového bodu lze zlepšit tím, že koncové body s výchozí hodnoty pro běžně používané vlastnosti koncového bodu. Standardní koncové body umožňují vývojáři definovat koncový bod, který má výchozí hodnoty nebo kde se nemění vlastnosti jednoho nebo více koncových bodů.  Tyto koncové body umožňují použít takový koncový bod bez nutnosti zadat informace statické povahy. Standardní koncové body lze použít pro koncové body infrastruktury a aplikace.  
  
## <a name="infrastructure-endpoints"></a>Koncové body infrastruktury  
 Služba může vystavit koncové body s některými vlastnostmi, které nejsou explicitně implementovány autorem služby. Například koncový bod výměny metadat <xref:System.ServiceModel.Description.IMetadataExchange> zveřejňuje smlouvy, ale jako autor služby neimplementujete toto rozhraní, je implementována WCF. Tyto koncové body infrastruktury mají výchozí hodnoty pro jednu nebo více vlastností koncového bodu, z nichž některé mohou být neměnné. Vlastnost <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> koncového bodu výměny metadat <xref:System.ServiceModel.Description.IMetadataExchange>musí být , zatímco jiné vlastnosti, jako je vazba může být poskytnuta vývojář. Koncové body infrastruktury jsou <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> identifikovány nastavením vlastnosti `true`.  
  
## <a name="application-endpoints"></a>Koncové body aplikace  
 Vývojáři aplikací můžete definovat své vlastní standardní koncové body, které určují výchozí hodnoty pro adresu, vazbu nebo smlouvu. Standardní koncový bod definujete odvozením třídy z <xref:System.ServiceModel.Description.ServiceEndpoint> a nastavením příslušných vlastností koncového bodu. Můžete zadat výchozí hodnoty pro vlastnosti, které lze změnit. Některé další vlastnosti budou mít statické hodnoty, které se nemohou změnit. Následující příklad ukazuje, jak implementovat standardní koncový bod.  
  
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
  
 Chcete-li použít vlastní koncový bod definovaný uživatelem v <xref:System.ServiceModel.Configuration.StandardEndpointElement>konfiguračním <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>souboru, musíte odvodit třídu z , odvodit třídu z aplikace a zaregistrovat nový standardní koncový bod v části rozšíření v souboru app.config nebo machine.config.  Poskytuje <xref:System.ServiceModel.Configuration.StandardEndpointElement> podporu konfigurace pro standardní koncový bod, jak je znázorněno v následujícím příkladu.  
  
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
  
 Poskytuje <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> typ zálohování pro kolekci, která `standardEndpoints` se zobrazí pod <> části v konfiguraci pro standardní koncový bod.  Následující příklad ukazuje, jak implementovat tuto třídu.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Následující příklad ukazuje, jak zaregistrovat standardní koncový bod v části rozšíření.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Konfigurace standardního koncového bodu  
 Standardní koncové body lze přidat v kódu nebo v konfiguraci.  Chcete-li přidat standardní koncový bod v kódu, jednoduše vytvořte instanci příslušného standardního typu koncového bodu a přidejte jej do hostitele služby, jak je znázorněno v následujícím příkladu:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Chcete-li přidat standardní koncový bod `endpoint` v konfiguraci, `service` přidejte <> prvek `standardEndpoints` do <> elementu a všechna potřebná nastavení konfigurace v elementu <>. Následující příklad <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>ukazuje, jak přidat jeden ze standardních [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]koncových bodů, které jsou dodávány s .  
  
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
  
 Typ standardního koncového bodu je určen pomocí `endpoint` atributu kind v elementu <>. Koncový bod je konfigurován `standardEndpoints` v rámci <> elementu. Ve výše uvedeném <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> příkladu je přidán a nakonfigurován koncový bod. Prvek `udpDiscoveryEndpoint` <> obsahuje `standardEndpoint` <>, která nastaví <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> vlastnost <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Standardní koncové body dodávané s rozhraním .NET Framework  
 V následující tabulce jsou uvedeny [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]standardní koncové body dodávané s .  
  
 `Mex Endpoint`  
 Standardní koncový bod, který se používá k odhalení metadat služby.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Standardní koncový bod, který používá služby k odesílání zpráv oznámení.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Standardní koncový bod, který používá služby k odesílání zpráv zjišťování.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes vazbu vícesměrového vysílání UDP.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Standardní koncový bod, který používá služby k odesílání zpráv oznámení prostřednictvím vazby UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Standardní koncový bod, který používá WS-Discovery dynamicky najít adresu koncového bodu za běhu.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Standardní koncový bod pro výměnu metadat.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Standardní koncový bod <xref:System.ServiceModel.WebHttpBinding> s vazbou, <xref:System.ServiceModel.Description.WebHttpBehavior> která automaticky přidá chování  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Standardní koncový bod <xref:System.ServiceModel.WebHttpBinding> s vazbou, <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> která automaticky přidá chování.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Standardní koncový bod <xref:System.ServiceModel.WebHttpBinding> s vazbou.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Standardní koncový bod, který umožňuje volat operace řízení na instancích pracovního postupu.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Standardní koncový bod, který podporuje vytváření pracovních postupů a obnovení záložek.
