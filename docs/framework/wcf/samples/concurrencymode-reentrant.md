---
title: ConcurrencyMode Reentrant
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 17c3bf41f9db0458b91af808cbde56634ef1fca8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="e54e5-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="e54e5-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="e54e5-103">Tento příklad znázorňuje nezbytné a důsledky použití ConcurrencyMode.Reentrant na implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="e54e5-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="e54e5-104">ConcurrencyMode.Reentrant znamená, že služba (nebo zpětného volání) zpracovává jenom jednu zprávu v daném okamžiku (podobá `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="e54e5-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="e54e5-105">K zajištění bezpečnosti vlákno [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zámky `InstanceContext` zpracování zprávy, takže lze zpracovat žádné další zprávy.</span><span class="sxs-lookup"><span data-stu-id="e54e5-105">To ensure thread safety, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="e54e5-106">V případě vícenásobné režimu `InstanceContext` je odemčený těsně před služby umožňuje odchozí volání následných volání (může to být vícenásobné, jak je předvedeno v ukázce) a tím umožní získat zámek příštím pochází službě.</span><span class="sxs-lookup"><span data-stu-id="e54e5-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="e54e5-107">K předvedení chování, příklad ukazuje, jak může klient a služba odesílání zpráv mezi sebou pomocí duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e54e5-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="e54e5-108">Kontrakt definovaný je duplexního kontraktu s `Ping` metoda se implementuje službou a metoda zpětného volání `Pong` se implementuje klientem.</span><span class="sxs-lookup"><span data-stu-id="e54e5-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="e54e5-109">Klient vyvolá serveru `Ping` metoda s osové počet a inicializaci volání.</span><span class="sxs-lookup"><span data-stu-id="e54e5-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="e54e5-110">Služba zkontroluje, zda počet značek není roven 0 a poté vyvolá zpětná volání `Pong` metoda při dekrementace počet značek.</span><span class="sxs-lookup"><span data-stu-id="e54e5-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="e54e5-111">K tomu je potřeba následující kód v ukázce.</span><span class="sxs-lookup"><span data-stu-id="e54e5-111">This is done by the following code in the sample.</span></span>  
  
```  
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 Při zpětném volání `Pong` implementace má stejné logiky, která jako `Ping` implementace. To znamená, se ověří, zda počet značek není nula a poté vyvolá `Ping` metoda zpětného volání kanálu (v takovém případě je kanál, který se používá k odesílání původní `Ping` zpráva) s značek počet odečte o 1. Okamžiku, kdy počet značek dosáhne 0, vrátí tato metoda hodnotu a rozbalování všechny odpovědi zpět na první volání klienta, která iniciovala volání. <span data-ttu-id="e54e5-115">Ta se zobrazí v implementaci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e54e5-115">This is shown in the callback implementation.</span></span>  
  
```  
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Jak `Ping` a `Pong` jsou požadavek nebo odpověď, což znamená, že první volání metody `Ping` nevrací dokud volání `CallbackChannel<T>.Pong()` vrátí. Na straně klienta `Pong` metoda nemůže vrátit až do dalšího `Ping` volání, aby se provedené vrátí. <span data-ttu-id="e54e5-118">Vzhledem k tomu odchozí volání požadavek nebo odpověď musí provádět zpětné volání a služby, než může odpovědět čekající žádosti, musí být obě implementace označen s chováním ConcurrencyMode.Reentrant.</span><span class="sxs-lookup"><span data-stu-id="e54e5-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e54e5-119">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="e54e5-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e54e5-120">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e54e5-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e54e5-121">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e54e5-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e54e5-122">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e54e5-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e54e5-123">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="e54e5-123">Demonstrates</span></span>  
 <span data-ttu-id="e54e5-124">Do spuštění vzorového sestavení projektů klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="e54e5-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="e54e5-125">Dále otevřete dvě příkaz windows a přejděte do adresáře \<ukázka > \CS\Service\bin\debug a \<ukázka > \CS\Client\bin\debug adresáře.</span><span class="sxs-lookup"><span data-stu-id="e54e5-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="e54e5-126">Potom spusťte službu zadáním `service.exe` a pak vyvolejte Client.exe s počáteční hodnotou ticks předat jako vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="e54e5-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="e54e5-127">Ukázkový výstup pro rysky 10 se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="e54e5-127">A sample output for 10 ticks is shown.</span></span>  
  
```  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="e54e5-128">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="e54e5-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e54e5-129">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e54e5-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e54e5-130">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e54e5-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e54e5-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e54e5-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a><span data-ttu-id="e54e5-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e54e5-132">See Also</span></span>
