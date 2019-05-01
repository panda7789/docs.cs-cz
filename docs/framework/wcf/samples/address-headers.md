---
title: Hlavičky adresy
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 4ccb309178251b32068d6cdbb81874322f991bb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002947"
---
# <a name="address-headers"></a><span data-ttu-id="905e2-102">Hlavičky adresy</span><span class="sxs-lookup"><span data-stu-id="905e2-102">Address Headers</span></span>

<span data-ttu-id="905e2-103">Hlavičky adresy ukázka demonstruje, jak klienti můžete předávat parametry referenční dokumentace ke službě pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="905e2-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="905e2-104">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="905e2-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="905e2-105">Specifikace WS-Addressing koncept odkazem na koncový bod jako způsob, jak vyřešit konkrétní koncový bod webové služby.</span><span class="sxs-lookup"><span data-stu-id="905e2-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="905e2-106">Ve službě WCF, jsou modelovány pomocí koncového bodu odkazy `EndpointAddress` class - `EndpointAddress` je typ pole adresu `ServiceEndpoint` třídy.</span><span class="sxs-lookup"><span data-stu-id="905e2-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="905e2-107">Referenční model koncový bod je, že každý odkaz můžete provést některé odkaz parametry, které přidávají další identifikační údaje.</span><span class="sxs-lookup"><span data-stu-id="905e2-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="905e2-108">Ve službě WCF, jsou tyto parametry odkazů nemodelují jako instance `AddressHeader` třídy.</span><span class="sxs-lookup"><span data-stu-id="905e2-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="905e2-109">V této ukázce klienta přidá odkaz na parametr, aby `EndpointAddress` koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="905e2-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="905e2-110">Služba hledá tento odkaz na parametr a použije její hodnotu v logice jeho operace služby "Hello".</span><span class="sxs-lookup"><span data-stu-id="905e2-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="905e2-111">Klient</span><span class="sxs-lookup"><span data-stu-id="905e2-111">Client</span></span>

<span data-ttu-id="905e2-112">Pro klienta k odesílání referenční parametr, musíte přidat `AddressHeader` k `EndpointAddress` z `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="905e2-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="905e2-113">Protože `EndpointAddress` třída je neměnný, je nutné provést úpravu adresy koncového bodu pomocí `EndpointAddressBuilder` třídy.</span><span class="sxs-lookup"><span data-stu-id="905e2-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="905e2-114">Následující kód inicializuje klientovi umožní odeslat referenční parametr jako součást její zprávy.</span><span class="sxs-lookup"><span data-stu-id="905e2-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="905e2-115">Kód vytvoří `EndpointAddressBuilder` pomocí původní `EndpointAddress` jako počáteční hodnota.</span><span class="sxs-lookup"><span data-stu-id="905e2-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="905e2-116">Potom přidá hlavičku adresu nově vytvořeného; volání `CreateAddressHeader` vytvoří hlavičku s konkrétním názvem, obor názvů a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="905e2-116">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="905e2-117">V tomto poli hodnota je "John".</span><span class="sxs-lookup"><span data-stu-id="905e2-117">Here the value is "John".</span></span> <span data-ttu-id="905e2-118">Po přidání záhlaví do Tvůrce `ToEndpointAddress()` metoda převede zpátky do adresy koncového bodu (neměnné), které je přiřazeno zpět do pole adresy koncový bod klienta (proměnlivé) Tvůrce.</span><span class="sxs-lookup"><span data-stu-id="905e2-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="905e2-119">Když klient teď volá `Console.WriteLine(client.Hello());`, služba je schopná k získání hodnoty tohoto parametru adresu, jak je vidět ve výsledném výstupu z klienta.</span><span class="sxs-lookup"><span data-stu-id="905e2-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="905e2-120">Server</span><span class="sxs-lookup"><span data-stu-id="905e2-120">Server</span></span>

<span data-ttu-id="905e2-121">Provádění operace služby `Hello()` používá aktuální `OperationContext` ke kontrole hodnot hlavičky v příchozí zprávě.</span><span class="sxs-lookup"><span data-stu-id="905e2-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

```csharp
string id = null;
// look at headers on incoming message
for (int i = 0;
     i < OperationContext.Current.IncomingMessageHeaders.Count;
     ++i)
{
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];
    // for any reference parameters with the correct name & namespace
    if (h.IsReferenceParameter &&
        h.Name == IDName &&
        h.Namespace == IDNamespace)
    {
        // read the value of that header
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);
        id = xr.ReadElementContentAsString();
    }
}
return "Hello, " + id;
```

<span data-ttu-id="905e2-122">Kód Iteruje přes všechny hlavičky v příchozí zprávě, hledá hlavičky, které jsou parametry odkazu s konkrétním názvem a.</span><span class="sxs-lookup"><span data-stu-id="905e2-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="905e2-123">Po nalezení parametr přečte hodnotu parametru a uloží jej do proměnné "id".</span><span class="sxs-lookup"><span data-stu-id="905e2-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="905e2-124">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="905e2-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="905e2-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="905e2-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="905e2-126">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="905e2-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="905e2-127">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="905e2-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="905e2-128">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="905e2-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="905e2-129">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="905e2-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="905e2-130">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="905e2-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="905e2-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="905e2-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
