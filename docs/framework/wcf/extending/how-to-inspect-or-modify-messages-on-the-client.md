---
title: 'Postupy: Kontrola a změny zpráv v klientovi'
description: Přečtěte si, jak zkontrolovat nebo upravit příchozí nebo odchozí zprávy v rámci klienta nebo služby WCF implementací vhodného rozhraní.
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 6f6a3d20d7f3a9fb79de5cd3e29096e270d0f188
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247504"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="0e350-103">Postupy: Kontrola a změny zpráv v klientovi</span><span class="sxs-lookup"><span data-stu-id="0e350-103">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="0e350-104">Můžete kontrolovat nebo upravovat příchozí nebo odchozí zprávy v klientovi WCF implementací <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> a vložením do modulu runtime klienta.</span><span class="sxs-lookup"><span data-stu-id="0e350-104">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="0e350-105">Další informace najdete v tématu [rozšíření klientů](extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0e350-105">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="0e350-106">Ekvivalentní funkce služby je <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e350-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0e350-107">Úplný příklad kódu najdete v tématu Ukázka [kontrolorů zpráv](../samples/message-inspectors.md) .</span><span class="sxs-lookup"><span data-stu-id="0e350-107">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="0e350-108">Kontrola nebo změna zpráv</span><span class="sxs-lookup"><span data-stu-id="0e350-108">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="0e350-109">Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e350-109">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="0e350-110">Implementujte <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> v závislosti na rozsahu, ve kterém chcete vložit inspektor zprávy klienta.</span><span class="sxs-lookup"><span data-stu-id="0e350-110">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="0e350-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>umožňuje změnit chování na úrovni koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="0e350-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="0e350-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>umožňuje změnit chování na úrovni smlouvy.</span><span class="sxs-lookup"><span data-stu-id="0e350-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="0e350-113">Před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> metody nebo v zadejte chování <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e350-113">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0e350-114">Podrobnosti najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="0e350-114">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e350-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e350-115">Example</span></span>  
 <span data-ttu-id="0e350-116">Následující příklady kódu ukazují, v pořadí:</span><span class="sxs-lookup"><span data-stu-id="0e350-116">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="0e350-117">Implementace inspektora klienta.</span><span class="sxs-lookup"><span data-stu-id="0e350-117">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="0e350-118">Chování koncového bodu, které vkládá inspektor.</span><span class="sxs-lookup"><span data-stu-id="0e350-118">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="0e350-119"><xref:System.ServiceModel.Configuration.BehaviorExtensionElement>Třída odvozená, která umožňuje přidat chování do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0e350-119">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="0e350-120">Konfigurační soubor, který přidá chování koncového bodu, které vloží inspektor zprávy klienta do modulu runtime klienta.</span><span class="sxs-lookup"><span data-stu-id="0e350-120">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e350-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e350-121">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="0e350-122">Konfigurace a rozšíření modulu runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="0e350-122">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
