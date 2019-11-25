---
title: Vlastní filtr zpráv
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 9c0fe8ab3412976d9ccddac23e23d9c70f707a89
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978318"
---
# <a name="custom-message-filter"></a><span data-ttu-id="7fab2-102">Vlastní filtr zpráv</span><span class="sxs-lookup"><span data-stu-id="7fab2-102">Custom Message Filter</span></span>
<span data-ttu-id="7fab2-103">Tato ukázka demonstruje, jak nahradit filtry zpráv, které Windows Communication Foundation (WCF) používá k odesílání zpráv do koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="7fab2-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fab2-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7fab2-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7fab2-105">Když první zpráva na kanálu dorazí na server, server musí určit, který (pokud existuje) koncových bodů přidružených k tomuto identifikátoru URI by měla obdržet zprávu.</span><span class="sxs-lookup"><span data-stu-id="7fab2-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="7fab2-106">Tento proces je řízen <xref:System.ServiceModel.Dispatcher.MessageFilter> objekty připojenými k <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="7fab2-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="7fab2-107">Každý koncový bod služby má jednu <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="7fab2-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="7fab2-108"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> má <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="7fab2-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="7fab2-109">Sjednocením těchto dvou filtrů je filtr zpráv použitý pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7fab2-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="7fab2-110">Ve výchozím nastavení se <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> pro koncový bod shoduje se všemi zprávami, které jsou adresovány na adresu, která odpovídá <xref:System.ServiceModel.EndpointAddress>koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="7fab2-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="7fab2-111">Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> pro koncový bod kontroluje akci příchozí zprávy a odpovídá jakékoli zprávě s akcí, která odpovídá jedné z akcí operací kontraktu koncového bodu služby (jenom `IsInitiating`=jsou zvažovány `true` akce).</span><span class="sxs-lookup"><span data-stu-id="7fab2-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="7fab2-112">V důsledku toho filtr pro koncový bod ve výchozím nastavení odpovídá pouze v případě, že se jedná o <xref:System.ServiceModel.EndpointAddress> koncového bodu a akce zprávy odpovídá jedné z akcí operace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7fab2-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="7fab2-113">Tyto filtry je možné změnit pomocí chování.</span><span class="sxs-lookup"><span data-stu-id="7fab2-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="7fab2-114">V ukázce služba vytvoří <xref:System.ServiceModel.Description.IEndpointBehavior>, která nahrazuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span><span class="sxs-lookup"><span data-stu-id="7fab2-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="7fab2-115">Jsou definovány dva filtry adres:</span><span class="sxs-lookup"><span data-stu-id="7fab2-115">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="7fab2-116">`FilteringEndpointBehavior` je možné konfigurovat a umožňuje dvě různé varianty.</span><span class="sxs-lookup"><span data-stu-id="7fab2-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="7fab2-117">Variace 1 odpovídá jenom adresám, které obsahují "e" (ale mají jakoukoliv akci), zatímco variace 2 odpovídá jenom adresám, které nemají:</span><span class="sxs-lookup"><span data-stu-id="7fab2-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="7fab2-118">V konfiguračním souboru služba zaregistruje nové chování:</span><span class="sxs-lookup"><span data-stu-id="7fab2-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 <span data-ttu-id="7fab2-119">Potom služba vytvoří `endpointBehavior` konfigurace pro každou variaci:</span><span class="sxs-lookup"><span data-stu-id="7fab2-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 <span data-ttu-id="7fab2-120">Nakonec koncový bod služby odkazuje na jednu z `behaviorConfigurations`:</span><span class="sxs-lookup"><span data-stu-id="7fab2-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="7fab2-121">Implementace klientské aplikace je jednoduchá; k identifikátoru URI služby vytvoří dva kanály (předáním této hodnoty jako druhý parametr (`via`) <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> a pošle jednu zprávu na každý kanál, ale pro každou z nich používá jiné adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="7fab2-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="7fab2-122">Výsledkem je, že odchozí zprávy z klienta se liší od označení a server reaguje odpovídajícím způsobem, jak ukazuje výstup klienta:</span><span class="sxs-lookup"><span data-stu-id="7fab2-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="7fab2-123">Přepnutí změn v konfiguračním souboru serveru způsobí, že se filtr promění a klient uvidí opačné chování (zpráva pro `urn:e` úspěšná, zatímco zpráva, která `urn:a` selže).</span><span class="sxs-lookup"><span data-stu-id="7fab2-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="7fab2-124">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="7fab2-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7fab2-125">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="7fab2-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7fab2-126">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="7fab2-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7fab2-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7fab2-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7fab2-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7fab2-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7fab2-129">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7fab2-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="7fab2-130">Pokud chcete ukázku spustit v konfiguraci s jedním počítačem, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7fab2-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7fab2-131">Pokud chcete ukázku spustit v konfiguraci mezi počítači, postupujte podle pokynů v článku [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) a v Client.cs změňte následující řádek.</span><span class="sxs-lookup"><span data-stu-id="7fab2-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="7fab2-132">Položku localhost nahraďte názvem serveru.</span><span class="sxs-lookup"><span data-stu-id="7fab2-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
