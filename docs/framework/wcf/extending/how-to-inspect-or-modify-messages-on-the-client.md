---
title: "Postupy: Kontrola nebo úprava zprávy na straně klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06f4feaa5b0b44a26e3d31b65dc465b67544482f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Postupy: Kontrola nebo úprava zprávy na straně klienta
Můžete zkontrolovat nebo upravit příchozích nebo odchozích zpráv mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta implementací <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> a jejich vložení do modulu runtime klienta. Další informace najdete v tématu [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md). Ekvivalentní funkce služby je <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Kompletní příklad najdete v článku [inspektoři zpráv](../../../../docs/framework/wcf/samples/message-inspectors.md) ukázka.  
  
### <a name="to-inspect-or-modify-messages"></a>Chcete-li zkontrolovat nebo upravit zprávy  
  
1.  Implementace <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> rozhraní.  
  
2.  Implementace <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> v závislosti na oboru, ve kterém chcete vložit inspector zpráv klienta. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>Umožňuje změnit chování na úrovni koncového bodu. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>Umožňuje změnit chování na úrovni kontrakt.  
  
3.  Vložit chování před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu zobrazit v pořadí:  
  
-   Implementace inspector klienta.  
  
-   Chování koncového bodu, která vloží funkci Kontrola.  
  
-   A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-odvozené třídy, který umožňuje přidat chování v konfiguračním souboru.  
  
-   Konfigurační soubor, který přidává chování koncového bodu, která vloží inspector zpráv klienta do modulu runtime klienta.  
  
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
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
