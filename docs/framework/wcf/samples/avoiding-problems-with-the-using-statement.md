---
title: Jak se vyhnout problémům s příkazem Using
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd3065a21c1714b0643bfb87b731193d3367352f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="avoiding-problems-with-the-using-statement"></a><span data-ttu-id="d0f04-102">Jak se vyhnout problémům s příkazem Using</span><span class="sxs-lookup"><span data-stu-id="d0f04-102">Avoiding Problems with the Using Statement</span></span>
<span data-ttu-id="d0f04-103">Tento příklad znázorňuje, jak byste neměli používat "použití" příkaz automaticky vyčištění prostředků při použití typový klient jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="d0f04-103">This sample demonstrates how you should not use the C# "using" statement to automatically clean up resources when using a typed client.</span></span> <span data-ttu-id="d0f04-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="d0f04-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="d0f04-105">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="d0f04-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0f04-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d0f04-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d0f04-107">Tento příklad ukazuje dva běžné problémy, ke kterým dochází při používání "použití" příkaz s typem klienty, stejně jako kód, který správně vyčistí po výjimky jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="d0f04-107">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="d0f04-108">"Pomocí" příkazu jazyka C# výsledkem volání `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="d0f04-108">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="d0f04-109">Je to stejné nastavení jako `Close`(), který může vyvolat výjimky, když dojde k chybě sítě.</span><span class="sxs-lookup"><span data-stu-id="d0f04-109">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="d0f04-110">Protože volání `Dispose`() odehrává implicitně se na pravé složené závorce bloku "použití", tento zdroj výjimek je pravděpodobně přejdete unnoticed i uživatelé psaní kódu a čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="d0f04-110">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="d0f04-111">To představuje potenciální zdroj chyby aplikace.</span><span class="sxs-lookup"><span data-stu-id="d0f04-111">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="d0f04-112">První problém, zobrazené `DemonstrateProblemUsingCanThrow` metodou, je, že pravé složené závorce výjimku a kód po pravé složené závorce nepracuje:</span><span class="sxs-lookup"><span data-stu-id="d0f04-112">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="d0f04-113">I v případě, že nic uvnitř použití blokovat vyvolá výjimku nebo uvnitř použití všechny výjimky jsou zachyceny bloku, `Console.Writeline` nemusí dojít, protože implicitní `Dispose`volání () na pravé složené závorce může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="d0f04-113">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="d0f04-114">Druhý problém, zobrazené `DemonstrateProblemUsingCanThrowAndMask` metodou, je jiná vyplývá pravé složené závorce došlo k výjimce:</span><span class="sxs-lookup"><span data-stu-id="d0f04-114">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="d0f04-115">Protože `Dispose`() se provádí v bloku "finally" `ApplicationException` je nikdy neuvidí mimo použití blokování, pokud `Dispose`() se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="d0f04-115">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="d0f04-116">Pokud kód mimo musí vědět o tom, kdy `ApplicationException` dojde, "pomocí" konstrukce může způsobit problémy s nástrojem maskování výjimku.</span><span class="sxs-lookup"><span data-stu-id="d0f04-116">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="d0f04-117">Nakonec ukazuje, jak vyčistit správně při výskytu výjimek v ukázce `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="d0f04-117">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="d0f04-118">Tato služba využívá bloku try/catch k hlášení chyb a volání `Abort`.</span><span class="sxs-lookup"><span data-stu-id="d0f04-118">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="d0f04-119">Najdete v článku [očekává výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) ukázku další podrobnosti o zachytávání výjimek z volání klienta.</span><span class="sxs-lookup"><span data-stu-id="d0f04-119">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
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
>  <span data-ttu-id="d0f04-120">Pomocí příkazu a ServiceHost: mnoho samoobslužné hostování aplikací trochu více než hostování služby a ServiceHost.Close zřídka vyvolá výjimku, abyste takové aplikace můžete bezpečně používat na pomocí příkaz s hostiteli služby.</span><span class="sxs-lookup"><span data-stu-id="d0f04-120">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="d0f04-121">Upozorňujeme však, že můžete vyvolat ServiceHost.Close `CommunicationException`, takže pokud vaše aplikace bude pokračovat po zavření ServiceHost, neměli byste na pomocí prohlášení a postupujte podle vzoru dříve zadané.</span><span class="sxs-lookup"><span data-stu-id="d0f04-121">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="d0f04-122">Když spustíte ukázku, zobrazí se v okně konzoly klienta odpovědí na operaci a výjimky.</span><span class="sxs-lookup"><span data-stu-id="d0f04-122">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="d0f04-123">Klient proces spouští tři scénáře, každý z které pokusy o volání `Divide`.</span><span class="sxs-lookup"><span data-stu-id="d0f04-123">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="d0f04-124">První scénář ukazuje kód přeskočeno z důvodu výjimku z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="d0f04-124">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="d0f04-125">Druhý scénář ukazuje výjimku důležité maskovaného kvůli výjimku z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="d0f04-125">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="d0f04-126">Třetí scénář ukazuje správné vyčištění.</span><span class="sxs-lookup"><span data-stu-id="d0f04-126">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="d0f04-127">Je očekávaný výstup z procesu klienta:</span><span class="sxs-lookup"><span data-stu-id="d0f04-127">The expected output from the client process is:</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0f04-128">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d0f04-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d0f04-129">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0f04-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d0f04-130">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0f04-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d0f04-131">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0f04-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0f04-132">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d0f04-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0f04-133">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d0f04-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d0f04-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d0f04-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0f04-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d0f04-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="d0f04-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0f04-136">See Also</span></span>
