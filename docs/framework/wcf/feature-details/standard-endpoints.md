---
title: Standardní koncové body
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 395d910ddabc553cca47dcdd038f44b1470b3455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747768"
---
# <a name="standard-endpoints"></a>Standardní koncové body
Koncové body jsou definovány tak, že zadáte adresu, vazba a kontrakt. Další parametry, které lze nastavit v koncovém bodě zahrnují konfiguraci chování, záhlaví a identifikátory URI vychází vstříc požadavkům.  Pro některé typy koncových bodů tyto hodnoty nezměníte. Například vždy používat koncové body metadat systému exchange <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu. Další koncové body, jako například <xref:System.ServiceModel.Description.WebHttpEndpoint> vždy vyžadují chování zadaný koncový bod. Použitelnost koncový bod lze zvýšit tím, že koncové body s použitím výchozích hodnot pro vlastnosti běžně používaných koncového bodu. Standardní koncové body umožňují vývojářům definovat koncový bod, který má výchozí hodnoty nebo pokud jeden nebo více vlastnosti tohoto koncového bodu se nezmění.  Tyto koncové body umožňují jeho používání takové koncového bodu bez nutnosti zadávat informace statické povahy. Standardní koncové body, je možné pro infrastrukturu a aplikaci koncové body.  
  
## <a name="infrastructure-endpoints"></a>Koncové body infrastruktury  
 Služba může zpřístupňují koncové body se některé vlastnosti nejsou explicitně implementovaných Autor služby. Například zpřístupňuje koncový bod výměny metadat <xref:System.ServiceModel.Description.IMetadataExchange> smlouvy, ale jako služba autorem je neimplementují rozhraní, je implementováno WCF. Tyto koncové body infrastruktury mají výchozí hodnoty pro jeden nebo více vlastnosti koncového bodu, z nichž některé mohou být změnit. <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Vlastnost koncový bod výměny metadat musí být <xref:System.ServiceModel.Description.IMetadataExchange>, ale lze je zadat další vlastnosti, například vazby vývojářem. Koncové body infrastruktury jsou označeny nastavení <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> vlastnost `true`.  
  
## <a name="application-endpoints"></a>Koncové body aplikace  
 Vývojáři aplikací můžete definovat vlastní standardních koncových bodů, které určují výchozí hodnoty pro adresy, vazby nebo kontraktu. Můžete definovat standardní koncový bod odvozením třídy od <xref:System.ServiceModel.Description.ServiceEndpoint> a nastavení vlastností vhodný koncový bod. Můžete zadat výchozí hodnoty pro vlastnosti, které je možné změnit. Některé vlastnosti budou mít statické hodnoty, které nelze změnit. Následující příklad ukazuje, jak implementovat standardní koncový bod.  
  
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
  
 Použít vlastní koncový bod definovaný uživatelem v konfiguračním souboru musí být odvozen ze třídy <xref:System.ServiceModel.Configuration.StandardEndpointElement>, odvoďte třídu z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>a zaregistrujte nový standardní koncový bod v oddílu rozšíření, v souboru machine.config nebo v souboru app.config.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Poskytuje podporu konfigurace pro standardní koncový bod, jak je znázorněno v následujícím příkladu.  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Poskytuje základní typ pro kolekci, která se zobrazí v části <`standardEndpoints`> oddíl konfigurace pro standardní koncový bod.  Následující příklad ukazuje implementaci této třídy.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Následující příklad ukazuje, jak zaregistrovat v oddílu rozšíření, je standardní koncový bod.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Konfigurace je standardní koncový bod  
 Standardní koncové body mohou být přidány do kódu nebo v konfiguraci.  Chcete-li přidat standardní koncový bod v kódu jednoduše vytvořit instanci typu odpovídající standardní koncový bod a přidejte ho k hostiteli služby, jak je znázorněno v následujícím příkladu:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Chcete-li přidat standardní koncový bod v konfiguraci, přidejte <`endpoint`> element <`service`> element a všechny potřebné nastavení konfigurace v <`standardEndpoints`> element. Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jeden z standardních koncových bodů, které se dodává s [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 Typ standardního koncového bodu určena pomocí atributu kind v <`endpoint`> element. Koncový bod je nakonfigurovaný v rámci <`standardEndpoints`> element. V příkladu výše <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod je přidáte a nakonfigurujete. <`udpDiscoveryEndpoint`> Obsahuje element <`standardEndpoint`>, který nastavuje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> vlastnost <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Standardní koncové body, které jsou součástí rozhraní .NET Framework  
 Následující tabulka uvádí standardní koncové body, které jsou součástí [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Standardní koncový bod, který se používá ke zveřejnění metadat služby.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Je standardní koncový bod, který používá services k odesílání zprávy oznámení.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Je standardní koncový bod, který se používá Services k odesílání zprávy zjišťování.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování přes vícesměrové vysílání UDP vazby.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Je standardní koncový bod, který používá služby pro odeslání zpráv oznámení UDP vazby.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Standardní koncový bod, který používá protokol WS Discovery k vyhledání adresu koncového bodu dynamicky za běhu.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Standardní koncový bod výměny metadat.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby, která automaticky přidá <xref:System.ServiceModel.Description.WebHttpBehavior> chování  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby, která automaticky přidá <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> chování.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Standardní koncový bod, který umožňuje zavolání operace ovládacího prvku s instancí pracovního postupu.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Standardní koncový bod, který podporuje vytváření a záložku obnovení pracovního postupu.
