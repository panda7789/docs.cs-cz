---
title: Použít zavřít a přerušení k uvolnění prostředků klienta WCF
description: Dispose může selhat a vyvolání výjimky, pokud se nezdaří v síti. To může způsobit nežádoucí chování. Místo toho použijte zavřít a přerušení k uvolnění prostředků klienta, když k chybě sítě.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: d37ad9d2277fea2656311a5a1f57d51343d10d89
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147213"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="7a798-105">Zavřít a přerušení uvolnění prostředků bezpečně vynechali síťová připojení</span><span class="sxs-lookup"><span data-stu-id="7a798-105">Close and Abort release resources safely when network connections have dropped</span></span>
<span data-ttu-id="7a798-106">Tento příklad ukazuje použití `Close` a `Abort` metody pro vyčištění prostředků při použití typu klienta.</span><span class="sxs-lookup"><span data-stu-id="7a798-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="7a798-107">`using` Příkaz způsobí, že výjimky při připojení k síti není robustní.</span><span class="sxs-lookup"><span data-stu-id="7a798-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="7a798-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="7a798-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="7a798-109">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7a798-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a798-110">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7a798-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7a798-111">Tento příklad ukazuje dvě běžné problémy, ke kterým dochází při použití jazyka C# "" příkaz s typem klienty, stejně jako kód, který správně vyčištění po výjimkách.</span><span class="sxs-lookup"><span data-stu-id="7a798-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="7a798-112">Příkaz "using" C# výsledkem volání `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="7a798-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="7a798-113">To je stejný jako `Close`(), což může vyvolat výjimky, když dojde k chybě sítě.</span><span class="sxs-lookup"><span data-stu-id="7a798-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="7a798-114">Protože volání `Dispose`() se implicitně odehrává na pravou složenou závorku "pomocí" bloku, tento zdroj výjimky je pravděpodobně přejít unnoticed i uživatelé psaní kódu a čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="7a798-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="7a798-115">Reprezentuje možným zdrojem chyby aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a798-115">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="7a798-116">Prvním problémem, ukazuje `DemonstrateProblemUsingCanThrow` metoda, je, že pravou složenou závorku výjimku a kód po pravé složené závorce nespustí:</span><span class="sxs-lookup"><span data-stu-id="7a798-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="7a798-117">I když nic uvnitř using blokovat útoky DoS vyvolá výjimku nebo uvnitř using všechny výjimky jsou zachyceny bloku, `Console.Writeline` nemusí dojít, protože implicitní `Dispose`volání () na pravé složené závorce může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="7a798-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="7a798-118">Druhý problém ukazuje `DemonstrateProblemUsingCanThrowAndMask` metoda, je jiný nepřímo pravou složenou závorku, došlo k výjimce:</span><span class="sxs-lookup"><span data-stu-id="7a798-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="7a798-119">Protože `Dispose`() nastane uvnitř bloku "klíčové slovo finally" `ApplicationException` nikdy se neprohlédlo mimo using blokovat, pokud `Dispose`() se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7a798-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="7a798-120">Pokud kód mimo musí vědět o tom, kdy `ApplicationException` dojde, "using" konstruktoru může způsobit problémy pomocí jejich maskování této výjimky.</span><span class="sxs-lookup"><span data-stu-id="7a798-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="7a798-121">Nakonec vzorek ukazuje, jak vyčistit správně při výskytu výjimek v `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="7a798-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="7a798-122">Tento mechanismus využívá bloku try/catch k nahlášení chyb a volání `Abort`.</span><span class="sxs-lookup"><span data-stu-id="7a798-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="7a798-123">Zobrazit [očekávané výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) ukázka podrobné informace o zachycení výjimky z volání klienta.</span><span class="sxs-lookup"><span data-stu-id="7a798-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
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
>  <span data-ttu-id="7a798-124">Použití příkazu a hostitel služby: Samoobslužné hostování aplikací v mnoha trochu více než hostování služby a ServiceHost.Close zřídka vyvolá výjimku, takže tyto aplikace můžete bezpečně použít na pomocí příkazu s hostitele ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="7a798-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="7a798-125">Však být vědomi, že může vyvolat ServiceHost.Close `CommunicationException`, takže pokud vaše aplikace bude pokračovat až po zavření hostitele ServiceHost, měli byste se vyhnout pomocí příkazu a postupujte podle vzoru předem.</span><span class="sxs-lookup"><span data-stu-id="7a798-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="7a798-126">Při spuštění ukázky operace odpovědi a výjimky jsou zobrazeny v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="7a798-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="7a798-127">Klient proces spouští tři scénáře, každý z které pokusy o volání `Divide`.</span><span class="sxs-lookup"><span data-stu-id="7a798-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="7a798-128">První scénář ukazuje kód přeskočeno z důvodu výjimky z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="7a798-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="7a798-129">Druhý scénář ukazuje důležité výjimku z důvodu výjimky z maskovaného `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="7a798-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="7a798-130">Třetí scénář ukazuje správné vyčištění.</span><span class="sxs-lookup"><span data-stu-id="7a798-130">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="7a798-131">Očekávaný výstup z procesu klienta je:</span><span class="sxs-lookup"><span data-stu-id="7a798-131">The expected output from the client process is:</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7a798-132">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="7a798-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7a798-133">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a798-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7a798-134">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a798-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7a798-135">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a798-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7a798-136">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="7a798-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7a798-137">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7a798-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7a798-138">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7a798-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a798-139">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7a798-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="7a798-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a798-140">See Also</span></span>
