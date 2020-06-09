---
title: Očekávané výjimky
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: d8e3c024eb69fe22ec27f3e3697bc4fc7b4ee121
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600526"
---
# <a name="expected-exceptions"></a><span data-ttu-id="86e75-102">Očekávané výjimky</span><span class="sxs-lookup"><span data-stu-id="86e75-102">Expected Exceptions</span></span>
<span data-ttu-id="86e75-103">Tato ukázka předvádí, jak zachytit očekávané výjimky při použití typového klienta.</span><span class="sxs-lookup"><span data-stu-id="86e75-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="86e75-104">Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="86e75-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="86e75-105">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="86e75-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86e75-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="86e75-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="86e75-107">Tento příklad znázorňuje zachycení a zpracování dvou očekávaných typů výjimek, které musí zpracovat správné programy: `TimeoutException` a `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="86e75-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="86e75-108">Výjimky, které jsou vyvolány ze způsobů komunikace u klienta služby Windows Communication Foundation (WCF), jsou buď očekávány, nebo neočekávané.</span><span class="sxs-lookup"><span data-stu-id="86e75-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="86e75-109">Neočekávané výjimky zahrnují závažná selhání jako `OutOfMemoryException` a chyby programování jako `ArgumentNullException` nebo `InvalidOperationException` .</span><span class="sxs-lookup"><span data-stu-id="86e75-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="86e75-110">Obvykle neexistuje žádný užitečný způsob, jak zpracovat neočekávané chyby, takže byste je neměli zachytit při volání metody komunikace klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="86e75-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="86e75-111">Očekávané výjimky ze způsobů komunikace na klientovi WCF zahrnují `TimeoutException` , `CommunicationException` a jakékoliv odvozené třídy `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="86e75-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="86e75-112">Ty naznačují problém během komunikace, který je možné bezpečně zpracovat přerušením klienta WCF a odesláním chyby komunikace.</span><span class="sxs-lookup"><span data-stu-id="86e75-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="86e75-113">Vzhledem k tomu, že externí faktory mohou způsobovat tyto chyby v jakékoli aplikaci, správné aplikace musí zachytit tyto výjimky a obnovit ji, když k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="86e75-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="86e75-114">Existuje několik odvozených tříd `CommunicationException` , které může klient vyvolat.</span><span class="sxs-lookup"><span data-stu-id="86e75-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="86e75-115">V některých případech aplikace také zachytit některé z nich, aby provedla speciální zpracování, ale ostatní budou zpracována jako `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="86e75-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="86e75-116">To lze provést tak, že nejprve zachytíte konkrétnější typ výjimky a pak zachytíte `CommunicationException` v pozdější klauzuli catch.</span><span class="sxs-lookup"><span data-stu-id="86e75-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="86e75-117">Kód, který volá metodu komunikace klienta, musí zachytit `TimeoutException` a `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="86e75-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="86e75-118">Jedním ze způsobů, jak tyto chyby zpracovat, je přerušit klienta a ohlásit selhání komunikace.</span><span class="sxs-lookup"><span data-stu-id="86e75-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="86e75-119">Pokud dojde k očekávané výjimce, klient může nebo nemusí být použitelný později.</span><span class="sxs-lookup"><span data-stu-id="86e75-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="86e75-120">Chcete-li zjistit, zda je klient stále použitelný, zkontrolujte, zda `State` je vlastnost nastavena na hodnotu `CommunicationState` . Otevřít.</span><span class="sxs-lookup"><span data-stu-id="86e75-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="86e75-121">Pokud je stále otevřený, je stále možné ho použít.</span><span class="sxs-lookup"><span data-stu-id="86e75-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="86e75-122">V opačném případě byste měli klienta přerušit a uvolnit všechny odkazy na něj.</span><span class="sxs-lookup"><span data-stu-id="86e75-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="86e75-123">Můžete se setkat s tím, že klienti, kteří mají relaci, již nejsou po výjimce použitelné, a klienti, kteří relaci nemají, jsou často i nadále použitelné i po výjimce.</span><span class="sxs-lookup"><span data-stu-id="86e75-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="86e75-124">Ani jedna z těchto možností není zaručena, takže pokud se chcete pokusit nadále používat klienta po výjimce, měla by aplikace zkontrolovat `State` vlastnost a ověřit, zda je klient stále otevřen.</span><span class="sxs-lookup"><span data-stu-id="86e75-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="86e75-125">Při spuštění ukázky se v okně konzoly klienta zobrazí odezvy operace a výjimky.</span><span class="sxs-lookup"><span data-stu-id="86e75-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="86e75-126">Proces klienta spouští dva scénáře, z nichž každý se pokusí zavolat `Add` za ním `Divide` .</span><span class="sxs-lookup"><span data-stu-id="86e75-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="86e75-127">První scénář simuluje problém se sítí přerušením klienta před uskutečněním volání `Divide` .</span><span class="sxs-lookup"><span data-stu-id="86e75-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="86e75-128">Druhý scénář způsobí vypršení časového limitu tím, že nastaví časový limit příliš krátký pro dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="86e75-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="86e75-129">Očekávaný výstup z klientského procesu je:</span><span class="sxs-lookup"><span data-stu-id="86e75-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="86e75-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="86e75-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="86e75-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="86e75-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="86e75-132">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="86e75-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="86e75-133">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="86e75-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="86e75-134">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="86e75-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="86e75-135">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="86e75-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="86e75-136">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="86e75-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="86e75-137">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="86e75-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
