---
title: Očekávané výjimky
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144706"
---
# <a name="expected-exceptions"></a><span data-ttu-id="18648-102">Očekávané výjimky</span><span class="sxs-lookup"><span data-stu-id="18648-102">Expected Exceptions</span></span>
<span data-ttu-id="18648-103">Tato ukázka ukazuje, jak zachytit očekávané výjimky při použití zadaného klienta.</span><span class="sxs-lookup"><span data-stu-id="18648-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="18648-104">Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="18648-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="18648-105">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="18648-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18648-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="18648-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="18648-107">Tato ukázka ukazuje zachycení a zpracování dvou očekávaných `TimeoutException` typů `CommunicationException`výjimek, které správné programy musí zpracovat: a .</span><span class="sxs-lookup"><span data-stu-id="18648-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="18648-108">Výjimky, které jsou vyvolány z komunikačních metod v klientovi WCF (Windows Communication Foundation) jsou očekávané nebo neočekávané.</span><span class="sxs-lookup"><span data-stu-id="18648-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="18648-109">Neočekávané výjimky zahrnují `OutOfMemoryException` katastrofická selhání, jako jsou chyby programování, jako je `ArgumentNullException` nebo `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="18648-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="18648-110">Obvykle neexistuje žádný užitečný způsob zpracování neočekávaných chyb, takže obvykle byste je neměli zachytit při volání metody komunikace klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="18648-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="18648-111">Očekávané výjimky z komunikačních metod `TimeoutException`na `CommunicationException`wcf klienta `CommunicationException`patří , a všechny odvozené třídy .</span><span class="sxs-lookup"><span data-stu-id="18648-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="18648-112">Ty označují problém během komunikace, které lze bezpečně zpracovat přerušením wcf klienta a hlášení selhání komunikace.</span><span class="sxs-lookup"><span data-stu-id="18648-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="18648-113">Vzhledem k tomu, že externí faktory mohou způsobit tyto chyby v libovolné aplikaci, správné aplikace musí zachytit tyto výjimky a obnovit, když k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="18648-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="18648-114">Existuje několik odvozených `CommunicationException` tříd, které může klient vyvolat.</span><span class="sxs-lookup"><span data-stu-id="18648-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="18648-115">V některých případech aplikace také chytit některé z nich udělat zvláštní `CommunicationException`zacházení, ale nechte ostatní zacházet jako .</span><span class="sxs-lookup"><span data-stu-id="18648-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="18648-116">Toho lze dosáhnout zachycením konkrétnější typ výjimky `CommunicationException` první a potom zachycení v pozdější catch klauzule.</span><span class="sxs-lookup"><span data-stu-id="18648-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="18648-117">Kód, který volá metodu `TimeoutException` komunikace `CommunicationException`klienta, musí zachytit a .</span><span class="sxs-lookup"><span data-stu-id="18648-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="18648-118">Jedním ze způsobů, jak tyto chyby zpracovat, je přerušit klienta a nahlásit selhání komunikace.</span><span class="sxs-lookup"><span data-stu-id="18648-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="18648-119">Pokud dojde k očekávané výjimce, klient může nebo nemusí být použitelný později.</span><span class="sxs-lookup"><span data-stu-id="18648-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="18648-120">Chcete-li zjistit, zda je klient `State` stále `CommunicationState`použitelný, zkontrolujte, zda je vlastnost . Otevřít.</span><span class="sxs-lookup"><span data-stu-id="18648-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="18648-121">Pokud je stále otevřen, je stále použitelný.</span><span class="sxs-lookup"><span data-stu-id="18648-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="18648-122">V opačném případě byste měli přerušit klienta a uvolnit všechny odkazy na něj.</span><span class="sxs-lookup"><span data-stu-id="18648-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="18648-123">Můžete pozorovat, že klienti, kteří mají relaci jsou často již nelze použít po výjimce a klienti, kteří nemají relaci jsou často stále použitelné po výjimce.</span><span class="sxs-lookup"><span data-stu-id="18648-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="18648-124">Ani jeden z nich však není zaručena, takže pokud chcete pokračovat v používání `State` klienta po výjimce aplikace by měla zkontrolovat vlastnost ověřit klient je stále otevřen.</span><span class="sxs-lookup"><span data-stu-id="18648-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="18648-125">Při spuštění ukázky jsou v okně klientské konzole zobrazeny odpovědi na operaci a výjimky.</span><span class="sxs-lookup"><span data-stu-id="18648-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="18648-126">Proces klienta spustí dva scénáře, z `Add` nichž `Divide`každý se pokusí volat následovaný .</span><span class="sxs-lookup"><span data-stu-id="18648-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="18648-127">První scénář simuluje problém sítě přerušením klienta `Divide`před provedením volání .</span><span class="sxs-lookup"><span data-stu-id="18648-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="18648-128">Druhý scénář způsobí, že podmínka časového limitu nastavením časový limit příliš krátký pro dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="18648-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="18648-129">Očekávaný výstup z klientského procesu je:</span><span class="sxs-lookup"><span data-stu-id="18648-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18648-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="18648-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="18648-131">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18648-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="18648-132">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18648-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="18648-133">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18648-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="18648-134">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="18648-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18648-135">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="18648-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="18648-136">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="18648-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18648-137">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="18648-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
