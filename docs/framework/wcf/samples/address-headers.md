---
title: Hlavičky adresy
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 3bc8512fb2492a7249c81fc33a3c7b83904f1ccd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715232"
---
# <a name="address-headers"></a><span data-ttu-id="a42fe-102">Hlavičky adresy</span><span class="sxs-lookup"><span data-stu-id="a42fe-102">Address Headers</span></span>

<span data-ttu-id="a42fe-103">Ukázka hlaviček adres ukazuje, jak mohou klienti předat parametry odkazu do služby pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a42fe-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="a42fe-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a42fe-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a42fe-105">Specifikace WS-Addressing definuje pojem reference koncového bodu jako způsob, jak adresovat konkrétní koncový bod webové služby.</span><span class="sxs-lookup"><span data-stu-id="a42fe-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="a42fe-106">V WCF jsou odkazy na koncový bod modelovány pomocí `EndpointAddress` třídy – `EndpointAddress` je typ pole Adresa třídy `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="a42fe-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="a42fe-107">Součástí referenčního modelu koncového bodu je, že každý odkaz může mít několik referenčních parametrů, které přidávají dodatečné identifikační informace.</span><span class="sxs-lookup"><span data-stu-id="a42fe-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="a42fe-108">V rámci WCF jsou tyto parametry odkazu modelovány jako instance `AddressHeader` třídy.</span><span class="sxs-lookup"><span data-stu-id="a42fe-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="a42fe-109">V této ukázce klient přidá parametr reference do `EndpointAddress` koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="a42fe-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="a42fe-110">Služba vyhledá tento parametr odkazu a použije jeho hodnotu v logice jeho operace služby Hello.</span><span class="sxs-lookup"><span data-stu-id="a42fe-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="a42fe-111">Klient</span><span class="sxs-lookup"><span data-stu-id="a42fe-111">Client</span></span>

<span data-ttu-id="a42fe-112">Aby mohl klient odeslat odkazový parametr, musí přidat `AddressHeader` do `EndpointAddress` `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="a42fe-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="a42fe-113">Vzhledem k tomu, že třída `EndpointAddress` je neměnná, musí být úprava adresy koncového bodu provedena pomocí `EndpointAddressBuilder` třídy.</span><span class="sxs-lookup"><span data-stu-id="a42fe-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="a42fe-114">Následující kód inicializuje klienta, aby odesílal parametr reference jako součást jeho zprávy.</span><span class="sxs-lookup"><span data-stu-id="a42fe-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="a42fe-115">Kód vytvoří `EndpointAddressBuilder` jako počáteční hodnotu pomocí původní `EndpointAddress`.</span><span class="sxs-lookup"><span data-stu-id="a42fe-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="a42fe-116">Pak přidá nově vytvořenou hlavičku adresy; volání `CreateAddressHeader` vytvoří hlavičku s určitým názvem, oborem názvů a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="a42fe-116">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="a42fe-117">Tady je hodnota "Jan".</span><span class="sxs-lookup"><span data-stu-id="a42fe-117">Here the value is "John".</span></span> <span data-ttu-id="a42fe-118">Po přidání hlavičky do Tvůrce `ToEndpointAddress()` metoda převede (mutable) tvůrce zpátky na (neměnný) adresu koncového bodu, která se přiřadí zpátky do pole Adresa koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="a42fe-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="a42fe-119">Když teď klient volá `Console.WriteLine(client.Hello());`, může služba získat hodnotu tohoto parametru adresy, jak je vidět ve výsledném výstupu klienta.</span><span class="sxs-lookup"><span data-stu-id="a42fe-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="a42fe-120">Server</span><span class="sxs-lookup"><span data-stu-id="a42fe-120">Server</span></span>

<span data-ttu-id="a42fe-121">Implementace `Hello()` operací služby používá aktuální `OperationContext` k zkontrolování hodnot hlaviček v příchozí zprávě.</span><span class="sxs-lookup"><span data-stu-id="a42fe-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

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

<span data-ttu-id="a42fe-122">Kód projde všemi záhlavími příchozí zprávy a hledá hlavičky, které jsou referenčními parametry s konkrétním názvem a.</span><span class="sxs-lookup"><span data-stu-id="a42fe-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="a42fe-123">Když je parametr nalezen, přečte hodnotu parametru a uloží jej do proměnné "ID".</span><span class="sxs-lookup"><span data-stu-id="a42fe-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a42fe-124">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a42fe-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a42fe-125">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a42fe-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a42fe-126">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a42fe-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="a42fe-127">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a42fe-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a42fe-128">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="a42fe-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a42fe-129">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a42fe-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a42fe-130">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="a42fe-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a42fe-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a42fe-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
