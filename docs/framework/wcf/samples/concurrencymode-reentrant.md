---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183898"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="20a04-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="20a04-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="20a04-103">Tato ukázka ukazuje nutnost a důsledky použití ConcurrencyMode.Reentrant na implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="20a04-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="20a04-104">ConcurrencyMode.Reentrant znamená, že služba (nebo zpětné volání) zpracovává pouze jednu `ConcurencyMode.Single`zprávu v daném okamžiku (analogicky k).</span><span class="sxs-lookup"><span data-stu-id="20a04-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="20a04-105">Chcete-li zajistit bezpečnost podprocesu, Windows `InstanceContext` Communication Foundation (WCF) uzamkne zpracování zprávy tak, aby žádné jiné zprávy mohou být zpracovány.</span><span class="sxs-lookup"><span data-stu-id="20a04-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="20a04-106">V případě režimu Reentrant `InstanceContext` je odemčentěsně před tím, než služba provede odchozí volání, čímž umožní následnému volání (které může být reentrant, jak je znázorněno v ukázce), získat zámek při příštím příchozím do služby.</span><span class="sxs-lookup"><span data-stu-id="20a04-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="20a04-107">Chcete-li demonstrovat chování, ukázka ukazuje, jak klient a služba můžete odesílat zprávy mezi sebou pomocí duplexní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="20a04-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="20a04-108">Definovaná smlouva je duplexní `Ping` smlouva s metodou implementovanou `Pong` službou a metodou zpětného volání implementovanou klientem.</span><span class="sxs-lookup"><span data-stu-id="20a04-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="20a04-109">Klient vyvolá `Ping` metodu serveru s počtem značek a tím iniciuje volání.</span><span class="sxs-lookup"><span data-stu-id="20a04-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="20a04-110">Služba zkontroluje, zda počet značek není rovna 0 a `Pong` potom vyvolá metodu zpětná volání při snížení počtu značek.</span><span class="sxs-lookup"><span data-stu-id="20a04-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="20a04-111">To se provádí podle následujícího kódu v ukázce.</span><span class="sxs-lookup"><span data-stu-id="20a04-111">This is done by the following code in the sample.</span></span>  
  
```csharp
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
  
 Implementace zpětného `Pong` volání má stejnou logiku `Ping` jako implementace. To znamená, že zkontroluje, zda počet značek `Ping` není nula a potom vyvolá metodu na kanálu zpětného volání `Ping` (v tomto případě je kanál, který byl použit k odeslání původní zprávy) s počet značek snížena o 1. V okamžiku, kdy počet značek dosáhne 0, metoda vrátí a tím rozbalí všechny odpovědi zpět na první volání provedené klientem, který inicioval volání. <span data-ttu-id="20a04-115">To je zobrazeno v implementaci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="20a04-115">This is shown in the callback implementation.</span></span>  
  
```csharp
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
  
 Obě `Ping` metody `Pong` a jsou request/reply, což znamená, že první `Ping` volání `CallbackChannel<T>.Pong()` nevrátí, dokud volání vrátí. Na straně klienta `Pong` metoda nemůže `Ping` vrátit až do další volání, které se vrátí. <span data-ttu-id="20a04-118">Vzhledem k tomu, že zpětné volání a služba musí provést odchozí požadavek/odpověď volání před tím, než mohou odpovědět na čekající požadavek, obě implementace musí být označeny concurrencyMode.Reentrant chování.</span><span class="sxs-lookup"><span data-stu-id="20a04-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20a04-119">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="20a04-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="20a04-120">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20a04-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="20a04-121">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20a04-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="20a04-122">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20a04-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="20a04-123">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="20a04-123">Demonstrates</span></span>  
 <span data-ttu-id="20a04-124">Chcete-li spustit ukázku, vytvořte projekty klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="20a04-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="20a04-125">Potom otevřete dvě okna příkazů a \<změňte adresáře na ukázkový \<>\CS\Service\bin\debug a ukázkové>\CS\Client\bin\debug adresáře.</span><span class="sxs-lookup"><span data-stu-id="20a04-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="20a04-126">Potom spusťte službu zadáním `service.exe` a potom vyvolat Client.exe s počáteční hodnotou značek předaných jako vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="20a04-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="20a04-127">Ukázkový výstup pro 10 značek je zobrazen.</span><span class="sxs-lookup"><span data-stu-id="20a04-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
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
> <span data-ttu-id="20a04-128">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="20a04-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20a04-129">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="20a04-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="20a04-130">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="20a04-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20a04-131">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="20a04-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
