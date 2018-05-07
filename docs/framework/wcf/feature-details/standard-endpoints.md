---
title: Standardní koncové body
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 395d910ddabc553cca47dcdd038f44b1470b3455
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="standard-endpoints"></a>Standardní koncové body
Koncové body jsou definovány zadáním adresy, vazby a kontraktu. Další parametry, které může být nastaven na koncový bod patří konfigurace chování, záhlaví a naslouchání identifikátory URI.  Pro určité typy koncových bodů tyto hodnoty se nezmění. Například vždy použít koncové body metadat systému exchange <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt. Další koncové body, jako například <xref:System.ServiceModel.Description.WebHttpEndpoint> vždy vyžadují chování zadaný koncový bod. Tak, že jsou koncové body pomocí výchozí hodnoty pro vlastnosti běžně používané koncového bodu je možné zlepšit použitelnost koncový bod. Standardní koncové body umožňují vývojáři definovat koncový bod, který má výchozí hodnoty nebo kde vlastnosti jeden nebo více koncového bodu se nemění.  Tyto koncové body umožňují používat takové koncového bodu bez nutnosti zadávat informace, které statické. Standardní koncové body lze použít pro infrastrukturu a aplikaci koncové body.  
  
## <a name="infrastructure-endpoints"></a>Koncové body infrastruktury  
 Služba může vystavit koncové body se některé vlastnosti nejsou explicitně implementované vytváření služby. Například zpřístupní koncový bod metadat systému exchange <xref:System.ServiceModel.Description.IMetadataExchange> smlouvy, ale jako službu, můžete vytvářet neimplementuje rozhraní, je implementováno modulem WCF. Tyto infrastruktury koncové body mají výchozí hodnoty pro jednu nebo více vlastností koncový bod, některé z nich může být změnit. <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Musí být vlastnost koncovým bodem metadat exchange <xref:System.ServiceModel.Description.IMetadataExchange>, zatímco vývojáře můžete zadat další vlastnosti, například vazby. Koncové body infrastruktury se identifikují podle nastavení <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> vlastnost `true`.  
  
## <a name="application-endpoints"></a>Aplikace koncové body  
 Vývojáři aplikací můžete definovat svoje vlastní standardní koncové body, které určují výchozí hodnoty pro adresy, vazby nebo kontrakt. Můžete definovat koncový bod standardní odvozením třídy od <xref:System.ServiceModel.Description.ServiceEndpoint> a nastavení vlastností příslušný koncový bod. Můžete zadat výchozí hodnoty pro vlastnosti, které mohou být změněny. Některé další vlastnosti budou mít statické hodnoty, které nelze změnit. Následující příklad ukazuje, jak implementovat standardní koncový bod.  
  
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
  
 Chcete-li použít vlastní koncový bod uživatelem definované v konfiguračním souboru musí odvození třídy z <xref:System.ServiceModel.Configuration.StandardEndpointElement>, odvození třídy z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>a zaregistrujte nový standardní koncový bod v části rozšíření v souboru machine.config nebo v souboru app.config.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Poskytuje podporu konfigurace pro standardní koncový bod, jak je znázorněno v následujícím příkladu.  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Poskytuje základní typ pro kolekci, která se zobrazí pod <`standardEndpoints`> část v konfiguraci pro standardní koncový bod.  Následující příklad ukazuje, jak implementovat tuto třídu.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Následující příklad ukazuje, jak zaregistrovat koncový bod standardní na části rozšíření.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Koncový bod standardní konfigurace  
 Standardní koncové body mohou být přidány do kódu nebo v konfiguraci.  K přidání standardní koncového bodu v kódu jednoduše vytvořit instanci typu příslušné standardní koncový bod a přidejte ji do hostitele služby, jak je znázorněno v následujícím příkladu:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 K přidání standardní koncového bodu v konfiguraci, přidejte <`endpoint`> elementu, který chcete <`service`> elementu a všechny potřebné nastavení konfigurace v <`standardEndpoints`> elementu. Následující příklad ukazuje, jak přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jednu standardní koncové body, které se dodává s [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 Typ standardní koncového bodu je určen pomocí typu atributu v <`endpoint`> elementu. Koncový bod je nakonfigurované v rámci <`standardEndpoints`> elementu. V příkladu nahoře <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod a je nakonfigurovaný. <`udpDiscoveryEndpoint`> Obsahuje element <`standardEndpoint`>, který nastavuje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> vlastnost <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Standardní koncové body, které jsou součástí rozhraní .NET Framework  
 Následující tabulka uvádí standardní koncové body, které jsou součástí [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Standardní koncový bod, který se používá ke zveřejnění metadata služby.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Standardní koncový bod, který je používán služby zasílání oznámení.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Standardní koncový bod, který se používá služby k odesílání zprávy zjišťování.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Vytvoření vazby standardní koncový bod, který je předem nakonfigurován pro operace zjišťování přes UDP, vícesměrového vysílání.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Standardní koncový bod, který je používán služby pro odeslání zpráv oznámení vazbu UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Standardní koncový bod, který používá protokol WS-Discovery k vyhledání adresa koncového bodu dynamicky za běhu.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Standardní koncový bod pro metadata exchange.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby, který automaticky přidá <xref:System.ServiceModel.Description.WebHttpBehavior> chování  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby, který automaticky přidá <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> chování.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Standardní koncový bod s <xref:System.ServiceModel.WebHttpBinding> vazby.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Standardní koncový bod, který umožňuje volat operace ovládacího prvku na instancí pracovních postupů.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Standardní koncový bod, který podporuje vytváření a záložku obnovení pracovního postupu.
