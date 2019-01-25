---
title: Vlastní filtr zpráv
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 583c390c1f1a85df5b2dde3bcd06adf419eef668
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632137"
---
# <a name="custom-message-filter"></a><span data-ttu-id="bd2b0-102">Vlastní filtr zpráv</span><span class="sxs-lookup"><span data-stu-id="bd2b0-102">Custom Message Filter</span></span>
<span data-ttu-id="bd2b0-103">Tato ukázka předvádí, jak nahradit filtry zpráv, které Windows Communication Foundation (WCF) používá k odeslání zpráv do koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd2b0-104">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bd2b0-105">Při první zprávu v kanálu dorazí na server, server třeba určit, které (pokud existuje) o koncových bodech spojených s, který identifikátor URI by měla zobrazit zpráva.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="bd2b0-106">Tento proces se řídí <xref:System.ServiceModel.Dispatcher.MessageFilter> objekty připojené k <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="bd2b0-107">Každý koncový bod služby má jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="bd2b0-108"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Jsou obě <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="bd2b0-109">Spojení těchto dvou filtry se filtr zpráv pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="bd2b0-110">Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> pro koncový bod odpovídá všechny zprávy, které je určeno adresu, která odpovídá koncový bod služby <xref:System.ServiceModel.EndpointAddress>.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="bd2b0-111">Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> pro koncový bod zkontroluje akce příchozí zprávy a odpovídá jakékoli zprávy s akcí, které odpovídá jedné z akcí operace kontraktu koncového bodu služby (pouze `IsInitiating` = `true`akce jsou považovány za).</span><span class="sxs-lookup"><span data-stu-id="bd2b0-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="bd2b0-112">Proto ve výchozím nastavení, filtr pro koncový bod pouze odpovídá, pokud se obě zprávy do záhlaví <xref:System.ServiceModel.EndpointAddress> koncový bod a zprávy akce odpovídá jednomu z akce operace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="bd2b0-113">Tyto filtry lze změnit pomocí chování.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="bd2b0-114">V příkladu se vytvoří službu <xref:System.ServiceModel.Description.IEndpointBehavior> místo <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span><span class="sxs-lookup"><span data-stu-id="bd2b0-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 <span data-ttu-id="bd2b0-115">Jsou definovány dvě filtry adres:</span><span class="sxs-lookup"><span data-stu-id="bd2b0-115">Two address filters are defined:</span></span>  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 <span data-ttu-id="bd2b0-116">`FilteringEndpointBehavior` Se provádí konfigurovatelné a umožňuje pro dvě různé varianty.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 <span data-ttu-id="bd2b0-117">Variace 1 odpovídá pouze adresy, které obsahují "e" (ale, které mají jakoukoli akci) že variace 2 odpovídá jenom adresy, které nemají "e":</span><span class="sxs-lookup"><span data-stu-id="bd2b0-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="bd2b0-118">V konfiguračním souboru služby registruje nové chování:</span><span class="sxs-lookup"><span data-stu-id="bd2b0-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 <span data-ttu-id="bd2b0-119">Pak vytvoří službu `endpointBehavior` konfigurace pro každou změnu:</span><span class="sxs-lookup"><span data-stu-id="bd2b0-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
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
  
 <span data-ttu-id="bd2b0-120">Nakonec, jeden z koncového bodu služby odkazuje `behaviorConfigurations`:</span><span class="sxs-lookup"><span data-stu-id="bd2b0-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="bd2b0-121">Implementace klientské aplikace je jednoduchá; vytvoří dva kanály na identifikátor URI služby (předáním tuto hodnotu jako druhý (`via`) parametr k <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> a odešle zprávu jeden na každý kanál, ale používá jiný koncový bod adresy pro každý.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="bd2b0-122">V důsledku toho mají různé označení odchozích zpráv od klienta a serveru reagují odpovídajícím způsobem, jak je uvedeno ve výstupu klienta:</span><span class="sxs-lookup"><span data-stu-id="bd2b0-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="bd2b0-123">Přepínání variace v konfiguračním souboru serveru způsobí, že filtr pro záměnu a klient se zobrazí opačné chování (zpráva, která má `urn:e` proběhne úspěšně, zatímco zpráva, která má `urn:a` selže).</span><span class="sxs-lookup"><span data-stu-id="bd2b0-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd2b0-124">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd2b0-125">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bd2b0-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd2b0-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd2b0-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd2b0-128">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="bd2b0-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bd2b0-129">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd2b0-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="bd2b0-130">Spusťte ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd2b0-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bd2b0-131">Ke spuštění ukázky v konfiguraci mezi počítači, postupujte podle pokynů na adrese [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) a změňte následující řádek v Client.cs.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="bd2b0-132">Nahraďte názvem serveru localhost.</span><span class="sxs-lookup"><span data-stu-id="bd2b0-132">Replace localhost with the name of server.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bd2b0-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd2b0-133">See also</span></span>
