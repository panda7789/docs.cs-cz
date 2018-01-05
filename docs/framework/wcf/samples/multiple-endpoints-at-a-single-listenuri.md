---
title: "Víc koncových bodů na jedné adrese ListenUri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 909fb35f9b8e4628df06918f207c3c86770a2d4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="dada6-102">Víc koncových bodů na jedné adrese ListenUri</span><span class="sxs-lookup"><span data-stu-id="dada6-102">Multiple Endpoints at a Single ListenUri</span></span>
<span data-ttu-id="dada6-103">Tento příklad znázorňuje služby, který je hostitelem víc koncových bodů na jedné `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="dada6-103">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="dada6-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="dada6-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dada6-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="dada6-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="dada6-106">Jak je předvedeno v [několik koncových bodů](../../../../docs/framework/wcf/samples/multiple-endpoints.md) ukázku, služba může hostovat několik koncových bodů, každý s různé adresy a případně také různé vazby.</span><span class="sxs-lookup"><span data-stu-id="dada6-106">As demonstrated in the [Multiple Endpoints](../../../../docs/framework/wcf/samples/multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="dada6-107">Tento příklad ukazuje, že je možné k hostování víc koncových bodů na stejnou adresu.</span><span class="sxs-lookup"><span data-stu-id="dada6-107">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="dada6-108">Tento příklad znázorňuje také rozdíly mezi dva druhy adresy, které má koncový bod služby: `EndpointAddress` a `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="dada6-108">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="dada6-109">`EndpointAddress` Je adresa logické služby.</span><span class="sxs-lookup"><span data-stu-id="dada6-109">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="dada6-110">Je na adresu, která jsou určena protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="dada6-110">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="dada6-111">`ListenUri` Je fyzická adresa služby.</span><span class="sxs-lookup"><span data-stu-id="dada6-111">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="dada6-112">Obsahuje informace o portu a adresu kde koncový bod služby ve skutečnosti přijímá zprávy do aktuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="dada6-112">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="dada6-113">Ve většině případů není třeba pro tyto adresy do liší; Když `ListenUri` není explicitně zadané, nastaví se jako výchozí identifikátor URI `EndpointAddress` koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="dada6-113">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="dada6-114">V určitých případech je užitečné k rozlišení, například při konfiguraci směrovač, který může přijmout zprávy adresované do několik různých služeb.</span><span class="sxs-lookup"><span data-stu-id="dada6-114">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="dada6-115">Služba</span><span class="sxs-lookup"><span data-stu-id="dada6-115">Service</span></span>  
 <span data-ttu-id="dada6-116">Služba v této ukázce má dva kontrakty `ICalculator` a `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="dada6-116">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="dada6-117">Kromě obvyklé `IMetadataExchange` koncový bod, existují tři koncových bodů aplikace, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="dada6-117">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="dada6-118">Všechny tři koncové body jsou hostované ve stejné `ListenUri` a používat stejné `binding` -koncových bodů ve stejné `ListenUri` musí mít stejnou vazbu, protože jejich sdílení jednoho kanálu zásobníku, která přijímá zprávy v této fyzickou adresu na počítač.</span><span class="sxs-lookup"><span data-stu-id="dada6-118">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="dada6-119">`address` Každý koncový bod je název URN; když adresy obvykle představují fyzického umístění, ve skutečnosti adresa může být jakýkoli druh identifikátor URI, protože adresa se používá pro porovnávání a filtrování účely, jak je ukázáno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="dada6-119">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="dada6-120">Protože všechny tři koncové body sdílet stejný `ListenUri`, pokud existuje, doručení zprávy [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] musíte se rozhodnout, kterému koncovému bodu zprávy je určené pro.</span><span class="sxs-lookup"><span data-stu-id="dada6-120">Because all three endpoints share the same `ListenUri`, when a message arrives there, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="dada6-121">Každý koncový bod má filtr zpráv, která se skládá ze dvou částí: Filtr adres a filtru smlouvy.</span><span class="sxs-lookup"><span data-stu-id="dada6-121">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="dada6-122">Filtr adres odpovídá `To` protokolu SOAP zprávy na adresu koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="dada6-122">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="dada6-123">Například pouze zprávy adresované `To "Urn:OtherEcho"` jsou kandidáty pro třetí koncový bod této služby.</span><span class="sxs-lookup"><span data-stu-id="dada6-123">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="dada6-124">Filtr smlouvy odpovídá akce přidružené těmto operacím konkrétní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="dada6-124">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="dada6-125">Příklad zprávy s akcí `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="dada6-125">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="dada6-126">`Echo`odpovídá filtry kontrakt druhé a třetí koncových bodů služby, protože obě tyto koncové body hostitele `IEcho` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="dada6-126">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="dada6-127">Proto kombinace adresu filtr a kontraktů umožňuje směrovat každou zprávu, která dorazí na tuto službu `ListenUri` správný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dada6-127">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="dada6-128">Třetí koncový bod je z další dvě hodnoty, protože přijímá zprávy odeslané na jinou adresu z dalších koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="dada6-128">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="dada6-129">První a druhý koncových bodů jsou rozlišené od sebe navzájem na základě jejich smluv (akce příchozí zprávy).</span><span class="sxs-lookup"><span data-stu-id="dada6-129">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="dada6-130">Klient</span><span class="sxs-lookup"><span data-stu-id="dada6-130">Client</span></span>  
 <span data-ttu-id="dada6-131">Podobně jako koncové body na serveru dvě různé adresy, koncové body klienta také mít dvě adresy.</span><span class="sxs-lookup"><span data-stu-id="dada6-131">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="dada6-132">Na serveru a klienta, se nazývá logické adresy `EndpointAddress`.</span><span class="sxs-lookup"><span data-stu-id="dada6-132">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="dada6-133">Ale vzhledem k tomu, se nazývá fyzickou adresu `ListenUri` na serveru, na straně klienta, se nazývá fyzickou adresu `Via`.</span><span class="sxs-lookup"><span data-stu-id="dada6-133">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="dada6-134">Tyto dvě adresy jako na serveru, ve výchozím nastavení jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="dada6-134">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="dada6-135">Chcete-li určit `Via` v klientovi, který se liší od adresy pro koncový bod `ClientViaBehavior` se používá:</span><span class="sxs-lookup"><span data-stu-id="dada6-135">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="dada6-136">Adresu jako obvykle pochází z konfiguračního souboru klienta, který byl vygenerován nástrojem Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="dada6-136">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="dada6-137">`Via` (Která odpovídá `ListenUri` služby) pravděpodobně není v metadatech služby a tak tyto informace se sdělí klienta out-of-band (stejně jako adresu metadata služby).</span><span class="sxs-lookup"><span data-stu-id="dada6-137">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="dada6-138">Klient v této ukázce odešle zprávy ke každému serveru tři koncových bodů aplikace k předvedení to může komunikovat s (a odlišují jej od) všechny tři koncové body, i když všechny mají stejné `Via`.</span><span class="sxs-lookup"><span data-stu-id="dada6-138">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dada6-139">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="dada6-139">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="dada6-140">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dada6-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="dada6-141">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dada6-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="dada6-142">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dada6-142">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dada6-143">Cross-počítače je potřeba nahradit localhost v souboru Client.cs název počítače, služby.</span><span class="sxs-lookup"><span data-stu-id="dada6-143">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dada6-144">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="dada6-144">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dada6-145">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="dada6-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dada6-146">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="dada6-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dada6-147">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="dada6-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a><span data-ttu-id="dada6-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="dada6-148">See Also</span></span>
