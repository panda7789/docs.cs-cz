---
title: Vlastní filtr zpráv
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183885"
---
# <a name="custom-message-filter"></a><span data-ttu-id="20f00-102">Vlastní filtr zpráv</span><span class="sxs-lookup"><span data-stu-id="20f00-102">Custom Message Filter</span></span>
<span data-ttu-id="20f00-103">Tato ukázka ukazuje, jak nahradit filtry zpráv, které Windows Communication Foundation (WCF) používá k odesílání zpráv do koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="20f00-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20f00-104">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="20f00-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="20f00-105">Když na server dorazí první zpráva na kanálu, musí server určit, které (pokud existuje) koncových bodů přidružených k tomuto identifikátoru URI by měly zprávu obdržet.</span><span class="sxs-lookup"><span data-stu-id="20f00-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="20f00-106">Tento proces je <xref:System.ServiceModel.Dispatcher.MessageFilter> řízen objekty <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>připojenými k .</span><span class="sxs-lookup"><span data-stu-id="20f00-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="20f00-107">Každý koncový bod služby <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>má jeden .</span><span class="sxs-lookup"><span data-stu-id="20f00-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="20f00-108">Má <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> jak <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>a .</span><span class="sxs-lookup"><span data-stu-id="20f00-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="20f00-109">Sjednocení těchto dvou filtrů je filtr zpráv používaný pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="20f00-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="20f00-110">Ve výchozím <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> nastavení pro koncový bod odpovídá všechny zprávy, která je určena na <xref:System.ServiceModel.EndpointAddress>adresu, která odpovídá koncovému bodu služby .</span><span class="sxs-lookup"><span data-stu-id="20f00-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="20f00-111">Ve výchozím <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> nastavení pro koncový bod kontroluje akci příchozí zprávy a porovnává všechny zprávy s akcí, která odpovídá jedné z akcí `IsInitiating` = `true` operací smlouvy koncového bodu služby (jsou považovány pouze akce).</span><span class="sxs-lookup"><span data-stu-id="20f00-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="20f00-112">V důsledku toho ve výchozím nastavení filtr pro koncový bod odpovídá pouze v <xref:System.ServiceModel.EndpointAddress> případě, že obě záhlaví zprávy Do je koncového bodu a akce zprávy odpovídá jedné z akcí operace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="20f00-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="20f00-113">Tyto filtry lze změnit pomocí chování.</span><span class="sxs-lookup"><span data-stu-id="20f00-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="20f00-114">Ve vzorku služba <xref:System.ServiceModel.Description.IEndpointBehavior> vytvoří, který nahradí <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>na :</span><span class="sxs-lookup"><span data-stu-id="20f00-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="20f00-115">Jsou definovány dva filtry adres:</span><span class="sxs-lookup"><span data-stu-id="20f00-115">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="20f00-116">Je `FilteringEndpointBehavior` konfigurovatelný a umožňuje dvě různé varianty.</span><span class="sxs-lookup"><span data-stu-id="20f00-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="20f00-117">Varianta 1 odpovídá pouze adresám, které obsahují "e" (ale které mají nějakou akci), zatímco varianta 2 odpovídá pouze adresám, které postrádají "e":</span><span class="sxs-lookup"><span data-stu-id="20f00-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="20f00-118">V konfiguračním souboru služba zaregistruje nové chování:</span><span class="sxs-lookup"><span data-stu-id="20f00-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="20f00-119">Pak služba `endpointBehavior` vytvoří konfigurace pro každou variantu:</span><span class="sxs-lookup"><span data-stu-id="20f00-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
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
  
 <span data-ttu-id="20f00-120">Nakonec koncový bod služby odkazuje na `behaviorConfigurations`jednu z :</span><span class="sxs-lookup"><span data-stu-id="20f00-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="20f00-121">Implementace klientské aplikace je jednoduchá; vytvoří dva kanály uri služby (předáním této hodnoty`via`jako druhý <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> parametr ( ) a odešle jednu zprávu na každém kanálu, ale používá různé adresy koncového bodu pro každý.</span><span class="sxs-lookup"><span data-stu-id="20f00-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="20f00-122">V důsledku toho odchozí zprávy z klienta mají různé To označení a server odpovídá odpovídajícím způsobem, o čemž svědčí výstup klienta:</span><span class="sxs-lookup"><span data-stu-id="20f00-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="20f00-123">Přepnutí míchací v konfiguračním souboru serveru způsobí, že filtr bude `urn:e` prohozen a klient `urn:a` uvidí opačné chování (zpráva bude úspěšná, zatímco zpráva se nezdaří).</span><span class="sxs-lookup"><span data-stu-id="20f00-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="20f00-124">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="20f00-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20f00-125">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="20f00-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="20f00-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="20f00-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20f00-127">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="20f00-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20f00-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="20f00-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="20f00-129">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20f00-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="20f00-130">Chcete-li spustit ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20f00-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="20f00-131">Chcete-li spustit ukázku v konfiguraci mezi počítači, postupujte podle pokynů na [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) a změňte následující řádek v Client.cs.</span><span class="sxs-lookup"><span data-stu-id="20f00-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="20f00-132">Nahraďte localhost názvem serveru.</span><span class="sxs-lookup"><span data-stu-id="20f00-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
