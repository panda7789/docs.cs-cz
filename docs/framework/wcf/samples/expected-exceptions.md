---
title: "Očekávané výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 728f13fcf265c20c480d34388001d528ce43190e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="expected-exceptions"></a><span data-ttu-id="d5352-102">Očekávané výjimky</span><span class="sxs-lookup"><span data-stu-id="d5352-102">Expected Exceptions</span></span>
<span data-ttu-id="d5352-103">Tento příklad znázorňuje, jak zachytit očekávané výjimky při použití typový klient.</span><span class="sxs-lookup"><span data-stu-id="d5352-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="d5352-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="d5352-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="d5352-105">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="d5352-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5352-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d5352-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d5352-107">Tento příklad znázorňuje zachytávání a zpracování těchto dvou typů očekávané výjimky, které opravit programy musí zpracovat: `TimeoutException` a `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d5352-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="d5352-108">Výjimky, které jsou vyvolány z metody komunikace na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta jsou očekávané nebo neočekávané.</span><span class="sxs-lookup"><span data-stu-id="d5352-108">Exceptions that are thrown from communication methods on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client are either expected or unexpected.</span></span> <span data-ttu-id="d5352-109">Neočekávané výjimky patří závažné chyby jako `OutOfMemoryException` a programovací chyby, jako jsou `ArgumentNullException` nebo `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="d5352-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="d5352-110">Obvykle se nedá nijak užitečné pro zpracování neočekávaným chybám, takže obvykle neměli je zachytit při volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metoda komunikace s klientem.</span><span class="sxs-lookup"><span data-stu-id="d5352-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client communication method.</span></span>  
  
 <span data-ttu-id="d5352-111">Na očekávané výjimky z metody komunikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnují klienta `TimeoutException`, `CommunicationException`, a všechny odvozené třídy `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d5352-111">Expected exceptions from communication methods on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="d5352-112">Ty naznačují problém při komunikaci, která může bezpečně ošetřit přerušení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a vytváření sestav selhání komunikace.</span><span class="sxs-lookup"><span data-stu-id="d5352-112">These indicate a problem during communication that can be safely handled by aborting the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and reporting a communication failure.</span></span> <span data-ttu-id="d5352-113">Vzhledem k tomu, že externí faktory mohou způsobit tyto chyby v jakékoli aplikaci, musíte správné aplikace zachytit tyto výjimky a obnovit, pokud k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="d5352-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="d5352-114">Existuje několik odvozené třídy `CommunicationException` který lze vyvolat klienta.</span><span class="sxs-lookup"><span data-stu-id="d5352-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="d5352-115">V některých případech aplikace i catch některé z těchto provést zvláštní zpracování, ale nechat řešeny jako ostatní `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d5352-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="d5352-116">To lze provést tak, že nejprve zachytávání konkrétnější typ výjimky a potom zachytávání `CommunicationException` novější klauzule catch.</span><span class="sxs-lookup"><span data-stu-id="d5352-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="d5352-117">Kód, který volá metodu komunikace klienta musí catch `TimeoutException` a `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d5352-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="d5352-118">Jedním ze způsobů ke zpracování těchto chyb je abort klienta a ohlásí selhání komunikace.</span><span class="sxs-lookup"><span data-stu-id="d5352-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```  
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
  
 <span data-ttu-id="d5352-119">Pokud dojde k výjimce očekávané, klienta může nebo nemusí být použitelná později.</span><span class="sxs-lookup"><span data-stu-id="d5352-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="d5352-120">Pokud chcete zjistit, pokud je klient stále možné použít, zkontrolujte, zda `State` vlastnost je `CommunicationState`. Otevřít.</span><span class="sxs-lookup"><span data-stu-id="d5352-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="d5352-121">Pokud je stále otevřen, je stále možné použít.</span><span class="sxs-lookup"><span data-stu-id="d5352-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="d5352-122">V opačném případě by měl abort klienta a uvolnit všechny odkazy na ni.</span><span class="sxs-lookup"><span data-stu-id="d5352-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d5352-123">Můžete pozorovat, že klienti, kteří mají relaci často již nejsou použitelné po výjimce a klientů, které nemají relaci jsou stále často použitelné po výjimce.</span><span class="sxs-lookup"><span data-stu-id="d5352-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="d5352-124">Však ani jedno z těchto záruku, že, takže pokud chcete pokračovat i po výjimce vaše aplikace by se mělo zjistit pomocí klienta `State` vlastnost ověření klienta je stále otevřen.</span><span class="sxs-lookup"><span data-stu-id="d5352-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="d5352-125">Když spustíte ukázku, zobrazí se v okně konzoly klienta odpovědí na operaci a výjimky.</span><span class="sxs-lookup"><span data-stu-id="d5352-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="d5352-126">Spustí proces klienta dva scénáře, každý z které pokusy o volání `Add` následuje `Divide`.</span><span class="sxs-lookup"><span data-stu-id="d5352-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="d5352-127">První scénář simuluje potíže se sítí pomocí přerušení klient před provedením volání `Divide`.</span><span class="sxs-lookup"><span data-stu-id="d5352-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="d5352-128">Druhý scénář způsobí, že podmínka časový limit nastavením časový limit příliš krátká pro metodu dokončení.</span><span class="sxs-lookup"><span data-stu-id="d5352-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="d5352-129">Je očekávaný výstup z procesu klienta:</span><span class="sxs-lookup"><span data-stu-id="d5352-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d5352-130">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d5352-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d5352-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5352-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d5352-132">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5352-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d5352-133">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5352-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5352-134">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d5352-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d5352-135">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d5352-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d5352-136">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d5352-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5352-137">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d5352-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a><span data-ttu-id="d5352-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5352-138">See Also</span></span>
