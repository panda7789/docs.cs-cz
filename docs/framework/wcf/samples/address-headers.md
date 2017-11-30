---
title: "Hlavičky adresy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19a7291ce13221e85b49c6ef97c6b375b8b71014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="address-headers"></a><span data-ttu-id="67084-102">Hlavičky adresy</span><span class="sxs-lookup"><span data-stu-id="67084-102">Address Headers</span></span>
<span data-ttu-id="67084-103">Příklad hlavičky adresy ukazuje, jak mohou klienti předat parametry odkaz na službu pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67084-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67084-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="67084-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="67084-105">Specifikace WS-Addressing definuje představu o odkaz na koncový bod jako způsob, jak konkrétní koncový bod webové služby.</span><span class="sxs-lookup"><span data-stu-id="67084-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="67084-106">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], koncový bod odkazy jsou modelovány pomocí `EndpointAddress` třída - `EndpointAddress` je typ pole adresy `ServiceEndpoint` – třída.</span><span class="sxs-lookup"><span data-stu-id="67084-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="67084-107">Část referenčního modelu koncový bod je, že každý odkaz přenášet některé odkaz parametry, které přidat velmi identifikační informace.</span><span class="sxs-lookup"><span data-stu-id="67084-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="67084-108">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], tyto parametry odkaz jsou modelovat jako instance `AddressHeader` třídy.</span><span class="sxs-lookup"><span data-stu-id="67084-108">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="67084-109">V této ukázce klienta přidá odkaz na parametr, který se `EndpointAddress` koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="67084-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="67084-110">Služba hledá tento odkaz na parametr a používá jeho hodnotu v logice jeho operace služby "Hello".</span><span class="sxs-lookup"><span data-stu-id="67084-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="67084-111">Klient</span><span class="sxs-lookup"><span data-stu-id="67084-111">Client</span></span>  
 <span data-ttu-id="67084-112">Pro klienta k odesílání parametr odkaz, musíte přidat `AddressHeader` k `EndpointAddress` z `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="67084-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="67084-113">Protože `EndpointAddress` třídy se nedá změnit, změna adresy koncového bodu je třeba provést pomocí `EndpointAddressBuilder` – třída.</span><span class="sxs-lookup"><span data-stu-id="67084-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="67084-114">Následující kód inicializuje klientovi umožní odeslat odkaz na parametr jako součást zprávy.</span><span class="sxs-lookup"><span data-stu-id="67084-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```  
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="67084-115">Kód vytvoří `EndpointAddressBuilder` pomocí původní `EndpointAddress` jako počáteční hodnota.</span><span class="sxs-lookup"><span data-stu-id="67084-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="67084-116">Potom přidá hlavičku nově vytvořený adresu; volání `CreateAddressHeadercreates` hlavička s konkrétním názvem, obor názvů a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67084-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="67084-117">V tomto poli hodnota je "Jan".</span><span class="sxs-lookup"><span data-stu-id="67084-117">Here the value is "John".</span></span> <span data-ttu-id="67084-118">Jakmile záhlaví se přidá do Tvůrce `ToEndpointAddress()` metoda převede (měnitelný) Tvůrce zpět na adresu koncového bodu (neměnné), která je přiřazená zpět do pole Adresa koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="67084-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="67084-119">Teď, když volání klienta `Console.WriteLine(client.Hello());`, služba je moct získat hodnotu tohoto parametru adresu, jak je vidět ve výsledném výstupu klienta.</span><span class="sxs-lookup"><span data-stu-id="67084-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="67084-120">Server</span><span class="sxs-lookup"><span data-stu-id="67084-120">Server</span></span>  
 <span data-ttu-id="67084-121">Provádění operace služby `Hello()` používá aktuální `OperationContext` zkontrolovat hodnoty hlavičky na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="67084-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
```  
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h =   
        OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr =   
OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 <span data-ttu-id="67084-122">Kód iteruje nad všechny hlavičky na příchozí zprávy, hledá hlavičky, které jsou parametry odkaz s určitým názvem a.</span><span class="sxs-lookup"><span data-stu-id="67084-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="67084-123">Když se najde parametr čte hodnotu parametru a ukládá v proměnné "id".</span><span class="sxs-lookup"><span data-stu-id="67084-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="67084-124">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="67084-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="67084-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67084-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="67084-126">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67084-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="67084-127">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67084-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="67084-128">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="67084-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="67084-129">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="67084-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="67084-130">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="67084-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="67084-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="67084-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="67084-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="67084-132">See Also</span></span>
