---
title: Vytvoření postupu kanálu
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 2aa44c4ef274fa548d490b0d8a648457a7b1e03b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600656"
---
# <a name="channel-factory"></a><span data-ttu-id="a5705-102">Vytvoření postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="a5705-102">Channel Factory</span></span>

<span data-ttu-id="a5705-103">Tato ukázka předvádí, jak může klientská aplikace vytvořit kanál s <xref:System.ServiceModel.ChannelFactory> třídou namísto vygenerovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="a5705-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="a5705-104">Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a5705-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="a5705-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a5705-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a5705-106">Tato ukázka používá <xref:System.ServiceModel.ChannelFactory%601> třídu k vytvoření kanálu pro koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="a5705-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="a5705-107">Chcete-li vytvořit kanál pro koncový bod služby, vygenerujete typ klienta pomocí nástroje pro tvorbu [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) a vytvoříte instanci generovaného typu.</span><span class="sxs-lookup"><span data-stu-id="a5705-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="a5705-108">Kanál můžete také vytvořit pomocí <xref:System.ServiceModel.ChannelFactory%601> třídy, jak je znázorněno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="a5705-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="a5705-109">Služba vytvořená následujícím ukázkovým kódem je shodná se službou v [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a5705-109">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="a5705-110">Pokud tuto ukázku spouštíte ve scénáři více počítačů, je nutné v předchozím kódu nahradit "localhost" úplným názvem počítače, na kterém je spuštěna služba.</span><span class="sxs-lookup"><span data-stu-id="a5705-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="a5705-111">Tato ukázka nepoužívá konfiguraci k nastavení adresy koncového bodu, takže to je nutné provést v kódu.</span><span class="sxs-lookup"><span data-stu-id="a5705-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="a5705-112">Po vytvoření kanálu mohou být operace služby vyvolány stejně jako u vygenerovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="a5705-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="a5705-113">Chcete-li kanál zavřít, musí být nejprve převeden na <xref:System.ServiceModel.IClientChannel> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a5705-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="a5705-114">Důvodem je, že kanál jak je vygenerován, je deklarován v klientské aplikaci pomocí `ICalculator` rozhraní, které má metody jako `Add` a nikoli `Subtract` `Close` .</span><span class="sxs-lookup"><span data-stu-id="a5705-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="a5705-115">`Close`Metoda pochází z <xref:System.ServiceModel.ICommunicationObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a5705-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="a5705-116">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a5705-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a5705-117">V okně klienta stiskněte klávesu ENTER, aby se ukončila klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5705-117">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a5705-118">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a5705-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a5705-119">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5705-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a5705-120">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5705-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="a5705-121">Všimněte si, že tato ukázka nepovoluje publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="a5705-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="a5705-122">Aby bylo možné znovu vygenerovat typ klienta, je třeba nejprve povolit publikování metadat pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="a5705-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="a5705-123">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5705-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="a5705-124">Spuštění ukázkového počítače</span><span class="sxs-lookup"><span data-stu-id="a5705-124">To run the sample cross machine</span></span>

1. <span data-ttu-id="a5705-125">Nahraďte "localhost" v následujícím kódu plně kvalifikovaným názvem počítače, na kterém je spuštěna služba.</span><span class="sxs-lookup"><span data-stu-id="a5705-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="a5705-126">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="a5705-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5705-127">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a5705-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a5705-128">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="a5705-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5705-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a5705-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
