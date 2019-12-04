---
title: Použití metod Close a Abort k uvolnění prostředků klienta WCF
description: Dispose může selhat a vyvolat výjimky, pokud dojde k selhání sítě. To může způsobit nežádoucí chování. Místo toho použijte příkaz Zavřít a přerušit k uvolnění prostředků klienta, pokud se síť nezdařila.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 38861252a470f71a6fa88554e289344e2918d710
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715324"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="7315e-105">V případě, že jsou síťová připojení vyřazena, uzavřete a přerušit uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="7315e-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="7315e-106">Tato ukázka demonstruje použití metod `Close` a `Abort` k vyčištění prostředků při použití typového klienta.</span><span class="sxs-lookup"><span data-stu-id="7315e-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="7315e-107">Příkaz `using` způsobuje výjimky v případě nerobustního síťového připojení.</span><span class="sxs-lookup"><span data-stu-id="7315e-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="7315e-108">Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="7315e-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="7315e-109">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="7315e-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="7315e-110">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7315e-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="7315e-111">Tato ukázka ukazuje dva běžné problémy, ke kterým dochází při použití příkazu C# "using" se zadanými klienty, jakož i kódu, který správně čistí po výjimkách.</span><span class="sxs-lookup"><span data-stu-id="7315e-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="7315e-112">C# Příkaz using má za následek volání `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="7315e-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="7315e-113">To je stejné jako `Close`(), což může vyvolat výjimky při výskytu chyby sítě.</span><span class="sxs-lookup"><span data-stu-id="7315e-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="7315e-114">Vzhledem k tomu, že volání `Dispose`() probíhá implicitně na pravé závorce bloku "using", tento zdroj výjimek je pravděpodobně neupozorněn na uživatele, kteří píší kód a čtou kód.</span><span class="sxs-lookup"><span data-stu-id="7315e-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="7315e-115">To představuje potenciální zdroj chyb aplikace.</span><span class="sxs-lookup"><span data-stu-id="7315e-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="7315e-116">První problém, znázorněný v metodě `DemonstrateProblemUsingCanThrow`, je, že pravá složená závorka vyvolá výjimku a kód po pravé složené závorce nespustí:</span><span class="sxs-lookup"><span data-stu-id="7315e-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="7315e-117">I v případě, že nic uvnitř bloku using vyvolá výjimku nebo jsou zachyceny všechny výjimky uvnitř bloku using, `Console.WriteLine` pravděpodobně neproběhne, protože volání implicitního `Dispose`() na pravé závorce může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="7315e-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="7315e-118">Druhý problém, znázorněný v metodě `DemonstrateProblemUsingCanThrowAndMask`, je další příčinou pravé složené závorky, která vyvolává výjimku:</span><span class="sxs-lookup"><span data-stu-id="7315e-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="7315e-119">Vzhledem k tomu, že se `Dispose`() nachází uvnitř bloku "finally", `ApplicationException` se nikdy nezobrazuje vně bloku using, pokud `Dispose`() dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="7315e-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="7315e-120">Pokud kód mimo musí znát, kdy k `ApplicationException` dojde, může konstrukce "using" způsobit problémy pomocí maskování této výjimky.</span><span class="sxs-lookup"><span data-stu-id="7315e-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="7315e-121">Nakonec Ukázka ukazuje, jak správně vyčistit při výskytu výjimek v `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="7315e-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="7315e-122">K nahlášení chyb a volání `Abort`se používá blok try/catch.</span><span class="sxs-lookup"><span data-stu-id="7315e-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="7315e-123">Další podrobnosti o zachycování výjimek od klientských volání najdete v ukázce [očekávaných výjimek](../../../../docs/framework/wcf/samples/expected-exceptions.md) .</span><span class="sxs-lookup"><span data-stu-id="7315e-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

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
> <span data-ttu-id="7315e-124">Příkaz using a Třída ServiceHost: mnoho aplikací pro samoobslužné hostování má málo větší počet než hostitel a služba a třídu ServiceHost. zavření zřídka vyvolá výjimku, takže takové aplikace mohou bezpečně používat příkaz using s použitím třídy ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="7315e-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="7315e-125">Upozorňujeme však, že Třída ServiceHost. Close může vyvolat `CommunicationException`, takže pokud vaše aplikace po zavření hostitele ServiceHost pokračuje, měli byste se vyhnout příkazu Using a postupovat podle výše uvedeného vzoru.</span><span class="sxs-lookup"><span data-stu-id="7315e-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="7315e-126">Při spuštění ukázky se v okně konzoly klienta zobrazí odezvy operace a výjimky.</span><span class="sxs-lookup"><span data-stu-id="7315e-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="7315e-127">Proces klienta spouští tři scénáře, z nichž každý se pokusí volat `Divide`.</span><span class="sxs-lookup"><span data-stu-id="7315e-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="7315e-128">První scénář ukazuje přeskočení kódu z důvodu výjimky z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="7315e-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="7315e-129">Druhý scénář ukazuje, že důležitá výjimka je maskována z důvodu výjimky z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="7315e-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="7315e-130">Třetí scénář demonstruje správné vyčištění.</span><span class="sxs-lookup"><span data-stu-id="7315e-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="7315e-131">Očekávaný výstup z klientského procesu je:</span><span class="sxs-lookup"><span data-stu-id="7315e-131">The expected output from the client process is:</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7315e-132">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7315e-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7315e-133">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7315e-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="7315e-134">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7315e-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="7315e-135">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7315e-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7315e-136">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="7315e-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7315e-137">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="7315e-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7315e-138">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="7315e-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7315e-139">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7315e-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
