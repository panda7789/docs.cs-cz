---
title: Hostování IIS pomocí vloženého kódu
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 862ae61112db475825901f7c3f1d5127b384bb22
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711613"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="176c8-102">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="176c8-102">IIS Hosting Using Inline Code</span></span>

<span data-ttu-id="176c8-103">Tato ukázka předvádí, jak implementovat službu hostovanou službou Internetová informační služba (IIS), kde je kód služby obsažen v souboru. svc a je kompilován na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="176c8-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="176c8-104">Kód služby se dá taky implementovat přímo ve zdrojových souborech, které se nacházejí v adresáři aplikace \ App_Code, nebo zkompilované do sestavení nasazeného v \Bin.</span><span class="sxs-lookup"><span data-stu-id="176c8-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="176c8-105">Tato ukázka tyto techniky předvádí.</span><span class="sxs-lookup"><span data-stu-id="176c8-105">This sample does not demonstrate these techniques.</span></span>

> [!NOTE]
> <span data-ttu-id="176c8-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="176c8-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="176c8-107">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="176c8-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="176c8-108">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="176c8-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="176c8-109">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="176c8-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="176c8-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="176c8-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

<span data-ttu-id="176c8-111">Ukázka předvádí typickou službu, která implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="176c8-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="176c8-112">Služba je hostována službou IIS a kód služby je zcela obsažen v souboru Service. svc.</span><span class="sxs-lookup"><span data-stu-id="176c8-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="176c8-113">Služba je hostovaná a kompilovaná na vyžádání první zprávou odeslanou službě.</span><span class="sxs-lookup"><span data-stu-id="176c8-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="176c8-114">Není nutná žádná předkompilace.</span><span class="sxs-lookup"><span data-stu-id="176c8-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="176c8-115">Služba implementuje kontrakt `ICalculator`, jak je definován v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="176c8-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="176c8-116">Implementace služby vypočítá a vrátí příslušný výsledek.</span><span class="sxs-lookup"><span data-stu-id="176c8-116">The service implementation calculates and returns the appropriate result.</span></span>

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="176c8-117">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="176c8-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="176c8-118">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="176c8-118">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="176c8-119">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="176c8-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="176c8-120">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="176c8-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="176c8-121">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="176c8-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="176c8-122">Po sestavení řešení spusťte soubor Setup. bat a nastavte aplikaci ServiceModelSamples ve službě IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="176c8-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="176c8-123">Adresář ServiceModelSamples by se teď měl zobrazit jako aplikace IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="176c8-123">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="176c8-124">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="176c8-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="176c8-125">Příklad, jak vytvořit klientskou aplikaci, která může zavolat tuto službu, naleznete v tématu [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="176c8-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="176c8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="176c8-126">See also</span></span>

- [<span data-ttu-id="176c8-127">Hostování technologie AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="176c8-127">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
