---
title: "Hostování IIS pomocí vloženého kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc1e17d027aece31bf6313a23799dc2d18af3ee7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="11039-102">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="11039-102">IIS Hosting Using Inline Code</span></span>
<span data-ttu-id="11039-103">Tento příklad ukazuje, jak implementovat službě hostované pomocí Internetové informační služby (IIS), kde je kód služby jsou obsaženy v řádku v souboru .svc a kompiluje na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="11039-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="11039-104">Kódu služby můžete implementovat také přímo v soubory zdrojového kódu umístěný v adresáři aplikace \App_Code nebo zkompilovat do sestavení nasazeno v \bin.</span><span class="sxs-lookup"><span data-stu-id="11039-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="11039-105">Tato ukázka nepředvádí těchto postupů.</span><span class="sxs-lookup"><span data-stu-id="11039-105">This sample does not demonstrate these techniques.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11039-106">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="11039-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11039-107">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="11039-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="11039-108">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="11039-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11039-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="11039-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11039-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="11039-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 <span data-ttu-id="11039-111">Ukázka ukazuje typické služba, která implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="11039-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="11039-112">Služba je hostovaná ve službě IIS a kódu služby je zcela obsažen v souboru Service.svc.</span><span class="sxs-lookup"><span data-stu-id="11039-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="11039-113">Služba aktivuje hostitele je a zkompilují na vyžádání první zprávou odeslanou ke službě.</span><span class="sxs-lookup"><span data-stu-id="11039-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="11039-114">Neexistuje žádné předkompilaci potřeby.</span><span class="sxs-lookup"><span data-stu-id="11039-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="11039-115">Implementuje služby `ICalculator` smlouvy definovaným v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="11039-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>  
  
```  
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
  
 <span data-ttu-id="11039-116">Implementace služby vypočítá a vrátí odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="11039-116">The service implementation calculates and returns the appropriate result.</span></span>  
  
```  
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
…  
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
  
 <span data-ttu-id="11039-117">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="11039-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="11039-118">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="11039-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="11039-119">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="11039-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="11039-120">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="11039-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="11039-121">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="11039-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="11039-122">Po vytvoření řešení, spusťte setup.bat nastavit aplikaci ServiceModelSamples v [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11039-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="11039-123">Adresář ServiceModelSamples by se měla zobrazit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="11039-123">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="11039-124">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="11039-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="11039-125">Příklad o tom, jak vytvořit klientskou aplikaci, které můžete volat tuto službu, naleznete v části [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="11039-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11039-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="11039-126">See Also</span></span>  
 [<span data-ttu-id="11039-127">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="11039-127">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
