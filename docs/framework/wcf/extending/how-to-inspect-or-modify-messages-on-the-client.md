---
title: 'Postupy: Kontrola a změny zpráv v klientovi'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: db1a99d2ed1f765e39815e6b6c70d6ada1db1d15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185529"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Postupy: Kontrola a změny zpráv v klientovi
Můžete zkontrolovat nebo upravit příchozí nebo odchozí zprávy přes wcf <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> klienta implementací a vložením do běhu klienta. Další informace naleznete v [tématu Rozšíření klientů](extending-clients.md). Ekvivalentní funkce služby je <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Úplný příklad kódu naleznete v ukázce [Inspektory zpráv.](../samples/message-inspectors.md)  
  
### <a name="to-inspect-or-modify-messages"></a>Kontrola nebo úprava zpráv  
  
1. Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
2. Implementujte <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> nebo v závislosti na oboru, do kterého chcete vložit inspektor zpráv klienta. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>umožňuje změnit chování na úrovni koncového bodu. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>umožňuje změnit chování na úrovni smlouvy.  
  
3. Před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> metody nebo <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na metodu na <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Podrobnosti naleznete [v tématu Konfigurace a rozšíření běhu s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu ukazují, v pořadí:  
  
- Implementace inspektora klienta.  
  
- Chování koncového bodu, který vloží inspektor.  
  
- A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- odvozené třídy, která umožňuje přidat chování v konfiguračním souboru.  
  
- Konfigurační soubor, který přidá chování koncového bodu, který vloží inspektor zpráv klienta do běhu klienta.  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md)
