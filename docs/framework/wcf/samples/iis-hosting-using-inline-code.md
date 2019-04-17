---
title: Hostování IIS pomocí vloženého kódu
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 8e401d6ce73c036188d13f40c1293abd1f0de58c
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613171"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="8788f-102">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="8788f-102">IIS Hosting Using Inline Code</span></span>

<span data-ttu-id="8788f-103">Tato ukázka předvádí, jak implementovat služba hostovaná podle Internetové informační služby (IIS), kde je kód služby jsou obsaženy v řádku v souboru .svc a je zkompilován na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="8788f-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="8788f-104">Kód služby je možné implementovat také přímo do souborů se zdrojovým kódem v adresáři \App_Code aplikace nebo zkompilovány do sestavení nasazeno v \bin.</span><span class="sxs-lookup"><span data-stu-id="8788f-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="8788f-105">Tento příklad neukazuje těchto technik.</span><span class="sxs-lookup"><span data-stu-id="8788f-105">This sample does not demonstrate these techniques.</span></span>

> [!NOTE]
> <span data-ttu-id="8788f-106">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8788f-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8788f-107">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="8788f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8788f-108">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8788f-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8788f-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8788f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8788f-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8788f-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

<span data-ttu-id="8788f-111">Vzorek ukazuje typické služba, která implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="8788f-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8788f-112">Služba je hostována ve službě IIS a kódu služby je zcela obsažený v souboru Service.svc.</span><span class="sxs-lookup"><span data-stu-id="8788f-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="8788f-113">Služba aktivována hostitele je a kompilovaná první zpráva odeslaná do služby na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="8788f-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="8788f-114">Neexistuje žádné předkompilace nezbytné.</span><span class="sxs-lookup"><span data-stu-id="8788f-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="8788f-115">Implementuje služby `ICalculator` smlouvy, jak je definováno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8788f-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>

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

<span data-ttu-id="8788f-116">Implementace služby vypočítá a vrátí odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="8788f-116">The service implementation calculates and returns the appropriate result.</span></span>

```svc
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>
```

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

<span data-ttu-id="8788f-117">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="8788f-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8788f-118">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="8788f-118">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8788f-119">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="8788f-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8788f-120">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8788f-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8788f-121">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8788f-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="8788f-122">Po řešení je sestavený Build, spusťte setup.bat nastavit aplikaci ServiceModelSamples [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8788f-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="8788f-123">Adresář ServiceModelSamples by se měla objevit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="8788f-123">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>

4. <span data-ttu-id="8788f-124">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8788f-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="8788f-125">Příklad o tom, jak vytvořit klientskou aplikaci, která může volat tuto službu, naleznete v tématu [jak: Vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="8788f-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8788f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8788f-126">See also</span></span>

- [<span data-ttu-id="8788f-127">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="8788f-127">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
