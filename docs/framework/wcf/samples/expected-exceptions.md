---
title: Očekávané výjimky
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 3add9faa9a07249639c1ff3e83469d0634008472
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317087"
---
# <a name="expected-exceptions"></a><span data-ttu-id="6937d-102">Očekávané výjimky</span><span class="sxs-lookup"><span data-stu-id="6937d-102">Expected Exceptions</span></span>
<span data-ttu-id="6937d-103">Tento příklad ukazuje, jak zachytit očekávané výjimky, při použití typu klienta.</span><span class="sxs-lookup"><span data-stu-id="6937d-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="6937d-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="6937d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="6937d-105">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="6937d-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6937d-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="6937d-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6937d-107">Tato ukázka předvádí, zachycení a zpracování dva typy očekávané výjimky, které opravte programy musí zpracovat: `TimeoutException` a `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="6937d-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="6937d-108">Výjimky, které jsou vyvolány z metody komunikace klienta Windows Communication Foundation (WCF) jsou očekávané nebo neočekávané.</span><span class="sxs-lookup"><span data-stu-id="6937d-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="6937d-109">Neočekávané výjimky zahrnují katastrofických selhání jako `OutOfMemoryException` a programové chyby, jako jsou `ArgumentNullException` nebo `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="6937d-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="6937d-110">Obvykle se nedají užitečné pro zpracování neočekávaných chyb, takže obvykle že při volání metody komunikace klienta WCF, neměli byste je zachytit.</span><span class="sxs-lookup"><span data-stu-id="6937d-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="6937d-111">Očekávané výjimky z metody komunikace na klienta WCF zahrnují `TimeoutException`, `CommunicationException`, a všechny odvozené třídy `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="6937d-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="6937d-112">Ty naznačují problém při komunikaci, která může bezpečně ošetřit přerušení klienta WCF a hlášení selhání komunikace.</span><span class="sxs-lookup"><span data-stu-id="6937d-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="6937d-113">Protože vnější faktory mohou způsobit tyto chyby v jakékoli aplikaci, správné aplikace musí zachytit tyto výjimky a obnovit, když k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="6937d-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="6937d-114">Existuje několik odvozené třídy `CommunicationException` , který může klient vyvolat.</span><span class="sxs-lookup"><span data-stu-id="6937d-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="6937d-115">V některých případech může aplikace také catch některé z nich proveďte zvláštní zpracování, ale umožněte ostatním zacházet jako `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="6937d-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="6937d-116">To můžete udělat nejdřív zachytávání konkrétnější typ výjimky a následné zachycování `CommunicationException` v pozdější klauzule catch.</span><span class="sxs-lookup"><span data-stu-id="6937d-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="6937d-117">Musíte zachytit kód, který volá metodu komunikaci klienta `TimeoutException` a `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="6937d-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="6937d-118">Jedním ze způsobů zpracování těchto chyb je přerušit klienta a tvorba sestav selhání komunikace.</span><span class="sxs-lookup"><span data-stu-id="6937d-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="6937d-119">Pokud dojde k očekávané výjimky, klient může nebo nemusí být použitelné později.</span><span class="sxs-lookup"><span data-stu-id="6937d-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="6937d-120">Pokud chcete zjistit, pokud je klient stále možné použít, zkontrolujte, že `State` vlastnost `CommunicationState`. Otevřít.</span><span class="sxs-lookup"><span data-stu-id="6937d-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="6937d-121">Pokud je stále otevřen, je stále možné použít.</span><span class="sxs-lookup"><span data-stu-id="6937d-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="6937d-122">V opačném případě by měl přerušení klienta a uvolnit všechny odkazy na ni.</span><span class="sxs-lookup"><span data-stu-id="6937d-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6937d-123">Podívat se, že klienti, kteří mají relaci často již nejsou použitelné po výjimce a klienti, které nemají relaci stále často použitelné po výjimce.</span><span class="sxs-lookup"><span data-stu-id="6937d-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="6937d-124">Ale ani jeden z nich je zaručeno, tak pokud budete chtít pokračovat i po výjimce by měla vaše aplikace provádět pomocí klienta `State` vlastnost ověření klienta je stále otevřen.</span><span class="sxs-lookup"><span data-stu-id="6937d-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="6937d-125">Při spuštění ukázky operace odpovědi a výjimky jsou zobrazeny v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="6937d-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="6937d-126">Spustí proces klienta dva scénáře, každý z které pokusy o volání `Add` následovaný `Divide`.</span><span class="sxs-lookup"><span data-stu-id="6937d-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="6937d-127">První scénář simuluje potíže se sítí přerušením klient před provedením volání `Divide`.</span><span class="sxs-lookup"><span data-stu-id="6937d-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="6937d-128">Druhý scénář způsobí, že vypršení časového limitu podmínku tak, že nastavíte časový limit příliš krátká pro metodu k dokončení.</span><span class="sxs-lookup"><span data-stu-id="6937d-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="6937d-129">Očekávaný výstup z procesu klienta je:</span><span class="sxs-lookup"><span data-stu-id="6937d-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6937d-130">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="6937d-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6937d-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6937d-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6937d-132">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6937d-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6937d-133">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6937d-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6937d-134">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="6937d-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6937d-135">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6937d-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6937d-136">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6937d-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6937d-137">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6937d-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
