---
title: Jak se vyhnout problémům s příkazem Using
ms.date: 03/30/2017
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 2c7534a56b2cc8fdc674242e135d70bec7f5017a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394695"
---
# <a name="avoiding-problems-with-the-using-statement"></a><span data-ttu-id="e32b8-102">Jak se vyhnout problémům s příkazem Using</span><span class="sxs-lookup"><span data-stu-id="e32b8-102">Avoiding Problems with the Using Statement</span></span>
<span data-ttu-id="e32b8-103">Tato ukázka předvádí, jak byste neměli používat "" příkaz using automaticky vyčistit prostředky, při použití typový klient C#.</span><span class="sxs-lookup"><span data-stu-id="e32b8-103">This sample demonstrates how you should not use the C# "using" statement to automatically clean up resources when using a typed client.</span></span> <span data-ttu-id="e32b8-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="e32b8-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e32b8-105">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="e32b8-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e32b8-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e32b8-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e32b8-107">Tento příklad ukazuje dvě běžné problémy, ke kterým dochází při použití jazyka C# "" příkaz s typem klienty, stejně jako kód, který správně vyčištění po výjimkách.</span><span class="sxs-lookup"><span data-stu-id="e32b8-107">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="e32b8-108">Příkaz "using" C# výsledkem volání `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="e32b8-108">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="e32b8-109">To je stejný jako `Close`(), což může vyvolat výjimky, když dojde k chybě sítě.</span><span class="sxs-lookup"><span data-stu-id="e32b8-109">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="e32b8-110">Protože volání `Dispose`() se implicitně odehrává na pravou složenou závorku "pomocí" bloku, tento zdroj výjimky je pravděpodobně přejít unnoticed i uživatelé psaní kódu a čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="e32b8-110">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="e32b8-111">Reprezentuje možným zdrojem chyby aplikace.</span><span class="sxs-lookup"><span data-stu-id="e32b8-111">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="e32b8-112">Prvním problémem, ukazuje `DemonstrateProblemUsingCanThrow` metoda, je, že pravou složenou závorku výjimku a kód po pravé složené závorce nespustí:</span><span class="sxs-lookup"><span data-stu-id="e32b8-112">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="e32b8-113">I když nic uvnitř using blokovat útoky DoS vyvolá výjimku nebo uvnitř using všechny výjimky jsou zachyceny bloku, `Console.Writeline` nemusí dojít, protože implicitní `Dispose`volání () na pravé složené závorce může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="e32b8-113">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="e32b8-114">Druhý problém ukazuje `DemonstrateProblemUsingCanThrowAndMask` metoda, je jiný nepřímo pravou složenou závorku, došlo k výjimce:</span><span class="sxs-lookup"><span data-stu-id="e32b8-114">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="e32b8-115">Protože `Dispose`() nastane uvnitř bloku "klíčové slovo finally" `ApplicationException` nikdy se neprohlédlo mimo using blokovat, pokud `Dispose`() se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e32b8-115">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="e32b8-116">Pokud kód mimo musí vědět o tom, kdy `ApplicationException` dojde, "using" konstruktoru může způsobit problémy pomocí jejich maskování této výjimky.</span><span class="sxs-lookup"><span data-stu-id="e32b8-116">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="e32b8-117">Nakonec vzorek ukazuje, jak vyčistit správně při výskytu výjimek v `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="e32b8-117">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="e32b8-118">Tento mechanismus využívá bloku try/catch k nahlášení chyb a volání `Abort`.</span><span class="sxs-lookup"><span data-stu-id="e32b8-118">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="e32b8-119">Zobrazit [očekávané výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) ukázka podrobné informace o zachycení výjimky z volání klienta.</span><span class="sxs-lookup"><span data-stu-id="e32b8-119">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="e32b8-120">Pomocí příkazu a hostitel služby: mnoho samoobslužné hostování aplikací trochu více než hostování služby a ServiceHost.Close zřídka vyvolá výjimku, takže tyto aplikace můžete bezpečně použít na pomocí příkazu s hostitele ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="e32b8-120">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="e32b8-121">Však být vědomi, že může vyvolat ServiceHost.Close `CommunicationException`, takže pokud vaše aplikace bude pokračovat až po zavření hostitele ServiceHost, měli byste se vyhnout pomocí příkazu a postupujte podle vzoru předem.</span><span class="sxs-lookup"><span data-stu-id="e32b8-121">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="e32b8-122">Při spuštění ukázky operace odpovědi a výjimky jsou zobrazeny v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="e32b8-122">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="e32b8-123">Klient proces spouští tři scénáře, každý z které pokusy o volání `Divide`.</span><span class="sxs-lookup"><span data-stu-id="e32b8-123">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="e32b8-124">První scénář ukazuje kód přeskočeno z důvodu výjimky z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="e32b8-124">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="e32b8-125">Druhý scénář ukazuje důležité výjimku z důvodu výjimky z maskovaného `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="e32b8-125">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="e32b8-126">Třetí scénář ukazuje správné vyčištění.</span><span class="sxs-lookup"><span data-stu-id="e32b8-126">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="e32b8-127">Očekávaný výstup z procesu klienta je:</span><span class="sxs-lookup"><span data-stu-id="e32b8-127">The expected output from the client process is:</span></span>  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e32b8-128">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="e32b8-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e32b8-129">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32b8-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e32b8-130">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32b8-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e32b8-131">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32b8-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e32b8-132">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e32b8-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e32b8-133">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e32b8-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e32b8-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e32b8-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e32b8-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e32b8-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="e32b8-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e32b8-136">See Also</span></span>
